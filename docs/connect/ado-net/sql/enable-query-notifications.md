---
title: Activation de notifications de requête
description: Explique comment utiliser les notifications de requêtes, notamment la configuration requise pour l’activation et l’utilisation de ces notifications.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 94b472a1fe040aa3a684d9f7b523ba09c82a651e
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452233"
---
# <a name="enabling-query-notifications"></a>Activation de notifications de requête

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Télécharger ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Les applications qui utilisent des notifications de requête ont un ensemble commun d’exigences. Votre source de données doit être correctement configurée pour prendre en charge les notifications de requête SQL, et l’utilisateur doit disposer des autorisations appropriées côté client et côté serveur.  
  
Pour utiliser des notifications de requête, vous devez :  
  
- Activez les notifications de requête pour votre base de données.  
  
- Assurez-vous que l’ID utilisateur utilisé pour se connecter à la base de données dispose des autorisations nécessaires.  
  
- Utilisez un objet <xref:Microsoft.Data.SqlClient.SqlCommand> pour exécuter une instruction SELECT valide avec un objet de notification associé, <xref:Microsoft.Data.SqlClient.SqlDependency> ou <xref:Microsoft.Data.Sql.SqlNotificationRequest>.  
  
- Fournissez du code pour traiter la notification si les données surveillées sont modifiées.  
  
## <a name="query-notifications-requirements"></a>Conditions requises pour les notifications de requêtes  
Les notifications de requête sont prises en charge uniquement pour les instructions SELECT qui répondent à une liste d’exigences spécifiques. Le tableau suivant fournit des liens vers les Service Broker et la documentation des notifications de requête dans Documentation en ligne de SQL Server.  
  
**Documentation SQL Server**  
  
- [Création d’une requête pour notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))  
  
- [Considérations relatives à sécurité pour Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))  
  
- [Sécurité et protection (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))  
  
- [Considérations relatives à la sécurité pour Notifications Services](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))  
  
- [Autorisations associées aux notifications de requêtes](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))  
  
- [Considérations d’ordre international pour Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))  
  
- [Considérations sur la conception de la solution (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))  
  
- [Centre d’informations du développeur Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))  
  
- [Guide du développeur (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Activation des notifications de requête pour exécuter un exemple de code  
Pour activer Service Broker sur la base de données **AdventureWorks** à l’aide de SQL Server Management Studio, exécutez l’instruction Transact-SQL suivante :  
  
`ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
Pour que les exemples de notifications de requête s’exécutent correctement, les instructions Transact-SQL suivantes doivent être exécutées sur le serveur de base de données.  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Autorisations pour les notifications de requêtes  
Les utilisateurs qui exécutent des commandes qui demandent une notification doivent disposer de l’autorisation ABONNer les NOTIFICATIONs de requêtes sur le serveur.  
  
Le code côté client qui s’exécute dans une situation de confiance partielle requiert l' <xref:Microsoft.Data.SqlClient.SqlClientPermission>.  
  
Le code suivant crée un objet <xref:Microsoft.Data.SqlClient.SqlClientPermission>, en affectant à la <xref:System.Security.Permissions.PermissionState> la valeur <xref:System.Security.Permissions.PermissionState.Unrestricted>. La <xref:System.Security.CodeAccessPermission.Demand%2A> forcera un <xref:System.Security.SecurityException> au moment de l’exécution si tous les appelants situés plus haut dans la pile des appels n’ont pas reçu l’autorisation.  
  
[!code-csharp[DataWorks SqlClientPermission_Demand#1](~/../sqlclient/doc/samples/SqlClientPermission_Demand.cs#1)]
  
## <a name="choosing-a-notification-object"></a>Choix d’un objet de notification  
L’API des notifications de requête fournit deux objets pour traiter les notifications : <xref:Microsoft.Data.SqlClient.SqlDependency> et <xref:Microsoft.Data.Sql.SqlNotificationRequest>.
  
### <a name="using-sqldependency"></a>Utilisation de SqlDependency  
Pour utiliser <xref:Microsoft.Data.SqlClient.SqlDependency>, Service Broker doit être activé pour la base de données SQL Server utilisée, et les utilisateurs doivent disposer des autorisations nécessaires pour recevoir des notifications. Service Broker objets, tels que la file d’attente de notification, sont prédéfinis.  
  
En outre, <xref:Microsoft.Data.SqlClient.SqlDependency> lance automatiquement un thread de travail pour traiter les notifications à mesure qu’elles sont publiées dans la file d’attente ; Il analyse également le message de Service Broker, en exposant les informations en tant que données d’argument d’événement. <xref:Microsoft.Data.SqlClient.SqlDependency> doit être initialisé en appelant la méthode `Start` pour établir une dépendance à la base de données. Il s’agit d’une méthode statique qui doit être appelée une seule fois lors de l’initialisation de l’application pour chaque connexion de base de données requise. La méthode `Stop` doit être appelée au moment de l’arrêt de l’application pour chaque connexion de dépendance qui a été établie.  
  
### <a name="using-sqlnotificationrequest"></a>Utilisation de SqlNotificationRequest  
En revanche, <xref:Microsoft.Data.Sql.SqlNotificationRequest> vous oblige à implémenter la totalité de l’infrastructure d’écoute. En outre, tous les objets de Service Broker de prise en charge tels que la file d’attente, le service et les types de messages pris en charge par la file d’attente doivent être définis. Cette approche manuelle est utile si votre application requiert des messages de notification spéciaux ou des comportements de notification, ou si votre application fait partie d’une plus grande Service Broker application.  
  
## <a name="next-steps"></a>Étapes suivantes
- [Notifications de requête dans SQL Server](query-notifications-sql-server.md)

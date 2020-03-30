---
title: Activation de notifications de requête
description: Explique comment utiliser les notifications de requêtes, notamment les exigences pour les activer et les utiliser.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: e587639f5323ea76c975e3a8c35d647a7eb3d891
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896970"
---
# <a name="enabling-query-notifications"></a>Activation de notifications de requête

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Les applications qui utilisent des notifications de requêtes ont un ensemble commun d’exigences. Votre source de données doit être correctement configurée pour prendre en charge les notifications de requête SQL, et l’utilisateur doit disposer des autorisations appropriées côté client et côté serveur.  
  
Pour utiliser des notifications de requêtes, vous devez :  
  
- Activer les notifications de requêtes pour votre base de données.  
  
- Vous assurer que l’ID utilisateur utilisé pour se connecter à la base de données dispose des autorisations nécessaires.  
  
- Utilisez un objet <xref:Microsoft.Data.SqlClient.SqlCommand> pour exécuter une instruction SELECT valide avec un objet de notification associé, <xref:Microsoft.Data.SqlClient.SqlDependency> ou <xref:Microsoft.Data.Sql.SqlNotificationRequest>.  
  
- Fournissez du code pour traiter la notification si les données surveillées sont modifiées.  
  
## <a name="query-notifications-requirements"></a>Exigences pour les notifications de requêtes  
Les notifications de requêtes sont prises en charge uniquement pour les instructions SELECT qui répondent à une liste d’exigences suivantes. Le tableau suivant fournit des liens vers la documentation sur les notifications de requêtes dans la Documentation en ligne de SQL Server.  
  
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
  
## <a name="enabling-query-notifications-to-run-sample-code"></a>Activation des notifications de requêtes pour exécuter un exemple de code  
Pour activer Service Broker sur la base de données **AdventureWorks** à l’aide de SQL Server Management Studio, exécutez l’instruction Transact-SQL suivante :  
  
`ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
Pour que les exemples de notifications de requêtes s’exécutent correctement, les instructions Transact-SQL suivantes doivent être exécutées sur le serveur de base de données.  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a>Autorisations des notifications de requêtes  
Les utilisateurs qui exécutent des commandes exigeant une notification doivent être INSCRITS à une autorisation de base de données de NOTIFICATIONS DE REQUÊTES sur le serveur.  
  
Le code côté client qui s’exécute dans une situation de confiance partielle requiert la <xref:Microsoft.Data.SqlClient.SqlClientPermission>.  
  
Le code suivant permet de créer un objet <xref:Microsoft.Data.SqlClient.SqlClientPermission> qui définit <xref:System.Security.Permissions.PermissionState> sur <xref:System.Security.Permissions.PermissionState.Unrestricted>. La <xref:System.Security.CodeAccessPermission.Demand%2A> force une <xref:System.Security.SecurityException> au moment de l’exécution si l’autorisation a été accordée à tous les appelants au dessus de la pile d’appels.  
  
[!code-csharp[DataWorks SqlClientPermission_Demand#1](~/../sqlclient/doc/samples/SqlClientPermission_Demand.cs#1)]
  
## <a name="choosing-a-notification-object"></a>Choix d’un objet de notification  
L’API des notifications de requête fournit deux objets pour traiter les notifications : <xref:Microsoft.Data.SqlClient.SqlDependency> et <xref:Microsoft.Data.Sql.SqlNotificationRequest>.
  
### <a name="using-sqldependency"></a>Utilisation de SqlDependency  
Pour utiliser <xref:Microsoft.Data.SqlClient.SqlDependency>, Service Broker doit être activé pour la base de données SQL Server utilisée, et les utilisateurs doivent disposer des autorisations nécessaires pour recevoir des notifications. Les objets Service Broker, tels que la file d’attente des notifications, sont prédéfinis.  
  
En outre, <xref:Microsoft.Data.SqlClient.SqlDependency> lance automatiquement un thread de travail pour traiter les notifications au fur et à mesure de leur publication dans la file d'attente ; il analyse également le message de Service Broker en exposant les informations comme données d'argument d'événement. <xref:Microsoft.Data.SqlClient.SqlDependency> doit être initialisé en appelant la méthode `Start` pour établir une dépendance à la base de données. Il s’agit d’une méthode statique qui ne doit être appelée qu’une seule fois pendant l’initialisation de l’application pour chaque connexion de base de données requise. La méthode `Stop` doit être appelée à la fin de l’application pour chaque connexion de dépendance effectuée.  
  
### <a name="using-sqlnotificationrequest"></a>Utilisation de SqlNotificationRequest  
Par contre, <xref:Microsoft.Data.Sql.SqlNotificationRequest> vous demande d’implémenter vous-même l’infrastructure d’écoute complète. En outre, tous les objets Service Broker de prise en charge tels que la file d’attente, le service et les types de messages pris en charge par la file d’attente doivent être définis. Cette approche manuelle est utile si votre application requiert des messages de notification spéciaux ou des comportements de notification ou si votre application fait partie d’une plus grande application Service Broker.  
  
## <a name="next-steps"></a>Étapes suivantes
- [Notifications de requête dans SQL Server](query-notifications-sql-server.md)

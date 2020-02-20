---
title: Utilisation des notifications de requêtes | Microsoft Docs
description: Utilisation des notifications de requêtes dans OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], query notifications
- rowsets [SQL Server], notifications
- OLE DB Driver for SQL Server, query notifications
- notifications [OLE DB Driver for SQL Server]
- query notifications [SQL Server], OLE DB Driver for SQL Server
- canceling rowset changes
- IRowsetNotify interface
- MSOLEDBSQL, query notifications
- OLE DB Driver for SQL Server, query notifications
- consumer notification for rowset changes [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 29aaab523b3a754c65b1b7a0312ceb5ea122f2d3
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "68419320"
---
# <a name="working-with-query-notifications"></a>Utilisation de notifications de requêtes

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Les notifications de requêtes ont été introduites dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] et OLE DB Driver pour SQL Server. Basées sur l’infrastructure de Service Broker SQL introduite dans SQL Server 2005 (9.x), les notifications de requêtes permettent aux applications d’être notifiées en cas de modification des données. Cette fonctionnalité est particulièrement utile pour les applications qui fournissent un cache d’informations d’une base de données, par exemple une application web, et qui doivent être notifiées en cas de modification des données sources.

Les notifications de requêtes vous permettent de demander une notification dans un délai d'attente spécifié lorsque les données sous-jacentes d'une requête sont modifiées. La demande spécifie les options de notification, notamment le nom du service, le texte du message et la valeur du délai d’attente au serveur. Les notifications sont remises par l’intermédiaire d’une file d’attente Service Broker qui peut être interrogée par les applications pour détecter les notifications disponibles.

La syntaxe de la chaîne des options de notifications de requêtes est :

`service=<service-name>[;(local database=<database> | broker instance=<broker instance>)]`

 Par exemple :

`service=mySSBService;local database=mydb`

Les abonnements aux notifications survivent au processus qui les initie. En effet, une application peut créer un abonnement aux notifications, puis se terminer. L’abonnement reste valide, et la notification a lieu si les données sont modifiées dans le délai d’attente imparti spécifié au moment de la création de l’abonnement. Une notification est identifiée par la requête exécutée, les options de notification et le texte du message. Vous pouvez l’annuler en attribuant la valeur 0 au délai d'attente.

Les notifications sont envoyées une seule fois. Pour recevoir une notification continue des modifications de données, créez un nouvel abonnement en réexécutant la requête une fois chaque notification traitée.

Les applications OLE DB Driver pour SQL Server reçoivent généralement les notifications à l’aide de la commande [!INCLUDE[tsql](../../../includes/tsql-md.md)] [RECEIVE](../../../t-sql/statements/receive-transact-sql.md). Cette commande permet de lire les notifications de la file d’attente associée au service spécifié dans les options de notification.

> [!NOTE]
> Les noms de tables doivent être qualifiés dans des requêtes pour lesquelles une notification est requise. Par exemple : `dbo.myTable`. Les noms de tables doivent être qualifiés avec des noms en deux parties. L'abonnement n'est pas valide si des noms en trois ou quatre parties sont utilisés.

L'infrastructure de notification repose sur une fonctionnalité de mise en file d'attente introduite dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. En général, les notifications générées au niveau du serveur sont envoyées par l’intermédiaire de ces files d’attente pour un traitement ultérieur.

Pour utiliser des notifications de requêtes, une file d’attente et un service doivent exister sur le serveur. Vous pouvez les créer à l'aide d'une commande [!INCLUDE[tsql](../../../includes/tsql-md.md)] semblable à la suivante :

```sql
CREATE QUEUE myQueue
CREATE SERVICE myService ON QUEUE myQueue
([https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification])
```

> [!NOTE]
> Le service doit utiliser le contrat prédéfini, comme indiqué plus haut.

## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver pour SQL Server

OLE DB Driver pour SQL Server prend en charge les notifications du consommateur lors de la modification de l’ensemble de lignes. Le consommateur reçoit une notification à chaque phase de la modification de l’ensemble de lignes et à chaque tentative de modification.

> [!NOTE]
> Le passage d’une requête de notifications au serveur avec **ICommand::Execute** est la seule méthode valide pour s’abonner à des notifications de requête avec OLE DB Driver pour SQL Server.

### <a name="dbpropset_sqlserverrowset-property-set"></a>Jeu de propriétés DBPROPSET_SQLSERVERROWSET

Pour prendre en charge les notifications de requêtes via OLE DB, OLE DB Driver pour SQL Server ajoute les nouvelles propriétés suivantes au jeu de propriétés `DBPROPSET_SQLSERVERROWSET`.

|Name|Type|Description|
|----------|----------|-----------------|
|SSPROP_QP_NOTIFICATION_TIMEOUT|VT_UI4|Nombre de secondes pendant lesquelles la notification de requête doit rester active.<br /><br /> La valeur par défaut est 432 000 secondes (5 jours). La valeur minimale est 1 seconde, et la valeur maximale est 2^31-1 secondes.|
|SSPROP_QP_NOTIFICATION_MSGTEXT|VT_BSTR|Texte du message de la notification. Ce texte est défini par l’utilisateur et n’a aucun format prédéfini.<br /><br /> Par défaut, la chaîne est vide. Spécifiez un message en utilisant 1 à 2 000 caractères.|
|SSPROP_QP_NOTIFICATION_OPTIONS|VT_BSTR|Options de notification de requêtes. Celles-ci sont spécifiées dans une chaîne avec la syntaxe *nom*=*valeur*. L'utilisateur est chargé de créer le service et de lire les notifications de la file d'attente.<br /><br /> La valeur par défaut est une chaîne vide.|

L’abonnement aux notifications est toujours validé, que l'instruction ait été exécutée dans une transaction utilisateur ou en mode de validation automatique, ou que la transaction dans laquelle l'instruction s'est exécutée ait été validée ou restaurée. La notification du serveur est déclenchée lorsque l'une des conditions de notification non valides suivantes se produit : modification des données sous-jacentes ou du schéma ou expiration du délai d'attente imparti (selon l'opération qui se produit en premier). 

Les inscriptions de notification sont supprimées dès qu’elles sont déclenchées. Par conséquent, lorsque l’application reçoit des notifications, elle doit encore s’abonner si vous voulez obtenir d’autres mises à jour.

Une autre connexion ou un autre thread peut vérifier la file d'attente de destination pour les notifications. Par exemple :

```sql
WAITFOR (RECEIVE * FROM MyQueue); -- Where MyQueue is the queue name.
```

> [!NOTE]
> `SELECT *` ne supprime pas l’entrée de la file d’attente. Mais `RECEIVE * FROM` la supprime. Cela bloque un thread serveur si la file d'attente est vide. S’il existe des entrées de file d’attente au moment de l’appel, elles sont immédiatement retournées. Sinon, l’appel attend qu’une entrée de file d’attente soit créée.

```sql
RECEIVE * FROM MyQueue
```

Cette instruction retourne immédiatement un jeu de résultats vide si la file d'attente est vide. Sinon, elle retourne toutes les notifications de la file d'attente.

Si `SSPROP_QP_NOTIFICATION_MSGTEXT` et `SSPROP_QP_NOTIFICATION_OPTIONS` sont des valeurs non Null et non vides, l’en-tête TDS des notifications de requêtes qui contient les trois propriétés définies ci-dessus est envoyé au serveur. Cela se produit à chaque exécution de la commande. Si l’une des valeurs est Null (ou vide), l’en-tête n’est pas envoyé, et `DB_E_ERRORSOCCURRED` est déclenché (ou `DB_S_ERRORSOCCURRED` est déclenché, si les propriétés sont toutes les deux marquées comme facultatives). La valeur d'état est définie sur `DBPROPSTATUS_BADVALUE`. La validation se produit dans la phase d'exécution et de préparation. De la même façon, `DB_S_ERRORSOCCURED` est déclenché quand les propriétés de notification de requête sont définies pour les connexions sur les versions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avant [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Dans ce cas, la valeur d’état est `DBPROPSTATUS_NOTSUPPORTED`.

L’initialisation d’un abonnement ne garantit pas la bonne remise des messages suivants. De plus, aucun contrôle n’est effectué en termes de validité du nom du service spécifié.

> [!NOTE]
> La préparation des instructions n’entraînera jamais l’initialisation de l’abonnement. Seule l’exécution de l’instruction permet l’initiation. Les notifications de requêtes ne sont pas affectées par l’utilisation des services principaux d’OLE DB.

Pour plus d’informations sur le jeu de propriétés `DBPROPSET_SQLSERVERROWSET`, consultez [Propriétés et comportements de l'ensemble de lignes](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md).

## <a name="see-also"></a>Voir aussi

[Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)

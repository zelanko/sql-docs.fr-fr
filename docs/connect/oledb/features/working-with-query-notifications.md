---
title: Utilisation des notifications de requête | Microsoft Docs
description: Utilisation des notifications de requête dans le pilote OLE DB pour SQL Server
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
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419320"
---
# <a name="working-with-query-notifications"></a>Utilisation de notifications de requêtes

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

Les notifications de requêtes [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ont été introduites dans et OLE DB pilote pour SQL Server. Basées sur l’infrastructure de Service Broker SQL introduite dans SQL Server 2005 (9.x), les notifications de requêtes permettent aux applications d’être notifiées en cas de modification des données. Cette fonctionnalité est particulièrement utile pour les applications qui fournissent un cache d’informations d’une base de données, par exemple une application web, et qui doivent être notifiées en cas de modification des données sources.

En utilisant des notifications de requête, vous pouvez demander des notifications dans un délai d’attente spécifié lorsque les données sous-jacentes d’une requête sont modifiées. La demande spécifie les options de notification, notamment le nom du service, le texte du message et la valeur du délai d’attente au serveur. Les notifications sont remises par l’intermédiaire d’une file d’attente Service Broker qui peut être interrogée par les applications pour détecter les notifications disponibles.

La syntaxe de la chaîne des options de notifications de requêtes est :

`service=<service-name>[;(local database=<database> | broker instance=<broker instance>)]`

 Par exemple :

`service=mySSBService;local database=mydb`

Les abonnements aux notifications convivent au processus qui les initie. En effet, une application peut créer un abonnement aux notifications, puis se terminer. L’abonnement reste valide, et la notification a lieu si les données sont modifiées dans le délai d’attente imparti spécifié au moment de la création de l’abonnement. Une notification est identifiée par la requête exécutée, les options de notification et le texte du message. Vous pouvez l’annuler en définissant sa valeur de délai d’attente sur zéro.

Les notifications sont envoyées une seule fois. Pour être informé continuellement des modifications de données, créez un nouvel abonnement en exécutant à nouveau la requête après le traitement de chaque notification.

OLE DB pilote pour les applications SQL Server reçoit généralement des notifications [!INCLUDE[tsql](../../../includes/tsql-md.md)] à l’aide de la commande [Receive](../../../t-sql/statements/receive-transact-sql.md) . Elle utilise cette commande pour lire les notifications de la file d’attente associée au service spécifié dans les options de notification.

> [!NOTE]
> Les noms de tables doivent être qualifiés dans des requêtes pour lesquelles une notification est requise. Par exemple, `dbo.myTable`. Les noms de tables doivent être qualifiés avec des noms en deux parties. L'abonnement n'est pas valide si des noms en trois ou quatre parties sont utilisés.

L'infrastructure de notification repose sur une fonctionnalité de mise en file d'attente introduite dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. En général, les notifications générées au niveau du serveur sont envoyées par l’intermédiaire de ces files d’attente pour un traitement ultérieur.

Pour utiliser des notifications de requêtes, une file d’attente et un service doivent exister sur le serveur. Vous pouvez les créer à l’aide [!INCLUDE[tsql](../../../includes/tsql-md.md)] de la commande, similaire à ce qui suit:

```sql
CREATE QUEUE myQueue
CREATE SERVICE myService ON QUEUE myQueue
([https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification])
```

> [!NOTE]
> Le service doit utiliser le contrat prédéfini, comme indiqué plus haut.

## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver pour SQL Server

Le pilote OLE DB pour SQL Server prend en charge les notifications du consommateur lors de la modification de l’ensemble de lignes. Le consommateur reçoit une notification à chaque phase de la modification de l’ensemble de lignes et à chaque tentative de modification.

> [!NOTE]
> Le passage d’une requête de notifications au serveur avec **ICommand::Execute** est la seule méthode valide pour s’abonner à des notifications de requête avec OLE DB Driver pour SQL Server.

### <a name="dbpropsetsqlserverrowset-property-set"></a>Jeu de propriétés DBPROPSET_SQLSERVERROWSET

Pour prendre en charge les notifications de requêtes via OLE DB, OLE DB Driver pour SQL Server ajoute les nouvelles propriétés suivantes au jeu de propriétés `DBPROPSET_SQLSERVERROWSET`.

|Créer une vue d’abonnement|Type|Description|
|----------|----------|-----------------|
|SSPROP_QP_NOTIFICATION_TIMEOUT|VT_UI4|Nombre de secondes pendant lesquelles la notification de requête doit rester active.<br /><br /> La valeur par défaut est 432 000 secondes (5 jours). La valeur minimale est 1 seconde, et la valeur maximale est 2^31-1 secondes.|
|SSPROP_QP_NOTIFICATION_MSGTEXT|VT_BSTR|Texte du message de la notification. Ce texte est défini par l’utilisateur et n’a aucun format prédéfini.<br /><br /> Par défaut, la chaîne est vide. Spécifiez un message à l’aide de 1 à 2000 caractères.|
|SSPROP_QP_NOTIFICATION_OPTIONS|VT_BSTR|Options de notification de requêtes. Celles-ci sont spécifiées dans une chaîne avec la syntaxe *nom*=*valeur*. L'utilisateur est chargé de créer le service et de lire les notifications de la file d'attente.<br /><br /> La valeur par défaut est une chaîne vide.|

L’abonnement aux notifications est toujours validé. Cela se produit même si l’instruction a été exécutée dans une transaction utilisateur ou dans autocommit ou si la transaction dans laquelle l’instruction a été exécutée ou annulée. La notification du serveur est déclenchée lorsque l'une des conditions de notification non valides suivantes se produit : modification des données sous-jacentes ou du schéma ou expiration du délai d'attente imparti (selon l'opération qui se produit en premier). 

Les inscriptions de notification sont supprimées dès qu’elles sont déclenchées. Par conséquent, lorsque l’application reçoit des notifications, elle doit encore s’abonner si vous voulez obtenir d’autres mises à jour.

Une autre connexion ou un autre thread peut vérifier la file d'attente de destination pour les notifications. Par exemple :

```sql
WAITFOR (RECEIVE * FROM MyQueue); -- Where MyQueue is the queue name.
```

> [!NOTE]
> `SELECT *`ne supprime pas l’entrée de la file d’attente. Toutefois, `RECEIVE * FROM` le fait. Cela bloque un thread serveur si la file d'attente est vide. S’il existe des entrées de file d’attente au moment de l’appel, elles sont retournées immédiatement. Dans le cas contraire, l’appel attend jusqu’à ce qu’une entrée de file d’attente soit créée.

```sql
RECEIVE * FROM MyQueue
```

Cette instruction retourne immédiatement un jeu de résultats vide si la file d’attente est vide. Dans le cas contraire, elle retourne toutes les notifications de file d’attente.

Si `SSPROP_QP_NOTIFICATION_MSGTEXT` et`SSPROP_QP_NOTIFICATION_OPTIONS` sont non null et non vide, l’en-tête TDS des notifications de requête qui contient les trois propriétés définies ci-dessus sont envoyées au serveur. Cela se produit à chaque exécution de la commande. Si l’un d’eux est null (ou vide), l’en-tête `DB_E_ERRORSOCCURRED` n’est pas envoyé `DB_S_ERRORSOCCURRED` et est déclenché (ou est déclenché, si les propriétés sont toutes les deux marquées comme étant facultatives). La valeur d’État est alors définie `DBPROPSTATUS_BADVALUE`sur. La validation se produit lors de l’exécution et de la préparation. De la même façon, `DB_S_ERRORSOCCURED` est déclenché quand les propriétés de notification de requête sont définies pour les connexions sur les versions [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avant [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. La valeur d’État dans ce cas `DBPROPSTATUS_NOTSUPPORTED`est.

L’initialisation d’un abonnement ne garantit pas la bonne remise des messages suivants. De plus, aucun contrôle n’est effectué en termes de validité du nom du service spécifié.

> [!NOTE]
> La préparation des instructions ne provoque jamais l’initialisation de l’abonnement. Seule l’exécution des instructions permet l’initiation. Les notifications de requêtes ne sont pas affectées par l’utilisation de services OLE DB Core.

Pour plus d’informations sur `DBPROPSET_SQLSERVERROWSET` le jeu de propriétés, consultez [Propriétés et comportements](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md)de l’ensemble de lignes.

## <a name="see-also"></a>Voir aussi

[Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)

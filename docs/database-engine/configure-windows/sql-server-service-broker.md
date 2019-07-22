---
title: SQL Server Service Broker | Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL13.SWB.SSBMSGTYPEPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBCONTRACTPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBQUEUEPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBREMSVCBINDPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBROUTEPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBPRIORITYPROPERTIES.GENERAL.F1
- SQL13.SWB.SSBSERVICEPROPERTIES.GENERAL.F1
helpviewer_keywords:
- Broker See Service Broker
- SQL Server Service Broker
- Service Broker
ms.assetid: 8b8b3b57-fd46-44de-9a4e-e3a8e3999c1e
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 11dc9169ec88928c893d875b7051bfbf551c95fd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68034521"
---
# <a name="service-broker"></a>Service Broker
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssSB](../../includes/sssb-md.md)] fournit la prise en charge native de la messagerie et des files d’attente dans le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index). Les développeurs peuvent créer plus facilement des applications perfectionnées qui utilisent les composants de [!INCLUDE[ssDE](../../includes/ssde-md.md)] pour la communication entre des bases de données disparates, et créer des applications fiables et distribuées.  
  
## <a name="when-to-use-service-broker"></a>Quand utiliser Service Broker ?

 Utilisez les composants de Service Broker pour implémenter des fonctionnalités natives de traitement des messages asynchrones dans la base de données. Les développeurs d'applications qui utilisent [!INCLUDE[ssSB](../../includes/sssb-md.md)] peuvent distribuer les charges de données sur plusieurs bases de données sans développer des mécanismes de messagerie et de communication complexes. Service Broker réduit le travail de développement et de test car [!INCLUDE[ssSB](../../includes/sssb-md.md)] gère les chemins de communication dans le contexte d’une conversation. Les performances sont aussi meilleures. Par exemple, les bases de données frontales prenant en charge les sites Web peuvent enregistrer des informations et mettre des tâches intensives en file d'attente dans des bases de données principales. [!INCLUDE[ssSB](../../includes/sssb-md.md)] garantit que toutes les tâches sont gérées dans le contexte des transactions afin d’assurer une fiabilité et une cohérence techniques.  
  
## <a name="overview"></a>Vue d’ensemble

  Service Broker est un framework de remise de message qui vous permet de créer des applications natives orientées service dans la base de données. Contrairement aux fonctionnalités de traitement des requêtes classiques qui lisent constamment les données à partir des tables et les traitent au cours du cycle de vie de requête, dans une application orientée service vous avez des services de base de données qui échangent des messages. Chaque service dispose d’une file d’attente où les messages sont placés jusqu’à ce qu’ils soient traités.
  
![Service Broker](media/service-broker.png)
  
  Les messages dans les files d’attente peuvent être extraits à l’aide de la commande Transact-SQL `RECEIVE` ou par la procédure d’activation qui est appelée chaque fois que le message arrive dans la file d’attente.
  
### <a name="creating-services"></a>Création de services
 
  La création des services de base de données s’effectue à l’aide de l’instruction Transact-SQL [CREATE SERVICE](../../t-sql/statements/create-service-transact-sql.md). Le service peut être associée à la file d’attente de message créée à l’aide de l’instruction [CREATE QUEUE](../../t-sql/statements/create-queue-transact-sql.md) :
  
```sql
CREATE QUEUE dbo.ExpenseQueue;
GO
CREATE SERVICE ExpensesService
    ON QUEUE dbo.ExpenseQueue; 
```

### <a name="sending-messages"></a>Envoi de messages
  
  Les messages sont envoyés sur la conversation entre les services à l’aide de l’instruction Transact-SQL [SEND](../../t-sql/statements/send-transact-sql.md). Une conversation est un canal de communication établi entre les services à l’aide de l’instruction Transact-SQL `BEGIN DIALOG`. 
  
```sql
DECLARE @dialog_handle UNIQUEIDENTIFIER;

BEGIN DIALOG @dialog_handle  
FROM SERVICE ExpensesClient  
TO SERVICE 'ExpensesService';  
  
SEND ON CONVERSATION @dialog_handle (@Message) ;  
```
   Le message est envoyé vers `ExpenssesService` et placé dans `dbo.ExpenseQueue`. Comme aucune procédure d’activation n’est associée à cette file d’attente, le message reste dans la file d’attente jusqu’à ce qu’un utilisateur le lise.

### <a name="processing-messages"></a>Traitement des messages

   Les messages placés dans la file d’attente peuvent être sélectionnés à l’aide d’une requête `SELECT` standard. L’instruction `SELECT` ne modifie pas la file d’attente et ne supprime pas les messages. Pour lire et extraire les messages de la file d’attente, vous pouvez utiliser l’instruction Transact-SQL [RECEIVE](../../t-sql/statements/receive-transact-sql.md).

```sql
RECEIVE conversation_handle, message_type_name, message_body  
FROM ExpenseQueue; 
```

  Une fois que vous avez traité tous les messages de la file d’attente, vous devez fermer la conversation à l’aide de l’instruction Transact-SQL [END CONVERSATION](../../t-sql/statements/end-conversation-transact-sql.md).

## <a name="where-is-the-documentation-for-service-broker"></a>Emplacement de la documentation de Service Broker  
 La documentation de référence pour [!INCLUDE[ssSB](../../includes/sssb-md.md)] est incluse dans la documentation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . Cette documentation de référence comprend les sections suivantes :  
  
-   [Instructions DDL &#40;Data Definition Language &#41; &#40;Transact-SQL&#41;](../../t-sql/statements/statements.md) pour les instructions CREATE, ALTER et DROP  
  
-   [Instructions de Service Broker](../../t-sql/statements/service-broker-statements.md)  
  
-   [Affichages catalogue relatifs à Service Broker &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/service-broker-catalog-views-transact-sql.md)  
  
-   [Vues de gestion dynamique liées à Service Broker &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
-   [Utilitaire ssbdiagnose &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
 Consultez la [documentation précédemment publiée](https://go.microsoft.com/fwlink/?LinkId=231312) pour les concepts [!INCLUDE[ssSB](../../includes/sssb-md.md)] et pour les tâches de gestion et de développement. Cette documentation n'est pas reproduite dans la documentation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] en raison de quelques modifications apportées dans [!INCLUDE[ssSB](../../includes/sssb-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="whats-new-in-service-broker"></a>Nouveautés dans Service Broker  
 Aucune modification importante n'a été introduite dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  Les modifications suivantes ont été introduites dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  

### <a name="service-broker-and-azure-sql-database-managed-instance"></a>Service Broker et Azure SQL Database Managed Instance

- Service Broker entre instances n’est pas pris en charge. 
 - `sys.routes` – Prérequis : sélectionnez l’adresse à partir de sys.routes. L’adresse doit être LOCAL sur tous les itinéraires. Voir [sys.routes](../../relational-databases/system-catalog-views/sys-routes-transact-sql.md).
 - `CREATE ROUTE` – `CREATE ROUTE` n’est pas utilisable avec `ADDRESS` autre que `LOCAL`. Voir [CREATE ROUTE](https://docs.microsoft.com/sql/t-sql/statements/create-route-transact-sql).
 - `ALTER ROUTE` – `ALTER ROUTE` n’est pas utilisable avec `ADDRESS` autre que `LOCAL`. Voir [ALTER ROUTE](../../t-sql/statements/alter-route-transact-sql.md).  
  
### <a name="messages-can-be-sent-to-multiple-target-services-multicast"></a>Les messages peuvent être envoyés à des services cibles (multidiffusion).  
 La syntaxe de l’instruction [SEND &#40;Transact-SQL&#41;](../../t-sql/statements/send-transact-sql.md) a été étendue pour permettre la multidiffusion au moyen de la prise en charge de plusieurs descripteurs de conversation.  
  
### <a name="queues-expose-the-message-enqueued-time"></a>Les files d'attente exposent le temps d'empilement des messages.  
 Les files d’attente ont une nouvelle colonne, **message_enqueue_time**, qui indique depuis combien de temps un message est dans la file d’attente.  
  
### <a name="poison-message-handling-can-be-disabled"></a>La gestion des messages incohérents peut être désactivée  
 Les instructions [CREATE QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/create-queue-transact-sql.md) et [ALTER QUEUE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-queue-transact-sql.md) ont désormais la possibilité d’activer ou désactiver la gestion des messages incohérents en ajoutant la clause `POISON_MESSAGE_HANDLING (STATUS = ON | OFF)`. L’affichage catalogue **sys.service_queues** comprend maintenant la colonne **is_poison_message_handling_enabled** pour indiquer si le message incohérent est activé ou désactivé.  
  
### <a name="always-on-support-in-service-broker"></a>Prise en charge d’Always On dans Service Broker  
 Pour plus d’informations, consultez [Service Broker avec les groupes de disponibilité Always On (SQL Server)](../../database-engine/availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md).  
  
  


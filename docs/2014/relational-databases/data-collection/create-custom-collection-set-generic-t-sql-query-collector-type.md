---
title: Créer un jeu d’collections personnalisé qui utilise le type de collecteur requête T-SQL générique (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- T-SQL Query collector type
- collection sets [SQL Server], creating custom
ms.assetid: 6b06db5b-cfdc-4ce0-addd-ec643460605b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab21ad5fd65556dec639fd5ca6999d23e2de673b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84970469"
---
# <a name="create-a-custom-collection-set-that-uses-the-generic-t-sql-query-collector-type-transact-sql"></a>Créer un jeu d'éléments de collecte personnalisé qui utilise le type de collecteur Requête T-SQL générique (Transact-SQL)
  Vous pouvez créer un jeu d'éléments de collecte personnalisé avec des éléments de collecte qui utilisent le type de collecteur Requête T-SQL générique à l'aide des procédures stockées fournies avec le collecteur de données. Accomplir cette tâche implique l'utilisation de l'éditeur de requête dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour effectuer les procédures suivantes :  
  
-   Configurer les planifications de téléchargement.  
  
-   Définir et créer le jeu d'éléments de collecte.  
  
-   Définir et créer un élément de collecte.  
  
-   Vérifier que le jeu d'éléments de collecte et les éléments de collecte existent.  
  
> [!NOTE]  
>  Avant de créer un jeu d'éléments de collecte personnalisé, vous devez configurer des paramètres de collecte de données. Pour plus d’informations, consultez [Configurer des paramètres de collecte de données &#40;Transact-SQL&#41;](configure-data-collection-parameters-transact-sql.md).  
  
### <a name="define-and-create-the-collection-set"></a>Définir et créer le jeu d'éléments de collecte  
  
1.  Définissez un nouveau jeu d'éléments de collecte à l'aide de la procédure stockée sp_syscollector_create_collection_set.  
  
    ```  
    USE msdb;  
    DECLARE @collection_set_id int;  
    DECLARE @collection_set_uid uniqueidentifier;  
    EXEC sp_syscollector_create_collection_set   
        @name=N'DMV Test 1',   
        @collection_mode=0,   
        @description=N'This is a test collection set',   
        @logging_level=1,   
        @days_until_expiration=14,   
        @schedule_name=N'CollectorSchedule_Every_15min',   
        @collection_set_id=@collection_set_id OUTPUT,   
        @collection_set_uid=@collection_set_uid OUTPUT;  
    SELECT @collection_set_id, @collection_set_uid;  
    ```  
  
     Le mode de collecte peut être défini à 0 (avec mise en cache) ou à 1 (sans mise en cache).  
  
     Le niveau de journalisation peut être défini sur 0, 1 ou 2.  
  
     Les planifications préconfigurées suivantes sont fournies avec le collecteur de données :  
  
    -   CollectorSchedule_Every_5min  
  
    -   CollectorSchedule_Every_10min  
  
    -   CollectorSchedule_Every_15min  
  
    -   CollectorSchedule_Every_30min  
  
    -   CollectorSchedule_Every_60min  
  
    -   CollectorSchedule_Every_6h  
  
     Si vous ne souhaitez pas utiliser l'une des planifications fournies, vous pouvez en créer une et vous en servir pour le jeu d'éléments de collecte. Pour plus d’informations, consultez [Créer des planifications et les attacher à des travaux](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
### <a name="define-and-create-a-collection-item"></a>Définir et créer un élément de collecte  
  
1.  Le nouvel élément de collecte étant basé sur un type de collecteur générique déjà installé, vous pouvez exécuter le code suivant pour définir le GUID de sorte qu'il corresponde au type de collecteur Requête T-SQL générique.  
  
    ```sql  
    DECLARE @collector_type_uid uniqueidentifier;  
    SELECT @collector_type_uid = collector_type_uid FROM [msdb].[dbo].[syscollector_collector_types]   
    WHERE name = N'Generic T-SQL Query Collector Type';  
    DECLARE @collection_item_id int;  
    ```  
  
2.  Utilisez la procédure stockée sp_syscollector_create_collection_item pour créer l'élément de collecte. Déclarez le schéma de l'élément de collecte de manière à ce qu'il soit mappé au schéma requis pour le type de collecteur Requête T-SQL générique.  
  
    ```sql  
    EXEC sp_syscollector_create_collection_item   
        @name=N'Query Stats - Test 1',   
        @parameters=N'  
            <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
            <Query>  
            <Value>SELECT * FROM sys.dm_exec_query_stats</Value>  
            <OutputTable>dm_exec_query_stats</OutputTable>  
            </Query>  
            </ns:TSQLQueryCollector>',   
        @collection_item_id=@collection_item_id OUTPUT,   
        @frequency=5,   
        @collection_set_id=@collection_set_id,   
        @collector_type_uid=@collector_type_uid;  
    SELECT @collection_item_id;  
    ```  
  
### <a name="verify-that-the-new-collection-set-and-collection-item-exist"></a>Vérifier que le nouveau jeu d'éléments de collecte et l'élément de collecte existent  
  
1.  Avant de démarrer le nouveau jeu d'éléments de collecte, exécutez la requête suivante pour vérifier que le nouveau jeu d'éléments de collecte et son élément de collecte ont été créés.  
  
    ```sql  
    USE msdb;  
    SELECT * FROM syscollector_collection_sets;  
    SELECT * FROM syscollector_collection_items;  
    GO  
    ```  
  
     Vous pouvez également procéder à un contrôle visuel dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Dans l’Explorateur d’objets, développez le nœud **Gestion** , puis développez **Collecte de données**. Le nouveau jeu d'éléments de collecte s'affiche. Le cercle rouge sur l'icône du jeu d'éléments de collecte indique que ce dernier est arrêté.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant combine les exemples documentés dans les étapes précédentes. Notez que la fréquence de collecte définie pour l'élément de collecte (5 secondes) est ignorée, car le mode de collecte du jeu d'éléments de collecte est défini sur 0, ce qui correspond au mode avec mise en cache. Pour plus d'informations, consultez [Data Collection](data-collection.md).  
  
```sql  
USE msdb;  
  
DECLARE @collection_set_id int;  
DECLARE @collection_set_uid uniqueidentifier  
  
EXEC dbo.sp_syscollector_create_collection_set  
    @name = N'DMV Stats Test 1',  
    @collection_mode = 0,  
    @description = N'This is a test collection set',  
    @logging_level=1,  
    @days_until_expiration = 14,  
    @schedule_name=N'CollectorSchedule_Every_15min',  
    @collection_set_id = @collection_set_id OUTPUT,  
    @collection_set_uid = @collection_set_uid OUTPUT;  
SELECT @collection_set_id,@collection_set_uid;  
  
DECLARE @collector_type_uid uniqueidentifier;  
SELECT @collector_type_uid = collector_type_uid FROM syscollector_collector_types   
WHERE name = N'Generic T-SQL Query Collector Type';  
  
DECLARE @collection_item_id int;  
EXEC sp_syscollector_create_collection_item  
@name= N'Query Stats - Test 1',  
@parameters=N'  
<ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
<Query>  
  <Value>select * from sys.dm_exec_query_stats</Value>  
  <OutputTable>dm_exec_query_stats</OutputTable>  
</Query>  
 </ns:TSQLQueryCollector>',  
    @collection_item_id = @collection_item_id OUTPUT,  
    @frequency = 5, -- This parameter is ignored in cached mode  
    @collection_set_id = @collection_set_id,  
    @collector_type_uid = @collector_type_uid;  
SELECT @collection_item_id;  
  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql)   
 [Gérer les planifications](../../ssms/agent/manage-schedules.md)   
 [Démarrer ou arrêter un jeu d’éléments de collecte](start-or-stop-a-collection-set.md)  
  
  

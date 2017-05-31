---
title: "Ajouter un élément de collecte à un jeu d’éléments de collecte (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- collection items [SQL Server]
- collection sets [SQL Server], adding items
ms.assetid: 9fe6454e-8c0e-4b50-937b-d9871b20fd13
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 90261ca03da94b15b003da029f07d8804aaa1805
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="add-a-collection-item-to-a-collection-set-transact-sql"></a>Ajouter un élément de collecte à un jeu d'éléments de collecte (Transact-SQL)
  Vous pouvez ajouter un élément de collecte à un jeu d'éléments de collecte existant à l'aide des procédures stockées fournies avec le collecteur de données.  
  
 Effectuez les étapes suivantes à l'aide de l'éditeur de requête dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
### <a name="add-a-collection-item-to-a-collection-set"></a>Ajouter un élément de collecte à un jeu d'éléments de collecte  
  
1.  Arrêtez le jeu d’éléments de collecte auquel vous souhaitez ajouter l’élément en exécutant la procédure stockée **sp_syscollector_stop_collection_set** . Par exemple, pour arrêter un jeu d'éléments de collecte nommé « Test Collection Set », exécutez les instructions suivantes :  
  
    ```tsql  
    USE msdb  
    DECLARE @csid int  
    SELECT @csid = collection_set_id  
    FROM syscollector_collection_sets  
    WHERE name = 'Test Collection Set'  
    SELECT @csid  
    EXEC dbo.sp_syscollector_stop_collection_set @collection_set_id = @csid  
    ```  
  
    > [!NOTE]  
    >  Vous pouvez également arrêter le jeu d'éléments de collecte en utilisant l'Explorateur d'objets de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, consultez [Démarrer ou arrêter un jeu d’éléments de collecte](../../relational-databases/data-collection/start-or-stop-a-collection-set.md).  
  
2.  Déclarez le jeu d'éléments de collecte auquel vous souhaitez ajouter l'élément de collecte. Le code suivant fournit un exemple de la façon dont déclarer l'ID du jeu d'éléments de collecte.  
  
    ```tsql  
    DECLARE @collection_set_id_1 int  
    SELECT @collection_set_id_1 = collection_set_id FROM [msdb].[dbo].[syscollector_collection_sets]  
    WHERE name = N'Test Collection Set'; -- name of collection set  
    ```  
  
3.  Déclarez le type de collecteur. Le code suivant fournit un exemple de la façon dont déclarer le type de collecteur Requête T-SQL générique.  
  
    ```tsql  
    DECLARE @collector_type_uid_1 uniqueidentifier  
    SELECT @collector_type_uid_1 = collector_type_uid FROM [msdb].[dbo].[syscollector_collector_types]   
       WHERE name = N'Generic T-SQL Query Collector Type';  
    ```  
  
     Vous pouvez exécuter le code suivant pour obtenir la liste des types de collecteurs installés :  
  
    ```tsql  
    USE msdb  
    SELECT * from syscollector_collector_types  
    GO  
    ```  
  
4.  Exécutez la procédure stockée **sp_syscollector_create_collection_item** pour créer l’élément de collecte. Vous devez déclarer le schéma de l'élément de collecte de manière à ce qu'il soit mappé au schéma requis pour le type de collecteur voulu. L'exemple suivant utilise le schéma d'entrée Requête T-SQL générique.  
  
    ```tsql  
    DECLARE @collection_item_id int;  
    EXEC [msdb].[dbo].[sp_syscollector_create_collection_item]   
    @name=N'OS Wait Stats', --name of collection item  
    @parameters=N'  
    <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
     <Query>  
      <Value>select * from sys.dm_os_wait_stats</Value>  
      <OutputTable>os_wait_stats</OutputTable>  
    </Query>  
    </ns:TSQLQueryCollector>',  
    @collection_item_id = @collection_item_id OUTPUT,  
    @frequency = 60,  
    @collection_set_id = @collection_set_id_1, --- Provides the collection set ID number  
    @collector_type_uid = @collector_type_uid_1 -- Provides the collector type UID  
    SELECT @collection_item_id     
    ```  
  
5.  Avant de démarrer le jeu d'éléments de collecte mis à jour, exécutez la requête suivante pour vérifier que le nouvel élément de collecte a été créé :  
  
    ```xaml  
    USE msdb  
    SELECT * from syscollector_collection_sets  
    SELECT * from syscollector_collection_items  
    GO  
    ```  
  
     Les jeux d’éléments de collecte et leurs éléments de collecte figurent sous l’onglet **Résultats** .  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un jeu d’éléments de collecte personnalisé qui utilise le type de collecteur Requête T-SQL générique &#40;Transact-SQL&#41;](../../relational-databases/data-collection/create-custom-collection-set-generic-t-sql-query-collector-type.md)   
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  

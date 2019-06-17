---
title: Utilisation d’index Columnstore non-cluster | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 4c341fb8-7cb1-4cab-921b-e80b751d6c19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e97aed3a5a4f5b49e482479b58928d2092a314f9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62773785"
---
# <a name="using-nonclustered-columnstore-indexes"></a>Utilisation d'index columnstore non cluster
  Décrit les tâches clés pour l'utilisation d'un index columnstore non cluster sur une table [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Pour une présentation des index columnstore, consultez [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).  
  
 Pour plus d'informations sur les index columnstore cluster, consultez [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).  
  
## <a name="contents"></a>Sommaire  
  
-   [Créer un Index Columnstore non-cluster](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#load)  
  
-   [Modifier les données dans un Index Columnstore non-cluster](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#change)  
  
##  <a name="load"></a> Créer un Index Columnstore non-cluster  
 Pour charger des données dans un index non cluster, première charger des données dans une table rowstore traditionnelle stockée comme un segment de mémoire ou en cluster d’index et ensuite utiliser [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-columnstore-index-transact-sql) pour créer un index ColumnStore.  
  
 ![Chargement des données dans un index columnstore](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "le chargement des données dans un index columnstore")  
  
##  <a name="change"></a> Modifier les données dans un Index Columnstore non-cluster  
 Une fois que vous avez créé un index columnstore non cluster sur une table, vous ne pouvez pas modifier directement les données dans cette table. Une requête avec INSERT, UPDATE, DELETE ou MERGE échouera et renverra un message d'erreur. Pour ajouter ou modifier les données de la table, effectuez les tâches suivantes :  
  
-   Désactiver l’index columnstore. Vous pourrez ensuite mettre à jour les données de la table. Si vous désactivez l'index columnstore, vous pouvez le reconstruire lorsque vous avez fini de mettre à jour les données. Exemple :  
  
    ```  
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;  
    -- update mytable --  
    ALTER INDEX mycolumnstoreindex on mytable REBUILD  
    ```  
  
-   Supprimez l’index columnstore, mettre à jour la table, puis recréez l’index columnstore avec CREATE COLUMNSTORE INDEX. Exemple :  
  
    ```  
    DROP INDEX mycolumnstoreindex ON mytable  
    -- update mytable --  
    CREATE NONCLUSTERED COLUMNSTORE INDEX mycolumnstoreindex ON mytable;  
  
    ```  
  
-   Chargez les données dans une table intermédiaire qui n'a pas d'index columnstore. Créez un index columnstore sur la table intermédiaire. Basculez la table intermédiaire dans une partition vide de la table principale.  
  
-   Basculez une partition de la table avec l'index columnstore dans une table intermédiaire vide. S'il existe un index columnstore sur la table intermédiaire, désactivez-le. Effectuez toutes les mises à jour. Créez (ou reconstruisez) l'index columnstore. Rebasculez la table intermédiaire dans la partition (maintenant vide) de la table principale.  
  

  
  

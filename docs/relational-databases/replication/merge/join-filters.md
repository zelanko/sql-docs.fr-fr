---
title: "Filtres de jointure | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "filtres [réplication SQL Server], jointure"
  - "publications [réplication SQL Server], filtres de jointure"
  - "filtres de jointure de réplication de fusion [réplication SQL Server]"
  - "filtres de jointure"
ms.assetid: dd78fd8f-56e3-4582-9abd-6bc25c91e075
caps.latest.revision: 38
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 38
---
# Filtres de jointure
  Un filtre de jointure permet de filtrer une table en fonction du filtrage d'une table associée dans la publication. En général, une table parente est filtrée à l'aide d'un filtre paramétré ; un ou plusieurs filtres de jointure sont ensuite définis à peu près de la même façon que vous définissez une jointure entre des tables. Les filtres de jointure étendent le filtre paramétré de telle façon que les données des tables liées soient répliquées seulement si elles correspondent à la clause du filtre de jointure.  
  
 En règle générale, les filtres de jointure suivent les relations clé primaire/clé étrangère définies pour les tables auxquelles ils sont appliqués, mais ils ne sont pas strictement limités à ces relations. Le filtre de jointure peut être basé sur toute logique comparant des données associées dans deux tables.  
  
 Supposons les tables suivantes dans la base de données exemple [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)], qui sont associées via des relations de clé primaire à clé étrangère :  
  
-   **HumanResources.Employee**  
  
-   **Sales.SalesOrderHeader**  
  
-   **Sales.SalesOrderDetail**  
  
 Ces tables peuvent être utilisés dans une application pour prendre en charge une force de vente mobile, mais ils doivent être filtrées ainsi que chaque commercial existant dans la **HumanResources.Employee** table reçoit uniquement les données relatives aux commandes de leurs clients.  
  
 La première étape consiste à définir un filtre paramétrable sur la table parente, qui dans cet exemple est le **HumanResources.Employee** table. Cette table comprend la colonne **LoginID**, qui contient la connexion de chaque employé sous la forme *domain\login*. Pour filtrer cette table de façon à ce que chaque employé reçoive seulement les données qui le concernent, spécifiez la clause de filtre paramétré suivante :  
  
```  
LoginID = SUSER_SNAME()  
```  
  
 Ce filtre garantit que les abonnements de chaque employé contient seulement les données à partir de la **HumanResources.Employee** table correspondant à cet employé (dans ce cas est une seule ligne). Pour plus d'informations, voir [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 L'étape suivante consiste à étendre ce filtre à chacune des tables associées, à l'aide d'une syntaxe similaire à celle qui est utilisée pour spécifier une jointure entre deux tables. La première clause du filtre de jointure est :  
  
```  
Employee.EmployeeID = SalesOrderHeader.SalesPersonID  
```  
  
 Ceci fait que l'abonnement contient seulement les données des commandes concernant chacun des commerciaux. La seconde clause du filtre de jointure est :  
  
```  
SalesOrderHeader.SalesOrderID = SalesOrderDetail.SalesOrderID  
```  
  
 Ceci fait que l'abonnement contient seulement les données détaillées associées aux données des commandes pour chacun des commerciaux. Cet exemple montre une table jointe à chaque point ; il est également possible de joindre plusieurs tables à chaque point.  
  
 Filtres de jointure peuvent être ajoutés un à la fois dans l’Assistant Nouvelle Publication et **Propriétés de la Publication** boîte de dialogue, ou ils peuvent être ajoutés par programmation. Ils peuvent aussi être générés automatiquement via l'Assistant Nouvelle publication : vous spécifiez un filtre de lignes pour une table et des filtres de jointure sont appliqués à toutes les tables associées. Pour plus d’informations, consultez [définir et modifier une jointure filtre entre fusionner les Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md), [Générer automatiquement une valeur de joindre filtres entre fusion Articles & #40 ; SQL Server Management Studio & #41 ;](../../../relational-databases/replication/publish/automatically generate join filters between merge articles.md), et [définir un Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
## Optimisation des performances des filtres de jointure  
 Les performances des filtres de jointure peuvent être optimisées en suivant ces conseils :  
  
-   Limitez le nombre de tables dans la hiérarchie du filtre de jointure.  
  
     Les filtres de jointure peuvent impliquer un nombre illimité de tables, mais des filtres avec un grand nombre de tables peuvent avoir un impact significatif sur les performances lors du traitement de la fusion. Si vous générez des filtres de jointure pour au moins cinq tables, envisagez d'autres solutions : ne filtrez pas les petites tables, les tables qui ne changent pas ou les tables de recherche principales. Utilisez des filtres de jointure seulement entre des tables qui doivent être partitionnées entre des abonnements.  
  
-   Définir le **clé unique** option **True** le cas échéant.  
  
     Le traitement de fusion a des possibilités d'optimisation des performances spéciales si la colonne jointe dans le parent est unique. Si la condition de jointure est basée sur une colonne unique, définissez la **clé unique** option pour le filtre de jointure. Pour des informations sur la définition de cette option, consultez les rubriques Procédure dont la liste figure dans la section précédente.  
  
-   Vérifiez que les colonnes référencées dans les filtres de jointure sont indexées.  
  
     Si les colonnes référencées dans le filtre sont indexées, la réplication peut traiter les filtres plus efficacement.  
  
-   Ne créez pas de filtres de lignes équivalents aux filtres de jointure.  
  
     Il est possible de créer des filtres de lignes qui sont équivalents à des filtres de jointure en utilisant une sous-requête dans une clause WHERE, comme ceci :  
  
    ```  
    WHERE Customer.SalesPersonID IN (SELECT EmployeeID FROM Employee WHERE LoginID = SUSER_SNAME())   
    ```  
  
     Il est fortement recommandé que toutes les logiques de ce type soient exprimées dans un filtre de jointure plutôt que dans une sous-requête. Si votre application requiert qu'un filtre de lignes utilise une sous-requête, vérifiez que la sous-requête référence seulement des données de consultation qui ne font pas l'objet de modifications.  
  
## Voir aussi  
 [Filtrer des données publiées en vue de la réplication de fusion](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)   
 [Filtres de lignes paramétrés](../../../relational-databases/replication/merge/parameterized-row-filters.md)  
  
  
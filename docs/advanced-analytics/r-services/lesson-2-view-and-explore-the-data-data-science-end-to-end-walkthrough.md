---
title: "Le&#231;on 2 : Afficher et explorer les donn&#233;es (Proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
ms.assetid: d3835d6d-e68b-486d-81a0-81b717cc6134
caps.latest.revision: 32
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 26
---
# Le&#231;on 2 : Afficher et explorer les donn&#233;es (Proc&#233;dure pas &#224; pas pour une solution compl&#232;te de science des donn&#233;es)
L’exploration de données est une partie importante de la modélisation des données et implique l’examen de synthèses d’objets de données à utiliser dans les analyses, ainsi que la visualisation des données. Dans cette leçon, vous explorez les objets de données et générez des tracés en utilisant à la fois [!INCLUDE[tsql](../../includes/tsql-md.md)] et les fonctions R incluses dans [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
Ensuite, vous générez des tracés pour visualiser les données, en utilisant de nouvelles fonctions fournies par les packages installés avec [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)].  
  
> [!TIP]  
> Vous êtes déjà un utilisateur expérimenté de R ?  
>   
> Maintenant que vous avez téléchargé toutes les données et préparé l’environnement, vous êtes invité à exécuter le script R complet dans RStudio ou tout autre environnement, et à explorer les fonctionnalités par vous-même. Ouvrez simplement le fichier RSQL_Walkthrough.R, et sélectionnez et exécutez des lignes individuelles, ou exécutez la totalité du script en guise de démonstration.  
>   
> Pour obtenir des explications supplémentaires sur les fonctions RevoScaleR et des conseils sur l’utilisation des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans R, continuez le didacticiel. Il utilise exactement le même script.  
  
## <a name="verify-downloaded-data-using-sql"></a>Vérifier les données téléchargées à l’aide de SQL  
Tout d’abord, prenez le temps de vérifier que vos données ont été chargées correctement.  
  
1.  Connectez-vous à votre instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    Vous pouvez utiliser divers outils pour vous connecter aux bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les afficher.  
  
    -   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]    
    -   Explorateur de serveurs dans Visual Studio  
  
2.  Développez la base de données que vous avez créée. L’illustration suivante montre les nouvelles bases de données, tables et fonctions de **l’Explorateur de serveurs**.  
  
    ![new database objects created by script](../../advanced-analytics/r-services/media/rsql-e2e-ssms-newobjects.PNG "new database objects created by script")  
  
3.  Vous pouvez également exécuter des requêtes simples sur les données. Par exemple, dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], cliquez avec le bouton droit sur la table et sélectionnez **Sélectionner les 1000 premières lignes** pour générer et exécuter cette requête :  
  
    ```  
    SELECT TOP 1000 * FROM [dbo].[nyctaxi_sample]  
    ```  
    Si la table ne contient aucune donnée, consultez la section [Dépannage](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md) de la rubrique précédente.
      
4.  Pour afficher le schéma et les types des données, vous pouvez utiliser les vues de gestion système dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    ```  
    SELECT TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME, COLUMN_DEFAULT  
    FROM [TaxiSample].INFORMATION_SCHEMA.COLUMNS  
    WHERE TABLE_NAME = N'nyctaxi_sample';  
    ```  
  
    > [!TIP]  
    > Pour obtenir plus d’informations sur la création de la table de données, vous pouvez également consulter le script `create-db-tb-upload-data.sql`.  
  
### <a name="generate-summaries-using-sql"></a>Générer des synthèses à l’aide de SQL  
Un des atouts de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui en fait un bon assistant pour R est la possibilité d’effectuer des calculs très rapides basés sur un ensemble.  Dans le code utilisé pour créer la table de cette procédure pas à pas, un [index columnstore](../Topic/Columnstore%20Indexes%20Guide.md) a également été appliqué pour accélérer encore plus les calculs.   
  
```  
SELECT DISTINCT [passenger_count]  
    , ROUND (SUM ([fare_amount]),0) as TotalFares   
    , ROUND (AVG ([fare_amount]),0) as AvgFares  
FROM [dbo].[nyctaxi_sample]  
GROUP BY [passenger_count]   
ORDER BY  AvgFares desc  
```  

À l’étape suivante, vous utiliserez R pour générer des synthèses et des tracés plus sophistiqués à l’aide des données de SQL Server.  
  
## <a name="next-steps"></a>Étapes suivantes  
[Afficher et résumer des données à l’aide de R &#40;Procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/view-and-summarize-data-using-r-data-science-end-to-end-walkthrough.md)  
  
[Créer des graphiques et des tracés à l’aide de R &#40;Procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/create-graphs-and-plots-using-r-data-science-end-to-end-walkthrough.md)  
  
## <a name="previous-lesson"></a>Leçon précédente  
[Leçon 1 : Préparer les données &#40;Procédure pas à pas pour une solution complète de science des données&#41;](../../advanced-analytics/r-services/lesson-1-prepare-the-data-data-science-end-to-end-walkthrough.md)  
  
## <a name="see-also"></a>Voir aussi  
[Guide des index columnstore](../Topic/Columnstore%20Indexes%20Guide.md)  
  
  
  

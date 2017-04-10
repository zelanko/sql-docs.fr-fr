---
title: "Importer &#224; partir d&#39;une source de donn&#233;es multidimensionnelle (SSAS Tabulaire) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f0793ea-a4c7-42e9-b722-2164a454ebca
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Importer &#224; partir d&#39;une source de donn&#233;es multidimensionnelle (SSAS Tabulaire)
  Vous pouvez utiliser une base de données de cube Analysis Services comme source de données pour un modèle tabulaire. Pour importer des données à partir d'un cube Analysis Services, vous devez définir une requête MDX afin de sélectionner les données à importer.  
  
 Toutes les données contenues dans une base de données SQL Server Analysis Services peuvent être importées dans un modèle. Vous pouvez extraire tout ou partie d'une dimension ou obtenir des segments et des agrégats à partir du cube, tels que le cumul des ventes, mois par mois, pour l'année actuelle, etc. Toutefois, n'oubliez pas que toutes les données que vous importez à partir d'un cube sont aplaties. Par conséquent, si vous définissez une requête qui récupère des mesures le long de plusieurs dimensions, les données sont importées avec chaque dimension dans une colonne distincte.  
  
 Les cubes Analysis Services doivent être de version SQL Server 2005, SQL Server 2008, SQL Server 2008 R2, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]ou [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
### Pour importer des données à partir d'un cube Analysis Services  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Modèle** , puis sur **Importer à partir de la source de données**.  
  
2.  Sur la page **Connexion à une source de données** , sélectionnez **Microsoft Analysis Services**, puis cliquez sur **Suivant**.  
  
3.  Suivez les étapes de l'Assistant Importation de table. Vous pouvez spécifier une requête MDX sur la page **Spécifier une requête MDX** . Pour utiliser le concepteur de requêtes MDX, sur la page Spécifier une requête MDX, cliquez sur **Conception**.  
  
## Voir aussi  
 [Importer des données &#40;SSAS Tabulaire&#41;](../Topic/Import%20Data%20\(SSAS%20Tabular\).md)   
 [Sources de données prises en charge &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
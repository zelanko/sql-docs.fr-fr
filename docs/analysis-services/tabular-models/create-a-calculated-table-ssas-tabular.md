---
title: "Cr&#233;er une table calcul&#233;e (SSAS Tabulaire) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d7ff98a-82a9-4333-a7d3-7a95a6f2caf7
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Cr&#233;er une table calcul&#233;e (SSAS Tabulaire)
  Un *table calculée* est un objet calculé basé sur une requête ou une expression DAX, dérivé de tout ou partie des autres tables dans le même modèle.  
  
 Un problème de conception courant que les tables calculées peuvent résoudre est la présentation d’une dimension de rôle actif dans un contexte spécifique pour vous permettre de l'exposer comme une structure de requête dans les applications clientes.  Vous vous souvenez peut-être qu'une dimension de rôle actif est une simple table présentée dans plusieurs contextes : un exemple classique est la table Date, représentée par OrderDate, ShipDate ou DueDate, en fonction de la relation de clé étrangère. En créant explicitement une table calculée pour ShipDate, vous obtenez une table autonome et disponible pour les requêtes, et totalement opérationnelle comme toute autre table.  
  
 Une deuxième utilisation d’une table calculée est la configuration d’un ensemble de lignes filtré ou d’un sous-ensemble ou sur-ensemble de colonnes provenant d’autres tables existantes. Cela vous permet de conserver intacte la table d’origine, tout en créant des variations de cette table pour prendre en charge des scénarios spécifiques.  
  
 Pour tirer le meilleur parti des tables calculées, vous devez connaître quelques expressions DAX. Lorsque vous utilisez des expressions pour votre table, il peut être utile de savoir qu'une table calculée contient une partition unique avec un élément DAXSource, où l'expression est une expression DAX.  
Il existe un élément CalculatedTableColumn pour chaque colonne renvoyée par l'expression, où SourceColumn est le nom de la colonne retournée (identique à celui de DataColumns sur les tables non calculées).  
  
## Comment créer une table calculée  
  
1.  Vérifiez d'abord que le modèle tabulaire affiche un niveau de compatibilité de 1200. Vous pouvez vérifier la propriété **Niveau de compatibilité** sur le modèle dans SSDT.  
  
2.  Basculez en mode Données. Vous ne pouvez pas créer une table calculée dans la vue de diagramme.  
  
3.  Sélectionnez **Table** > **Nouvelle table calculée**.  
  
4.  Tapez ou collez une expression DAX (voir ci-dessous pour quelques suggestions).  
  
5.  Nommez la table.  
  
6.  Créez des relations vers d'autres tables dans le modèle. Consultez [Créer une relation entre deux tables &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/create-a-relationship-between-two-tables-ssas-tabular.md) si vous avez besoin d’aide pour cette étape.  
  
7.  Référencez la table dans les calculs ou expressions de votre modèle, ou utilisez **Analyser dans Excel** pour une exploration des données ad hoc.  
  
### Répliquer une dimension de rôle actif  
 Dans la barre de formule, entrez une formule DAX qui obtient une copie d’une autre table. Après avoir rempli la table calculée, attribuez-lui un nom descriptif puis définissez une relation qui utilise la clé étrangère spécifique au rôle. Par exemple, dans la base de données Adventure Works, vous pouvez créer une table calculée pour la date d'échéance et utiliser la valeur DueDateKey comme base d'une relation vers la table de faits.  
  
```  
=DimDate  
```  
  
### Jeu de données synthétisé ou filtré  
 Dans la barre de formule, entrez une expression DAX afin de filtrer, résumer ou manipuler un jeu de données pour contenir les lignes souhaitées. Cet exemple regroupe les données par ventes, par couleur et par devise.  
  
```  
=SUMMARIZECOLUMNS(DimProduct[Color]  
, DimCurrency[CurrencyName]   
, "Sales" , SUM(FactInternetSales[SalesAmount])  
)  
```  
  
### Sur-ensemble utilisant des colonnes de plusieurs tables  
 Dans la barre de formule, entrez une expression DAX qui combine des colonnes provenant de plusieurs tables. Dans ce cas, le résultat de la requête affiche la catégorie de produit pour chaque devise.  
  
```  
=CROSSJOIN(DimProductCategory, DimCurrency)  
```  
  
## Voir aussi  
 [Niveau de compatibilité pour les modèles tabulaires dans Analysis Services](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)   
 [Langage DAX &#40;Data Analysis Expressions&#41; dans Analysis Services](../Topic/Data%20Analysis%20Expressions%20\(DAX\)%20in%20Analysis%20Services.md)   
 [Fonctionnement de DAX dans les modèles tabulaires &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)  
  
  
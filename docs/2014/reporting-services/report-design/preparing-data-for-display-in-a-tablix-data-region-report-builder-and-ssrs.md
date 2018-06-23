---
title: Préparation des données à afficher dans une région de données de tableau matriciel (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fbb00dc6-7887-480c-b771-cab6fecb8dcc
caps.latest.revision: 4
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: bde345380c4fbf8531a74005d307d0b319183760
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140226"
---
# <a name="preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs"></a>Préparation des données à afficher dans une région de données de tableau matriciel (Générateur de rapports et SSRS)
  Une région de données de tableau matriciel affiche les données d'un dataset. Vous pouvez afficher toutes les données récupérées pour le dataset ou créer des filtres afin d'afficher uniquement un sous-ensemble de données. Vous pouvez également ajouter des expressions conditionnelles pour combler des valeurs NULL ou modifier la requête de dataset afin d'inclure des colonnes qui définissent l'ordre de tri d'une colonne existante.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="working-with-nulls-and-blanks-in-field-values"></a>Utilisation de valeurs NULL et d'espaces dans les valeurs de champ  
 Les données de la collection de champs d'un dataset incluent toutes les valeurs extraites de la source de données au moment de l'exécution, y compris les valeurs NULL et les espaces. Normalement, les valeurs NULL et les espaces sont indifférenciables. C'est le comportement souhaité dans la plupart des cas. Par exemple, les fonctions d’agrégation numériques comme [somme](report-builder-functions-sum-function.md) et [Avg](report-builder-functions-avg-function.md) ignorent les valeurs null. Pour plus d’informations, consultez [Informations de référence sur les fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).  
  
 Si vous souhaitez gérer les valeurs NULL différemment, vous pouvez utiliser des expressions conditionnelles ou du code personnalisé pour substituer une valeur personnalisée à la valeur NULL. Par exemple, l’expression suivante substitue le texte `Null` quand une valeur null est présente dans le champ `[Size]`.  
  
```  
=IIF(Fields!Size.Value IS NOTHING,"Null",Fields!Size.Value)  
```  
  
 Pour plus d’informations sur la suppression des valeurs null dans vos données avant d’extraire les données d’une source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de requêtes [!INCLUDE[tsql](../../includes/tsql-md.md)] , consultez « Valeurs Null » et « Valeurs Null et jointures » dans la documentation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au sein de la [documentation en ligne SQL Server](http://go.microsoft.com/fwlink/?linkid=120955).  
  
## <a name="handling-null-field-names"></a>Gestion de noms de champ NULL  
 Il est acceptable de tester une expression à la recherche de valeurs NULL tant que le champ lui-même existe dans le jeu de résultats de la requête. À partir de code personnalisé, vous pouvez vérifier si le champ lui-même est présent dans la collection de champs retournée par la source de données au moment de l'exécution. Pour plus d’informations, consultez [Référence à une collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](built-in-collections-dataset-fields-collection-references-report-builder.md).  
  
## <a name="adding-a-sort-order-column"></a>Ajout d'une colonne Ordre de tri  
 Par défaut, vous pouvez trier alphabétiquement les valeurs dans un champ de dataset. Pour les trier dans un ordre différent, vous pouvez ajouter une nouvelle colonne à votre dataset qui définit l'ordre de tri souhaité dans une région de données. Par exemple, pour trier les données en fonction du champ `[Color]` en commençant par les éléments noirs et blancs, vous pouvez ajouter une colonne `[ColorSortOrder]`, comme le montre la requête suivante :  
  
```  
SELECT ProductID, p.Name, Color,  
   CASE  
      WHEN p.Color = 'White' THEN 1  
      WHEN p.Color = 'Black' THEN 2  
      WHEN p.Color = 'Blue' THEN 3  
      WHEN p.Color = 'Yellow' THEN 4  
      ELSE 5  
   END As ColorSortOrder  
FROM Production.Product p  
```  
  
 Pour trier une région de données de table conformément à cet ordre de tri, affectez la valeur `=Fields!ColorSortOrder.Value`à l’expression de tri sur le groupe de détails. Pour plus d’informations, consultez [Trier des données dans une région de données &#40;Générateur de rapports et SSRS&#41;](sort-data-in-a-data-region-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](../report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Filtrer, regrouper et trier les données &#40;rapport Générateur et SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  
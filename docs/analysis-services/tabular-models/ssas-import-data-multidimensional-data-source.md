---
title: "Importer à partir d’une Source de données multidimensionnelle (SSAS tabulaire) | Documents Microsoft"
ms.custom: 
ms.date: 05/22/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f0793ea-a4c7-42e9-b722-2164a454ebca
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4aaa43e745c86cd493279fe8bd875d376f8185c0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="import-data---multidimensional-data-source"></a>Importer des données - Source de données multidimensionnelle
  Vous pouvez utiliser une base de données de cube Analysis Services comme source de données pour un modèle tabulaire. Pour importer des données à partir d'un cube Analysis Services, vous devez définir une requête MDX afin de sélectionner les données à importer.  
  
 Toutes les données contenues dans une base de données SQL Server Analysis Services peuvent être importées dans un modèle. Vous pouvez extraire tout ou partie d'une dimension ou obtenir des segments et des agrégats à partir du cube, tels que le cumul des ventes, mois par mois, pour l'année actuelle, etc. Toutefois, n'oubliez pas que toutes les données que vous importez à partir d'un cube sont aplaties. Par conséquent, si vous définissez une requête qui récupère des mesures le long de plusieurs dimensions, les données sont importées avec chaque dimension dans une colonne distincte.  
  
 Les cubes Analysis Services doivent être de version SQL Server 2005, SQL Server 2008, SQL Server 2008 R2, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]ou [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
### <a name="to-import-data-from-an-analysis-services-cube"></a>Pour importer des données à partir d'un cube Analysis Services  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Modèle** , puis sur **Importer à partir de la source de données**.  
  
2.  Sur la page **Connexion à une source de données** , sélectionnez **Microsoft Analysis Services**, puis cliquez sur **Suivant**.  
  
3.  Suivez les étapes de l'Assistant Importation de table. Vous pouvez spécifier une requête MDX sur la page **Spécifier une requête MDX** . Pour utiliser le concepteur de requêtes MDX, sur la page Spécifier une requête MDX, cliquez sur **Conception**.  
  
## <a name="see-also"></a>Voir aussi  
 [Importer des données &#40;SSAS Tabulaire&#41;](http://msdn.microsoft.com/library/6617b2a2-9f69-433e-89e0-4c5dc92982cf)   
 [Sources de données prises en charge &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
  

---
title: Importer à partir d’une Source de données multidimensionnelle (SSAS tabulaire) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f0793ea-a4c7-42e9-b722-2164a454ebca
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 6ad945994bda3f9198d3e686a3ce52ea02f496fb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038472"
---
# <a name="import-from-a-multidimensional-data-source-ssas-tabular"></a>Importer à partir d'une source de données multidimensionnelle (SSAS Tabulaire)
  Vous pouvez utiliser une base de données de cube Analysis Services comme source de données pour un modèle tabulaire. Pour importer des données à partir d'un cube Analysis Services, vous devez définir une requête MDX afin de sélectionner les données à importer.  
  
 Toutes les données contenues dans une base de données SQL Server Analysis Services peuvent être importées dans un modèle. Vous pouvez extraire tout ou partie d'une dimension ou obtenir des segments et des agrégats à partir du cube, tels que le cumul des ventes, mois par mois, pour l'année actuelle, etc. Toutefois, n'oubliez pas que toutes les données que vous importez à partir d'un cube sont aplaties. Par conséquent, si vous définissez une requête qui récupère des mesures le long de plusieurs dimensions, les données sont importées avec chaque dimension dans une colonne distincte.  
  
 Les cubes Analysis Services doivent être de version SQL Server 2005, SQL Server 2008, SQL Server 2008 R2, [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]ou [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
### <a name="to-import-data-from-an-analysis-services-cube"></a>Pour importer des données à partir d'un cube Analysis Services  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], cliquez sur le menu **Modèle** , puis sur **Importer à partir de la source de données**.  
  
2.  Sur la page **Connexion à une source de données** , sélectionnez **Microsoft Analysis Services**, puis cliquez sur **Suivant**.  
  
3.  Suivez les étapes de l'Assistant Importation de table. Vous pouvez spécifier une requête MDX sur la page **Spécifier une requête MDX** . Pour utiliser le concepteur de requêtes MDX, sur la page Spécifier une requête MDX, cliquez sur **Conception**.  
  
## <a name="see-also"></a>Voir aussi  
 [Importer des données &#40;SSAS tabulaire&#41;](import-data-ssas-tabular.md)   
 [Sources de données prises en charge &#40;SSAS Tabulaire&#41;](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
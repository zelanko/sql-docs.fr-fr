---
title: Classés de colonnes (exploration de données) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content types [data mining]
- STDEV column
- VARIANCE column
- PROBABLILITY column
- PROBABILITY_STDEV column
- columns [data mining], classified
- classified columns [data mining]
- PROBABILITY_VARIANCE column
- SUPPORT column
ms.assetid: 68bf3b78-dc12-497c-898f-b43a45646123
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c00a3e1e85beebba351340a9cacad5100e96dff6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050933"
---
# <a name="classified-columns-data-mining"></a>Colonnes classifiées (exploration de données)
  Lorsque vous définissez une colonne classée, vous créez une relation entre la colonne actuelle et une autre colonne de la structure d'exploration de données. Les données de la colonne de structure d'exploration de données que vous désignez comme colonne classée contiennent des informations catégorielles qui décrivent les valeurs dans une autre colonne de la structure d'exploration de données.  
  
 Par exemple, vous avez deux colonnes avec des données numériques : une colonne, [achats annuels], contient tous les achats annuels par client pour une année civile spécifique, et l’autre colonne, [écarts types], contient les écarts types de ces valeurs. Dans ce cas, vous pouvez indiquer la colonne [achats annuels] comme colonne classifiée, et le modèle peut utiliser cette relation dans l’analyse.  
  
> [!NOTE]  
>  Les algorithmes fournis dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne prennent pas en charge l’utilisation des colonnes classifiées ; cette fonctionnalité est fournie pour une utilisation dans la création d’algorithmes personnalisés.  
  
## <a name="defining-a-classified-column"></a>Définition d'une colonne classée  
 Le type de données d’une colonne classée doit être `Long` ou `Double`.  
  
 La liste suivante décrit les types de contenu pris en charge par [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour les colonnes classifiées.  
  
 **PROBABILITY**  
 La valeur de la colonne représente la probabilité de la valeur associée et est comprise entre 0 et 1.  
  
 **VARIANCE**  
 La valeur de la colonne représente la variance de la valeur associée.  
  
 **STDEV**  
 La valeur de la colonne représente l'écart type de la valeur associée.  
  
 **PROBABILITY_VARIANCE**  
 La valeur de la colonne représente la variance de la probabilité de la valeur associée.  
  
 **PROBABILITY_STDEV**  
 La valeur de la colonne représente l'écart type de la probabilité de la valeur associée.  
  
 **SUPPORT**  
 La valeur de la colonne représente le poids, ou facteur de réplication de cas, de la valeur associée.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de contenu &#40;d’exploration de données&#41;](content-types-data-mining.md)   
 [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](mining-structures-analysis-services-data-mining.md)   
 [Types de données &#40;d’exploration de données&#41;](data-types-data-mining.md)  
  
  
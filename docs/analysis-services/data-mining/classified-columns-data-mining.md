---
title: "Colonnes classifi&#233;es (exploration de donn&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "types de contenu [exploration de données]"
  - "STDEV (colonne)"
  - "VARIANCE (colonne)"
  - "PROBABLILITY (colonne)"
  - "PROBABILITY_STDEV (colonne)"
  - "colonnes [exploration de données], classifiées"
  - "colonnes classifiées [exploration de données]"
  - "PROBABILITY_VARIANCE (colonne)"
  - "SUPPORT (colonne)"
ms.assetid: 68bf3b78-dc12-497c-898f-b43a45646123
caps.latest.revision: 26
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 26
---
# Colonnes classifi&#233;es (exploration de donn&#233;es)
  Lorsque vous définissez une colonne classée, vous créez une relation entre la colonne actuelle et une autre colonne de la structure d'exploration de données. Les données de la colonne de structure d'exploration de données que vous désignez comme colonne classée contiennent des informations catégorielles qui décrivent les valeurs dans une autre colonne de la structure d'exploration de données.  
  
 Par exemple, vous avez deux colonnes avec des données numériques : une colonne, [achats annuels], contient tous les achats annuels par client pour une année civile spécifique, et l’autre colonne, [écarts types], contient les écarts types de ces valeurs. Dans ce cas, vous pouvez indiquer la colonne [achats annuels] comme colonne classifiée, et le modèle peut utiliser cette relation dans l’analyse.  
  
> [!NOTE]  
>  Les algorithmes fournis dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ne prennent pas en charge l’utilisation des colonnes classifiées ; cette fonctionnalité est fournie pour une utilisation dans la création d’algorithmes personnalisés.  
  
## Définition d'une colonne classée  
 Le type de données d’une colonne classifiée doit être **Long** ou **Double**.  
  
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
  
## Voir aussi  
 [Types de contenu &#40;exploration de données&#41;](../../analysis-services/data-mining/content-types-data-mining.md)   
 [Structures d’exploration de données &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)   
 [Types de données &#40;exploration de données&#41;](../../analysis-services/data-mining/data-types-data-mining.md)  
  
  
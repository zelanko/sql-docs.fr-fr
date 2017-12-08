---
title: Calculs (SSAS tabulaire) | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: tabular-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 738816e3-0e1d-44a5-8d1b-81068dce8ac0
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e65847285ccfd187c0dd58824a46d1dea1271a34
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="calculations-ssas-tabular"></a>Calculs (SSAS Tabulaire)
  Après avoir importé des données dans votre modèle, vous pouvez ajouter des calculs pour agréger, filtrer, étendre, combiner et sécuriser les données. Les modèles tabulaires utilisent DAX (Data Analysis Expressions), un langage de formule pour la création de calculs personnalisés. Dans les modèles tabulaires, les calculs que vous pouvez créer à l'aide de formules DAX sont utilisés dans des *colonnes calculées*, des *mesures*et des *filtres de lignes*.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Fonctionnement de DAX dans les modèles tabulaires &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)|Décrit le langage de formule DAX (Data Analysis Expressions) utilisé pour créer des calculs pour les colonnes calculées, les mesures et les filtres de lignes dans les modèles tabulaires.|  
|[Compatibilité des formules DAX en mode DirectQuery (SQL Server Analysis Services)](http://msdn.microsoft.com/en-us/981b6a68-434d-4db6-964e-d92f8eb3ee3e)|Décrit les différences, répertorie les fonctions qui ne sont pas prises en charge en mode DirectQuery et les fonctions prises en charge mais pouvant retourner des résultats différents.|  
|[Référence DAX (Data Analysis Expressions)](http://msdn.microsoft.com/en-us/70a82136-0926-4a91-bcb3-e18e82593b0d)|Cette section fournit une description détaillée de la syntaxe, des opérateurs et des fonctions DAX.|  
  
> [!NOTE]  
>  Les tâches pas à pas de création des calculs ne sont pas fournies dans cette section. Étant donné que les calculs sont spécifiés dans les colonnes calculées, les mesures et les filtres de lignes (dans les rôles), les instructions indiquant où créer des formules DAX sont fournies dans les tâches associées à ces fonctionnalités. Pour plus d’informations, consultez [Créer une colonne calculée &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/ssas-calculated-columns-create-a-calculated-column.md), [Créer et gérer des mesures &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md), et [Créer et gérer des rôles &#40;SSAS Tabulaire&#41;](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md).  
  
> [!NOTE]  
>  Bien que DAX puisse également être utilisé pour interroger un modèle tabulaire, les rubriques de cette section traitent spécifiquement de l'utilisation des formules DAX pour créer des calculs.  
  
  

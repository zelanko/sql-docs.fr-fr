---
title: Calculs (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 738816e3-0e1d-44a5-8d1b-81068dce8ac0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b19dce00f95559aec77c8d02c86631faadc466b7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48100479"
---
# <a name="calculations-ssas-tabular"></a>Calculs (SSAS Tabulaire)
  Après avoir importé des données dans votre modèle, vous pouvez ajouter des calculs pour agréger, filtrer, étendre, combiner et sécuriser les données. Les modèles tabulaires utilisent DAX (Data Analysis Expressions), un langage de formule pour la création de calculs personnalisés. Dans les modèles tabulaires, les calculs que vous pouvez créer à l'aide de formules DAX sont utilisés dans des *colonnes calculées*, des *mesures*et des *filtres de lignes*.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Présentation de DAX dans les modèles tabulaires &#40;SSAS tabulaire&#41;](understanding-dax-in-tabular-models-ssas-tabular.md)|Décrit le langage de formule DAX (Data Analysis Expressions) utilisé pour créer des calculs pour les colonnes calculées, les mesures et les filtres de lignes dans les modèles tabulaires.|  
|[Compatibilité des formules en Mode DirectQuery](../dax-formula-compatibility-in-directquery-mode-ssas-2014.md)|Décrit les différences, répertorie les fonctions qui ne sont pas prises en charge en mode DirectQuery et les fonctions prises en charge mais pouvant retourner des résultats différents.|  
|[Data Analysis Expressions &#40;DAX&#41; référence](https://msdn.microsoft.com/library/gg413422(v=sql.120).aspx)|Cette section fournit une description détaillée de la syntaxe, des opérateurs et des fonctions DAX.|  
  
> [!NOTE]  
>  Les tâches pas à pas de création des calculs ne sont pas fournies dans cette section. Étant donné que les calculs sont spécifiés dans les colonnes calculées, les mesures et les filtres de lignes (dans les rôles), les instructions indiquant où créer des formules DAX sont fournies dans les tâches associées à ces fonctionnalités. Pour plus d’informations, consultez [Créer une colonne calculée &#40;SSAS Tabulaire&#41;](ssas-calculated-columns-create-a-calculated-column.md), [Créer et gérer des mesures &#40;SSAS Tabulaire&#41;](measures-ssas-tabular.md), et [Créer et gérer des rôles &#40;SSAS Tabulaire&#41;](roles-ssas-tabular.md).  
  
> [!NOTE]  
>  Bien que DAX puisse également être utilisé pour interroger un modèle tabulaire, les rubriques de cette section traitent spécifiquement de l'utilisation des formules DAX pour créer des calculs.  
  
  

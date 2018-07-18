---
title: Calculs | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f2f137312af7b4ef7d77334b3830cd337a849f42
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983921"
---
# <a name="calculations"></a>Calculs 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Après avoir importé des données dans votre modèle, vous pouvez ajouter des calculs pour agréger, filtrer, étendre, combiner et sécuriser les données. Les modèles tabulaires utilisent DAX (Data Analysis Expressions), un langage de formule pour la création de calculs personnalisés. Dans les modèles tabulaires, les calculs que vous pouvez créer à l'aide de formules DAX sont utilisés dans des *colonnes calculées*, des *mesures*et des *filtres de lignes*.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Utilisation de DAX dans les modèles tabulaires](../../analysis-services/tabular-models/understanding-dax-in-tabular-models-ssas-tabular.md)|Décrit le langage de formule DAX (Data Analysis Expressions) utilisé pour créer des calculs pour les colonnes calculées, les mesures et les filtres de lignes dans les modèles tabulaires.|  
|[Compatibilité des formules DAX en mode DirectQuery](http://msdn.microsoft.com/981b6a68-434d-4db6-964e-d92f8eb3ee3e)|Décrit les différences, répertorie les fonctions qui ne sont pas prises en charge en mode DirectQuery et les fonctions prises en charge mais pouvant retourner des résultats différents.|  
|[Référence de Data Analysis Expressions (DAX)](http://msdn.microsoft.com/70a82136-0926-4a91-bcb3-e18e82593b0d)|Cette section fournit une description détaillée de la syntaxe, des opérateurs et des fonctions DAX.|  
  
> [!NOTE]  
>  Les tâches pas à pas de création des calculs ne sont pas fournies dans cette section. Étant donné que les calculs sont spécifiés dans les colonnes calculées, les mesures et les filtres de lignes (dans les rôles), les instructions indiquant où créer des formules DAX sont fournies dans les tâches associées à ces fonctionnalités. Pour plus d’informations, consultez [créer une colonne calculée](../../analysis-services/tabular-models/ssas-calculated-columns-create-a-calculated-column.md), [créer et gérer des mesures](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md), et [créer et gérer les rôles](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md).  
  
> [!NOTE]  
>  Bien que DAX puisse également être utilisé pour interroger un modèle tabulaire, les rubriques de cette section traitent spécifiquement de l'utilisation des formules DAX pour créer des calculs.  
  
  

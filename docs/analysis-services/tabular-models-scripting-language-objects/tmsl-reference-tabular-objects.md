---
title: "Définitions d’objets dans le tableau de modèle un langage de script (TMSL) | Documents Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 486f0507-cec6-4672-b947-0bb61d1cbc46
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: f03fce7d1159e6fe7d34024e7cf63167024b752b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="tmsl-reference---tabular-objects"></a>Référence TMSL - objets tabulaires
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Permet aux applications qui créer, utiliser ou administrer les bases de données tabulaires ou qui se connectent à une instance de SQL Server 2016 Analysis Services en mode tabulaire, le script langage TMSL (Tabular Model) pour les commandes et les représentations sous forme de l’objet au format JSON.  
  
 Cet article décrit les principaux objets du schéma TMSL utilisées dans les scripts générés par SQL Server Management Studio, SQL Server Data Tools (SSDT) et PowerShell AMO.  
  
 Définitions d’objet dans JSON et utilisées dans les commandes TMSL telles que Create, Alter et de suppression. Consultez [commandes sous forme de tableau de modèle un langage de script &#40; TMSL &#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md) pour obtenir la liste de commandes.  
  
## <a name="main-objects"></a>Objets principaux  
 Le tableau suivant est la liste des objets couramment utilisés dans un script TMSL.  
  
|||  
|-|-|  
|[Objet de base de données &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)|Définit une base de données tabulaire au niveau de compatibilité 1200 ou supérieur, basé sur un modèle ayant le même niveau.|  
|[Objet de modèle &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md)|Définit un modèle tabulaire au niveau de compatibilité 1200 ou supérieur.|  
|[Objet de sources de données &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)|Définit une connexion à une source de données utilisée lors de l’importation pour charger le modèle, ou pour transmettre des requêtes lorsque le modèle est en mode DirectQuery.|  
|[Objet tables &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)|Spécifie les tables du modèle.|  
|[Objet de partitions &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)|Définit le stockage d’ensembles de lignes de table, y compris les tables calculées.|  
|[Objet de relations &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md)|Définit les relations entre les tables.|  
|[Objet rôles &#40; TMSL &#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)|Définit les autorisations, les membres et les filtres de sécurité qui contrôlent l’accès aux données et aux opérations.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Informations de référence sur TMSL &#40;Tabular Model Scripting Language&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

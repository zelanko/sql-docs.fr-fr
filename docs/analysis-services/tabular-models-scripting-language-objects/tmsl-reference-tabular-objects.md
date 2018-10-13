---
title: Langage de script (TMSL) de modèle de définitions d’objets dans tabulaire | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tmsl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: de968c32f8c00132157a5b1b7a6682adc7148446
ms.sourcegitcommit: b75fc8cfb9a8657f883df43a1f9ba1b70f1ac9fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48851744"
---
# <a name="tmsl-reference---tabular-objects"></a>Informations de référence sur TMSL - Objets tabulaires
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Les applications qui créer, utiliser ou administrer les bases de données tabulaires ou qui se connectent à une instance de SQL Server 2016 Analysis Services en mode tabulaire, peuvent utiliser le modèle tabulaire Scripting Language (TMSL) pour les commandes et les représentations sous forme de l’objet au format JSON.  
  
 Cet article décrit les principaux objets du schéma TMSL utilisées dans les scripts générés par SQL Server Management Studio, SQL Server Data Tools (SSDT) et PowerShell AMO.  
  
 Définitions d’objet sont au format JSON et utilisées dans les commandes TMSL telles que Create, Alter et suppriment. Consultez [commandes dans Tabular Model Scripting Language &#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-commands/tmsl-reference-commands.md) pour obtenir la liste de commandes.  
  
## <a name="main-objects"></a>Objets principales  
 Le tableau suivant est la liste des objets couramment utilisés dans un script TMSL.  
  
|||  
|-|-|  
|[Objet de base de données &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/database-object-tmsl.md)|Définit une base de données tabulaire au niveau de compatibilité 1200 ou supérieur, basé sur un modèle du même niveau.|  
|[Objet de modèle &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/model-object-tmsl.md)|Définit un modèle tabulaire au niveau de compatibilité 1200 ou supérieur.|  
|[Sources de données objet &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)|Définit une connexion à une source de données utilisée lors de l’importation pour charger le modèle, ou pour passer des requêtes lorsque le modèle est en mode DirectQuery.|  
|[Objet tables &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)|Spécifie les tables du modèle.|  
|[Objet de partitions &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/partitions-object-tmsl.md)|Définit le stockage d’ensembles de lignes de table, y compris les tables calculées.|  
|[Relationships, objet &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md)|Définit les relations entre tables.|  
|[Objet rôles &#40;TMSL&#41;](../../analysis-services/tabular-models-scripting-language-objects/roles-object-tmsl.md)|Définit les autorisations, les membres et les filtres de sécurité qui contrôlent l’accès aux données et aux opérations.|  
  
## <a name="see-also"></a>Voir aussi  
 [Tabular Model Scripting Language &#40;TMSL&#41; Reference (Informations de référence sur TMSL &#40;Tabular Model Scripting Language&#41;)](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)  
  
  

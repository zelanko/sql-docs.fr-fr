---
title: Boîte de dialogue Paramètres d’algorithme (vue modèles d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.models.algorithmparameters.f1
helpviewer_keywords:
- Algorithm Parameters dialog box
ms.assetid: 57f9f6f8-8ca4-4a6e-8f18-85f0571b7060
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c72a3c52da21ca7af10103010500bb43fd46a10a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66062611"
---
# <a name="algorithm-parameters-dialog-box-mining-models-view"></a>Boîte de dialogue Paramètres d'algorithme (Vue Modèles d'exploration de données)
  Utilisez la boîte de dialogue **Paramètres d’algorithme** pour ajuster les paramètres d’algorithme spécifiques du modèle sélectionné. Lorsque vous modifiez un paramètre d'algorithme, vous modifiez habituellement les résultats du modèle d'exploration de données. L'influence de chaque paramètre sur les résultats dépend de l'algorithme que vous utilisez et de vos données. Pour plus d’informations, consultez [Personnaliser les modèles et les structures d’exploration de données](data-mining/customize-mining-models-and-structure.md).  
  
## <a name="options"></a>Options  
 **Paramètres**  
 Affiche la liste des paramètres disponibles pour le modèle d'exploration de données sélectionné.  
  
 La liste suivante décrit les colonnes disponibles.  
  
|Colonne|Description|  
|------------|-----------------|  
|**Paramètre**|Liste le nom du paramètre.|  
|**Valeur**|Vous ne devez entrer une valeur que si vous souhaitez remplacer la valeur par défaut du paramètre.|  
|**Valeurs**|Donne la valeur par défaut du paramètre, qui sera utilisée par l’algorithme si vous n’entrez pas de valeur dans la colonne **Valeur**.|  
|**Plage**|Répertorie l’intervalle des valeurs possibles que vous pouvez entrer dans la colonne **Valeur**. Les plages peuvent être l’une des suivantes :<br /><br /> Liste discrète, telle que 1, 2, 3<br /><br /> Une plage inclusive, telle que [0, 100]<br /><br /> Plage exclusive, telle que (0,...)<br /><br /> Une combinaison, telle que [0,...)|  
  
 **Description**  
 Décrit le paramètre sélectionné dans la liste **Paramètres**.  
  
 **Ajouter**  
 Cliquez sur cet élément pour ajouter à la liste des paramètres supplémentaires spécifiques de l'algorithme. Après avoir ajouté le paramètre, vous pouvez entrer le nom correct dans la colonne **Paramètre** et donner une valeur dans la colonne **Valeur**.  
  
 **Remove**  
 Cliquez sur cet élément pour supprimer un paramètre personnalisé de la liste.  
  
 Si vous supprimez l'un des paramètres d'algorithme Analysis Services standard de la liste, le paramètre continue d'être utilisé dans le modèle, mais avec ses valeurs par défaut. Le paramètre n'est pas supprimé définitivement et apparaîtra la prochaine fois que vous ouvrirez la boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithmes d’exploration de données &#40;Analysis Services d’exploration de données&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Vue modèles d’exploration de données &#40;le concepteur de modèle d’exploration de données&#41;](mining-models-view-data-mining-model-designer.md)   
 [Déplacement d'objets d'exploration de données](data-mining/moving-data-mining-objects.md)  
  
  

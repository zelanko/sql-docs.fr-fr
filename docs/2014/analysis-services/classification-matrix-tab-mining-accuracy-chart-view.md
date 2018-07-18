---
title: Onglet matrice de classification (vue graphique d’analyse de précision d’exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.confusionmatrix.f1
ms.assetid: 85d5a047-d656-41e0-8a31-400271c2a620
caps.latest.revision: 22
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 58df3c6d14edb8bfddbd53db0c110475d2a983bd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37251511"
---
# <a name="classification-matrix-tab-mining-accuracy-chart-view"></a>Onglet Matrice de classification (vue Graphique d'analyse de précision de l'exploration de données)
  L’onglet **Matrice de classification** affiche une matrice de classification pour chaque modèle sélectionné dans la grille des modèles de l’onglet **Mappage de colonne** . La matrice de classification est disponible uniquement si la colonne prédictible sélectionnée sous l’onglet **Mappage de colonne** n’est pas continue. Pour une description plus détaillée de l’onglet **Matrice de classification** , consultez [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md).  
  
## <a name="options"></a>Options  
 **Copier**  
 Copie le contenu de chaque matrice de classification dans le Presse-papiers.  
  
 **Nombre pour \<modèle > sur \< colonne prédictible >**  
 Affiche une matrice de classification pour chaque modèle d'exploration de données de la structure d'exploration de données. La matrice contient les colonnes suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Prédit**|Contient une ligne pour chaque état de la colonne prédictible.|  
|**\<États > (réel)**|Colonne pour chaque état de la colonne prédictible. Si l'état de la ligne et de la colonne correspond, la cellule représente le nombre réel de fois où l'état existe dans la base de données. S'il ne correspond pas, la cellule représente l'erreur de la prévision.|  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteur graphique d’analyse de précision d’exploration de données &#40;exploration de données&#41;](mining-accuracy-chart-designer-data-mining.md)   
 [Test et des tâches de Validation et des procédures &#40;exploration de données&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Test et Validation &#40;exploration de données&#41;](data-mining/testing-and-validation-data-mining.md)  
  
  

---
title: Exclure une colonne d’un modèle d’exploration de données | Documents Microsoft
ms.custom: ''
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 937a28d77b8398855773cb1c11799de6112a04fa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="exclude-a-column-from-a-mining-model"></a>Exclure une colonne d'un modèle d'exploration de données
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Lorsque vous créez un modèle d'exploration de données, vous pouvez décider de ne pas utiliser toutes les colonnes qui existent dans la structure d'exploration de données sur laquelle le modèle repose. Par exemple, vous pouvez avoir ajouté une colonne relative aux noms des clients pour l'extraction, mais vous ne souhaitez pas l'utiliser pour la modélisation. Ou, vous pouvez décider de créer plusieurs copies d'une colonne avec différentes discrétisations, et utiliser uniquement une des copies dans chaque modèle, et ignorer les autres. Vous pouvez également ajouter de manière sélective des colonnes d'entrée dans différents modèles pour voir de quelle façon la variable ajoutée affecte la colonne de sortie.  
  
 Vous n'avez pas besoin de créer une nouvelle structure d'exploration de données pour chaque combinaison de colonnes ; à la place, vous pouvez simplement marquer une colonne comme n'étant pas utilisée dans un modèle particulier.  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a>Pour exclure une colonne d'un modèle d'exploration de données  
  
1.  Sous l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], sélectionnez la cellule qui correspond à la colonne à exclure sous le modèle d’exploration de données approprié.  
  
2.  Sélectionnez **Ignorer** dans la zone de liste déroulante.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches liées aux modèles d’exploration de données et procédures](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  

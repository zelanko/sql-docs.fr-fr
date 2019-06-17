---
title: Exclure une colonne d’un modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 70049092909b625a1f304f16f153bf4287d5bcdf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66084561"
---
# <a name="exclude-a-column-from-a-mining-model"></a>Exclure une colonne d'un modèle d'exploration de données
  Lorsque vous créez un modèle d'exploration de données, vous pouvez décider de ne pas utiliser toutes les colonnes qui existent dans la structure d'exploration de données sur laquelle le modèle repose. Par exemple, vous avez peut-être ajouté une colonne de nom de client pour l’extraction, mais ne souhaitez pas utiliser pour la modélisation. Ou, vous pouvez décider de créer plusieurs copies d'une colonne avec différentes discrétisations, et utiliser uniquement une des copies dans chaque modèle, et ignorer les autres. Vous pouvez également ajouter de manière sélective des colonnes d'entrée dans différents modèles pour voir de quelle façon la variable ajoutée affecte la colonne de sortie.  
  
 Vous n'avez pas besoin de créer une nouvelle structure d'exploration de données pour chaque combinaison de colonnes ; à la place, vous pouvez simplement marquer une colonne comme n'étant pas utilisée dans un modèle particulier.  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a>Pour exclure une colonne d'un modèle d'exploration de données  
  
1.  Sous l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], sélectionnez la cellule qui correspond à la colonne à exclure sous le modèle d’exploration de données approprié.  
  
2.  Sélectionnez **Ignorer** dans la zone de liste déroulante.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et procédures des modèles d’exploration de données](mining-model-tasks-and-how-tos.md)  
  
  

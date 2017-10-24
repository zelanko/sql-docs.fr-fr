---
title: "Exclure une colonne d’un modèle d’exploration de données | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- excluding mining model columns
- mining models [Analysis Services], columns
- columns [data mining], excluding
ms.assetid: 404fe5fe-3ba2-4b9b-8780-0d02343d467f
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a12584791ec8ea21a1338c09dbc0e5f7ef8f7a62
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="exclude-a-column-from-a-mining-model"></a>Exclure une colonne d'un modèle d'exploration de données
  Lorsque vous créez un modèle d'exploration de données, vous pouvez décider de ne pas utiliser toutes les colonnes qui existent dans la structure d'exploration de données sur laquelle le modèle repose. Par exemple, vous pouvez avoir ajouté une colonne relative aux noms des clients pour l'extraction, mais vous ne souhaitez pas l'utiliser pour la modélisation. Ou, vous pouvez décider de créer plusieurs copies d'une colonne avec différentes discrétisations, et utiliser uniquement une des copies dans chaque modèle, et ignorer les autres. Vous pouvez également ajouter de manière sélective des colonnes d'entrée dans différents modèles pour voir de quelle façon la variable ajoutée affecte la colonne de sortie.  
  
 Vous n'avez pas besoin de créer une nouvelle structure d'exploration de données pour chaque combinaison de colonnes ; à la place, vous pouvez simplement marquer une colonne comme n'étant pas utilisée dans un modèle particulier.  
  
### <a name="to-exclude-a-column-from-a-mining-model"></a>Pour exclure une colonne d'un modèle d'exploration de données  
  
1.  Sous l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], sélectionnez la cellule qui correspond à la colonne à exclure sous le modèle d’exploration de données approprié.  
  
2.  Sélectionnez **Ignorer** dans la zone de liste déroulante.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches du modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)  
  
  


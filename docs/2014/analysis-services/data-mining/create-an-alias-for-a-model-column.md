---
title: Créer un Alias pour une colonne de modèle | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data mining [Analysis Services], how-to topics
- mining models [Analysis Services], columns
- column names [Analysis Services]
ms.assetid: c80ebe66-a8f8-4f24-9fe8-8288de9d13bc
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cf049cdd7fabbc50fdacf5ab72ca3ce1845482f7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051390"
---
# <a name="create-an-alias-for-a-model-column"></a>Créer un alias pour une colonne du modèle
  Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez créer un alias pour une colonne du modèle. Cela peut se révéler utile lorsque le nom de la structure d'exploration de données est trop long pour l'utiliser aisément, ou lorsque vous souhaitez renommer la colonne pour que son contenu ou son utilisation dans le modèle soient mieux décrits. Par exemple, si vous faites une copie d'une colonne de structure, puis que vous discrétisez la colonne différemment pour un modèle particulier, vous pouvez renommer la colonne pour refléter le contenu de manière plus précise.  
  
 Pour créer un alias pour une colonne du modèle, utilisez le volet **Propriétés** et définissez la propriété [Name](../scripting/properties/name-element-assl.md) de la colonne.  
  
 Sous l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données, l’alias apparaît entre parenthèses à côté de l’étiquette d’utilisation de la colonne.  
  
 Pour plus d’informations sur la définition des propriétés d’un modèle d’exploration de données, consultez [Colonnes de modèle d’exploration de données](mining-model-columns.md).  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a>Pour ajouter un alias à une colonne du modèle d'exploration de données  
  
1.  Sous l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données, cliquez avec le bouton droit sur la cellule dans le modèle d’exploration de données de la colonne d’exploration de données à modifier, puis sélectionnez **Propriétés**.  
  
2.  Dans la fenêtre **Propriétés** située à droite de l’écran, cliquez sur la cellule à côté de la propriété Name et supprimez la valeur actuelle. Tapez un nouveau nom pour la colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches liées aux modèles d’exploration de données et procédures](mining-model-tasks-and-how-tos.md)   
 [Propriétés du modèle d’exploration de données](mining-model-properties.md)  
  
  
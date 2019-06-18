---
title: Créer un Alias pour une colonne de modèle | Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e051c454223fc7fc710f45b97a1a76ecceb10f2b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62740221"
---
# <a name="create-an-alias-for-a-model-column"></a>Créer un alias pour une colonne du modèle
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous pouvez créer un alias pour une colonne du modèle. Cela peut se révéler utile lorsque le nom de la structure d'exploration de données est trop long pour l'utiliser aisément, ou lorsque vous souhaitez renommer la colonne pour que son contenu ou son utilisation dans le modèle soient mieux décrits. Par exemple, si vous faites une copie d'une colonne de structure, puis que vous discrétisez la colonne différemment pour un modèle particulier, vous pouvez renommer la colonne pour refléter le contenu de manière plus précise.  
  
 Pour créer un alias pour une colonne du modèle, utilisez le volet **Propriétés** et définissez la propriété [Name](https://docs.microsoft.com/bi-reference/assl/properties/name-element-assl) de la colonne.  
  
 Sous l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données, l’alias apparaît entre parenthèses à côté de l’étiquette d’utilisation de la colonne.  
  
 Pour plus d’informations sur la définition des propriétés d’un modèle d’exploration de données, consultez [Colonnes de modèle d’exploration de données](../../analysis-services/data-mining/mining-model-columns.md).  
  
### <a name="to-add-an-alias-to-a-mining-model-column"></a>Pour ajouter un alias à une colonne du modèle d'exploration de données  
  
1.  Sous l’onglet **Modèles d’exploration de données** du Concepteur d’exploration de données, cliquez avec le bouton droit sur la cellule dans le modèle d’exploration de données de la colonne d’exploration de données à modifier, puis sélectionnez **Propriétés**.  
  
2.  Dans la fenêtre **Propriétés** située à droite de l’écran, cliquez sur la cellule à côté de la propriété Name et supprimez la valeur actuelle. Tapez un nouveau nom pour la colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches du modèle d'exploration de données et procédures](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Propriétés du modèle d'exploration de données](../../analysis-services/data-mining/mining-model-properties.md)  
  
  

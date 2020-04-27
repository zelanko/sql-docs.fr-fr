---
title: Faire une copie d’un modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], copying
- mining models [Analysis Services], creating
- mining models [Analysis Services], how-to topics
- copying mining models
ms.assetid: 7975bb02-f188-49a0-b7de-5b9b216254ad
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7464c7d780a420b0f95b59ebde02494bd40661e6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66084220"
---
# <a name="make-a-copy-of-a-mining-model"></a>Créer une copie d'un modèle d'exploration de données
  La création d'une copie d'un modèle d'exploration de données est utile lorsque vous souhaitez créer rapidement plusieurs modèles d'exploration de données basés sur les mêmes données. Après avoir copié le modèle, vous pouvez ensuite changer la copie du modèle en modifiant des paramètres ou en ajoutant un filtre.  
  
 Par exemple, si vous avez une table de clients liée à une table d’achats, vous pouvez créer des copies pour générer des modèles d’exploration de données distincts pour chaque client en filtrant sur des informations démographiques, telles que des attributs d’âge ou de région.  
  
 Pour plus d’informations sur la copie du contenu du modèle (tel que la représentation graphique ou les schémas de modèles) dans le Presse-papiers pour une utilisation dans d’autres programmes, consultez [Copier une vue d’un modèle d’exploration de données](copy-a-view-of-a-mining-model.md).  
  
### <a name="to-create-a-related-mining-model"></a>Pour créer un modèle d'exploration de données connexe  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], dans l’Explorateur de solutions, cliquez sur la structure d’exploration de données qui contient le modèle d’exploration de données.  
  
2.  Cliquez sur l'onglet **Modèles d'exploration de données** .  
  
3.  Sélectionnez le modèle et cliquez avec le bouton droit pour ouvrir le menu contextuel.  
  
     -ou-  
  
     Sélectionnez le modèle. Dans le menu **Modèle d’exploration de données** , sélectionnez **Nouveau modèle d’exploration de données**.  
  
4.  Tapez un nom pour le nouveau modèle d'exploration de données et sélectionnez un algorithme. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-the-filter-on-the-copied-mining-model"></a>Pour modifier le filtre sur le modèle d'exploration de données copié  
  
1.  Sélectionnez le modèle d'exploration de données.  
  
2.  Dans la fenêtre **Propriétés** , cliquez sur la zone de texte correspondant à la propriété **filtre** , puis cliquez sur le bouton Générer **(...)** .  
  
3.  Modifiez les conditions de filtre.  
  
     Pour plus d’informations sur l’utilisation des boîtes de dialogue de l’éditeur de filtre, consultez [Appliquer un filtre à un modèle d’exploration de données](apply-a-filter-to-a-mining-model.md).  
  
4.  Dans la fenêtre **Propriétés** , dans la `AlgorithmParameters` zone de texte, cliquez sur **paramètres de définir**et modifiez les paramètres d’algorithme, si vous le souhaitez.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Filtres pour les modèles d’exploration de données &#40;Analysis Services d’exploration de données&#41;](mining-models-analysis-services-data-mining.md)   
 [Tâches du modèle d’exploration de données et procédures](mining-model-tasks-and-how-tos.md)   
 [Supprimer un filtre d'un modèle d'exploration de données](delete-a-filter-from-a-mining-model.md)  
  
  

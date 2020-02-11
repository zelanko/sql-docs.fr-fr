---
title: Copier une vue d’un modèle d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- clipboards [data mining]
- Mining Model Viewer [Analysis Services], clipboards
- copying mining models to clipboard
ms.assetid: 768372db-e5b4-4990-b459-03d854fd9a6d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 84abbb855673183910099f0a34d70702d34da7fd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66085600"
---
# <a name="copy-a-view-of-a-mining-model"></a>Copier une vue d'un modèle d'exploration de données
  L’onglet **Visionneuse de modèle d’exploration de données** du Concepteur d’exploration de données de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] utilise une visionneuse distincte pour chaque type de modèle d’exploration de données. Plusieurs des visionneuses ont des composants à partir desquels vous pouvez copier le contenu vers le Presse-papiers, puis coller le contenu dans un document ou un logiciel de manipulation d'image. Cette fonctionnalité est disponible avec les composants suivants :  
  
-   Diagramme de cluster dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] Cluster Viewer et la Visionneuse de l'algorithme MSC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster)  
  
-   Arbre de décision dans la Visionneuse d’arborescence [!INCLUDE[msCoName](../../includes/msconame-md.md)] et la Visionneuse de l’algorithme MTS ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series)  
  
-   Transitions d'état dans la Visionneuse de l'algorithme MSC ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Sequence Cluster)  
  
-   Réseau de dépendances dans la Visionneuse de l'algorithme MAR ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Association Rules), la Visionneuse de l'algorithme MNB ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Naive Bayes) et la Visionneuse d'arborescence [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
-   Contenu du modèle d’exploration de données à partir du volet Détails du nœud de la Visionneuse de l’arborescence de contenu générique [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
 Vous pouvez copier la représentation complète du modèle d'exploration de données ou simplement la partie visible dans la visionneuse.  
  
> [!WARNING]  
>  Lorsque vous copiez un modèle à l'aide de la visionneuse, il ne crée pas de nouvel objet de modèle. Pour créer un modèle, vous devez utiliser l'Assistant, ou le Concepteur d'exploration de données. Pour plus d’informations, consultez [Créer une copie d’un modèle d’exploration de données](make-a-copy-of-a-mining-model.md).  
  
### <a name="to-copy-the-complete-model-to-the-clipboard"></a>Pour copier le modèle complet dans le Presse-papiers  
  
1.  Dans la liste **Modèle d’exploration de données** sous l’onglet **Visionneuse de modèle d’exploration de données** , sélectionnez le modèle d’exploration de données à afficher.  
  
2.  Sélectionnez l’onglet approprié, tel que l’onglet **Réseau de dépendances** , puis cliquez sur **Copier le graphique entier** dans la barre d’outils de l’onglet.  
  
### <a name="to-copy-the-visible-piece-of-the-model-to-the-clipboard"></a>Pour copier la partie visible du modèle vers le Presse-papiers  
  
1.  Dans la liste **Modèle d’exploration de données** sous l’onglet **Visionneuse de modèle d’exploration de données** , sélectionnez le modèle d’exploration de données à afficher.  
  
2.  Sélectionnez l’onglet approprié, tel que l’onglet **Réseau de dépendances** , puis effectuez un zoom avant ou arrière sur le modèle au niveau approprié.  
  
3.  Cliquez sur **Copier la vue du graphique** dans la barre d’outils de l’onglet sélectionné.  
  
### <a name="to-copy-the-mining-model-content-to-the-clipboard"></a>Pour copier le contenu du modèle d'exploration de données dans le Presse-papiers  
  
1.  Dans la liste **Modèle d’exploration de données** sous l’onglet **Visionneuse de modèle d’exploration de données** , sélectionnez le modèle d’exploration de données à afficher.  
  
2.  Dans la liste déroulante **Visionneuse** , sélectionnez **Visionneuse de l’arborescence de contenu générique Microsoft**.  
  
3.  Dans le volet **Légende du nœud (ID unique)** , cliquez sur un nœud.  
  
4.  Cliquez avec le bouton droit sur le volet **Détails du nœud** , puis sélectionnez **Sélectionner tout**.  
  
5.  Cliquez de nouveau avec le bouton droit sur le volet **Détails du nœud** , puis sélectionnez **Copier**.  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches de la visionneuse de modèle d'exploration de données et procédures](mining-model-viewer-tasks-and-how-tos.md)  
  
  

---
title: Formes d’exploration de données pour Visio | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining shapes
- templates [Visio]
- Visio shapes
- shapes, data mining
ms.assetid: 11a821d9-1c0a-442e-b735-92208ce479dc
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6ebe206d4f4942e9a9456ba10b00d33514ef6212
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66086398"
---
# <a name="data-mining-shapes-for-visio"></a>Formes d'exploration de données pour Visio
  Les formes d'exploration de données pour Visio fournissent des modèles personnalisés pour l'affichage de modèles d'exploration de données. En utilisant ces modèles, vous pouvez vous connecter à un modèle que vous avez créé et créer des présentations interactives pour illustrer les résultats de l'exploration de données.  
  
 Les modèles offrent de nombreux avantages par rapport aux graphiques statiques et aux captures d’écran. ils interagissent avec les modèles d’exploration de données sous-jacents, qui sont stockés sur une instance de Analysis Services et vous permettent de personnaliser la façon dont les modèles dans le modèle d’exploration de données sont affichés. Réduisez et développez les niveaux d'un modèle d'arbre, filtrez sur les nœuds de données ou par les attributs, et affichez des statistiques du modèle telles que les probabilités et des coefficients.  
  
 ![DM](media/dm-stencil.gif "DM")  
  
 Les modèles Visio incluent ces Assistants :  
  
-   **Diagramme du réseau de dépendances :** Utilisez cet Assistant pour créer des graphiques pour les arbres de décision et les réseaux neuronaux.  
  
-   **Diagramme de l’arbre de décision :** Utilisez cet Assistant pour créer des diagrammes qui montrent les points de décision et les formules associés aux modèles d’arbre de décision. Ce diagramme peut également être utilisé avec des modèles de régression.  
  
-   **Diagramme du cluster :** Utilisez cet Assistant pour créer des graphiques colorés pour vos modèles de segmentation. Activez/désactivez les vues, telles que la discrimination d'attribut, les profils de cluster et les dépendances, et personnalisez l'apparence des clusters.  
  
## <a name="installation"></a>Installation  
 Lorsque vous installez les modèles d’exploration de données pour Visio, par défaut, les fichiers suivants \<sont installés dans le lecteur> \program Files\Microsoft SQL Server 2012 DM Add \<-ins (ou lecteur> \ ou Program Files (x86) \Microsoft SQL Server 2012 DM Add-ins) :  
  
-   **Exploration de données Microsoft. VST** Ce modèle contient des assistants de mise en forme et de mise en page prédéfinis pour vous aider à utiliser les formes d’exploration de données.  
  
-   **Microsoft Data Mining Shape Studio. VSS** Ce fichier de gabarit contient des formes associées au modèle.  
  
## <a name="how-to-use-the-templates"></a>Comment utiliser les modèles  
 Pour ouvrir les modèles, double-cliquez sur le fichier de forme, ou ouvrez Visio, puis ouvrez le modèle de forme.  
  
1.  Faites glisser l'une des formes d'exploration de données Visio du gabarit vers une nouvelle page.  
  
2.  Lorsque l'Assistant démarre, connectez-vous au serveur qui contient le modèle d'exploration de données que vous souhaitez afficher.  
  
3.  Sélectionnez le modèle d'exploration de données, qui fait correspondre le type de modèle au type de visualisation.  
  
4.  Définissez les options d'affichage et de mise en forme des données.  
  
5.  Une fois que vous avez terminé l' **Assistant Création de formes d’exploration de données**, vous disposez d’un diagramme que vous pouvez modifier et améliorer à l’aide des fonctionnalités de Visio.  
  
 Pour plus d’informations sur l’utilisation et l’amélioration des diagrammes de modèle Visio, consultez [affichage des modèles d’exploration de données dans Visio &#40;compléments d’exploration de données&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md)  
  
## <a name="requirements"></a>Conditions requises  
  
-   Pour utiliser les modèles, vous devez d'abord créer une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
     L'Assistant vous invite à sélectionner un serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et à spécifier la base de données qui contient le modèle d'exploration de données.  
  
     Pour plus d’informations sur la création d’une connexion, consultez [se connecter à des données sources &#40;client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
-   Si vous utilisez les outils d’analyse de table, assurez-vous d’enregistrer vos modèles [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] sur le serveur et n’utilisez pas de modèles temporaires.  
  
-   Le modèle doit avoir été créé avec un des algorithmes pris en charge : clustering, arbres de décision, réseaux neuronaux, Naïve Bayes ou régression logistique.  
  
  

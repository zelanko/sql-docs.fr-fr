---
title: Formes d’exploration de données pour Visio | Documents Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data mining shapes
- templates [Visio]
- Visio shapes
- shapes, data mining
ms.assetid: 11a821d9-1c0a-442e-b735-92208ce479dc
caps.latest.revision: 16
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cd037e0d4eefb7f894d956222219902a5082fffd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040983"
---
# <a name="data-mining-shapes-for-visio"></a>Formes d'exploration de données pour Visio
  Les formes d'exploration de données pour Visio fournissent des modèles personnalisés pour l'affichage de modèles d'exploration de données. En utilisant ces modèles, vous pouvez vous connecter à un modèle que vous avez créé et créer des présentations interactives pour illustrer les résultats de l'exploration de données.  
  
 Les modèles offrent de nombreux avantages par rapport aux graphiques statiques et aux captures d'écran. Ils interagissent avec les modèles d'exploration de données sous-jacents, stockés sur une instance d'Analysis Services, et vous laissent personnaliser la manière dont les modèles s'affichent dans le modèle d'exploration de données. Réduisez et développez les niveaux d'un modèle d'arbre, filtrez sur les nœuds de données ou par les attributs, et affichez des statistiques du modèle telles que les probabilités et des coefficients.  
  
 ![DM](media/dm-stencil.gif "DM")  
  
 Les modèles Visio incluent ces Assistants :  
  
-   **Diagramme réseau de dépendances :** cet Assistant permet de créer des graphiques pour les arbres de décision et les réseaux neuronaux.  
  
-   **Diagramme d’arbre de décision :** cet Assistant permet de créer des diagrammes qui affichent les points de décision et les formules associées aux modèles d’arbre de décision. Ce diagramme peut également être utilisé avec des modèles de régression.  
  
-   **Diagramme de cluster :** cet Assistant permet de créer des graphiques colorés pour vos modèles de segmentation. Activez/désactivez les vues, telles que la discrimination d'attribut, les profils de cluster et les dépendances, et personnalisez l'apparence des clusters.  
  
## <a name="installation"></a>Installation  
 Lorsque vous installez les modèles d’exploration de données pour Visio, par défaut, les fichiers suivants sont installés pour \<lecteur > \Program Files\Microsoft SQL Server 2012 DM Add-Ins (ou \<lecteur > \ ou Program Files (x86) \Microsoft SQL Server 2012 DM Add-Ins) :  
  
-   **Mining.vst de données Microsoft** ce modèle contient prédéfinies de mise en forme, disposition et les Assistants pour vous aider à travailler avec les formes d’exploration de données.  
  
-   **Microsoft Data Mining Shape Studio.vss** ce fichier de gabarit contient des formes associées au modèle.  
  
## <a name="how-to-use-the-templates"></a>Comment utiliser les modèles  
 Pour ouvrir les modèles, double-cliquez sur le fichier de forme, ou ouvrez Visio, puis ouvrez le modèle de forme.  
  
1.  Faites glisser l'une des formes d'exploration de données Visio du gabarit vers une nouvelle page.  
  
2.  Lorsque l'Assistant démarre, connectez-vous au serveur qui contient le modèle d'exploration de données que vous souhaitez afficher.  
  
3.  Sélectionnez le modèle d'exploration de données, qui fait correspondre le type de modèle au type de visualisation.  
  
4.  Définissez les options d'affichage et de mise en forme des données.  
  
5.  Après avoir terminé la **Assistant Création de forme d’exploration de données**, vous disposez d’un diagramme que vous pouvez modifier et améliorer les fonctionnalités de Visio.  
  
 Pour plus d’informations sur l’utilisation et l’amélioration des diagrammes de modèle Visio, consultez [affichage des modèles d’exploration de données dans Visio &#40;des compléments d’exploration de données&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md)  
  
## <a name="requirements"></a>Spécifications  
  
-   Pour utiliser les modèles, vous devez d'abord créer une connexion à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
     L'Assistant vous invite à sélectionner un serveur [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] et à spécifier la base de données qui contient le modèle d'exploration de données.  
  
     Pour plus d’informations sur la création d’une connexion, consultez [se connecter à la Source de données &#40;Client d’exploration de données pour Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
-   Si vous utilisez les outils d’analyse de Table, assurez-vous que vous enregistrez vos modèles sur le [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server et n’utilisent pas les modèles temporaires.  
  
-   Le modèle doit avoir été créé avec un des algorithmes pris en charge : clustering, arbres de décision, réseaux neuronaux, Naïve Bayes ou régression logistique.  
  
  
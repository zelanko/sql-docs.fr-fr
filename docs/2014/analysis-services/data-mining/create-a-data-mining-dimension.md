---
title: Créer une Dimension d’exploration de données | Documents Microsoft
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
- mining structures [Analysis Services], dimensions
ms.assetid: 9f0c39e5-3516-43ab-b203-f3f6dbcff89a
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: dc8b573a43b8e416164a4e100aa7610ba6021716
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139501"
---
# <a name="create-a-data-mining-dimension"></a>Créer une dimension d'exploration de données
  Si la structure d'exploration de données repose sur un cube OLAP, vous pouvez créer une dimension qui contient le contenu du modèle d'exploration de données, puis réintégrer la dimension dans le cube source.  
  
 Vous pouvez également parcourir la dimension, l'utiliser pour explorer les résultats du modèle ou interroger la dimension à l'aide de MDX.  
  
### <a name="to-create-a-data-mining-dimension"></a>Pour créer une dimension d'exploration de données  
  
1.  Dans le Concepteur d’exploration de données de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], sélectionnez l’onglet **Structure d’exploration de données** ou l’onglet **Modèles d’exploration de données** .  
  
2.  Dans le menu **Modèle d’exploration de données** , sélectionnez **Créer une dimension d’exploration de données**.  
  
     La boîte de dialogue **Créer une dimension d’exploration de données** s’ouvre.  
  
3.  Dans la liste **Nom du modèle** de la boîte de dialogue **Créer une dimension d’exploration de données** , sélectionnez un modèle d’exploration de données OLAP.  
  
4.  Dans la zone **Nom de la dimension** , entrez le nom de la nouvelle dimension d’exploration de données.  
  
5.  Si vous voulez créer un cube contenant cette nouvelle dimension, sélectionnez **Créer un cube**. Après avoir sélectionné **Créer un cube**, vous pouvez entrer le nom du nouveau cube.  
  
6.  Cliquez sur **OK**.  
  
     La dimension d’exploration de données est créée et ajoutée au dossier **Dimensions** dans l’Explorateur de solutions. Si vous avez sélectionné **Créer un cube**, un cube est créé et ajouté au dossier **Cubes** .  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches et procédures relatives aux structures d’exploration de données](mining-structure-tasks-and-how-tos.md)  
  
  
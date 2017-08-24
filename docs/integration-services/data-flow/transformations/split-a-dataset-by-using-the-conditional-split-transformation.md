---
title: "Fractionner un jeu de données à l’aide de la Transformation de fractionnement conditionnel | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Conditional Split transformation
- splitting dataset
- datasets [Integration Services], splitting
ms.assetid: 23b3e84f-9296-4dc9-81c0-c7f06ae3f1ff
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 8248e068541c6bd72b21f78d121811f4851850bb
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="split-a-dataset-by-using-the-conditional-split-transformation"></a>Fractionner un dataset à l'aide de la transformation de fractionnement conditionnel
  Pour pouvoir ajouter et configurer une transformation de fractionnement conditionnel, le package doit inclure au moins une tâche de flux de données et une source.  
  
### <a name="to-conditionally-split-a-dataset"></a>Pour fractionner un dataset de manière conditionnelle  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de données** puis, dans la **Boîte à outils**, faites glisser la transformation de fractionnement conditionnel sur l’aire de conception.  
  
4.  Connectez la transformation de fractionnement conditionnel au flux de données en faisant glisser le connecteur à partir de la source de données ou de la transformation précédente vers la transformation de fractionnement conditionnel.  
  
5.  Double-cliquez sur la transformation de fractionnement conditionnel.  
  
6.  Dans **l’Éditeur de transformation de fractionnement conditionnel**, générez les expressions à utiliser comme conditions en faisant glisser des variables, des colonnes, des fonctions et des opérateurs dans la colonne **Condition** de la grille. Vous pouvez également taper l’expression dans la colonne **Condition** .  
  
    > [!NOTE]  
    >  Une variable ou une colonne peut être utilisée dans plusieurs expressions.  
  
    > [!NOTE]  
    >  Si l'expression n'est pas valide, son texte est mis en surbrillance et une info-bulle dans la colonne décrit les erreurs.  
  
7.  Si vous le souhaitez, modifiez les valeurs de la colonne **Nom de la sortie** . Les noms par défaut sont Case 1, Case 2, etc.  
  
8.  Pour modifier la séquence dans laquelle les conditions sont évaluées, cliquez sur les flèches haut ou bas.  
  
    > [!NOTE]  
    >  Placez les conditions qui ont le plus de chances d'être rencontrées en haut de la liste.  
  
9. Si vous le souhaitez, modifiez le nom de la sortie par défaut des lignes de données qui ne correspondent à aucune condition.  
  
10. Pour configurer l’affichage des erreurs, cliquez sur **Configurer l’affichage des erreurs**. Pour plus d’informations, consultez [Débogage d’un flux de données](../../../integration-services/troubleshooting/debugging-data-flow.md).  
  
11. Cliquez sur **OK**.  
  
12. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Transformation de fractionnement conditionnel](../../../integration-services/data-flow/transformations/conditional-split-transformation.md)   
 [Transformations Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Chemins d’accès d’Integration Services](../../../integration-services/data-flow/integration-services-paths.md)   
 [Types de données Integration Services](../../../integration-services/data-flow/integration-services-data-types.md)   
 [Tâche de flux de données](../../../integration-services/control-flow/data-flow-task.md)   
 [Integration Services &#40; SSIS &#41; Expressions](../../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  

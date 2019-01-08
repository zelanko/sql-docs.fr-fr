---
title: Fractionner un dataset à l’aide de la transformation de fractionnement conditionnel | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Conditional Split transformation
- splitting dataset
- datasets [Integration Services], splitting
ms.assetid: 23b3e84f-9296-4dc9-81c0-c7f06ae3f1ff
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: fcce6d78b8a5193f944cd4287d612002c59196da
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52785061"
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
  
10. Pour configurer l’affichage des erreurs, cliquez sur **Configurer l’affichage des erreurs**. Pour plus d’informations, consultez [Configurer une sortie d’erreur dans un composant de flux de données](../../configure-an-error-output-in-a-data-flow-component.md).  
  
11. Cliquez sur **OK**.  
  
12. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Conditional Split Transformation](conditional-split-transformation.md)   
 [Transformations Integration Services](integration-services-transformations.md)   
 [Chemins Integration Services](../integration-services-paths.md)   
 [Types de données d’Integration Services](../integration-services-data-types.md)   
 [tâche de flux de données](../../control-flow/data-flow-task.md)   
 [Expressions Integration Services &#40;SSIS&#41;](../../expressions/integration-services-ssis-expressions.md)  
  
  

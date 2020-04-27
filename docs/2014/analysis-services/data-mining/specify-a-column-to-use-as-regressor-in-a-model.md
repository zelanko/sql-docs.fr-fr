---
title: Spécifier une colonne à utiliser comme régreseur dans un modèle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d8e0cb8e-302a-4166-9ed0-e2d9e2919b0a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cf035895142ae48cb59f6256e7249710d9709b92
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66082910"
---
# <a name="specify-a-column-to-use-as-regressor-in-a-model"></a>Spécifier une colonne à utiliser comme régresseur dans un modèle
  Un modèle de régression linéaire représente la valeur de l'attribut prévisible résultant d'une formule qui combine les entrées de telle façon que les données sont ajustées le mieux possible à une ligne de régression estimée. L'algorithme accepte uniquement les valeurs numériques comme entrées, et détecte automatiquement les entrées qui sont le mieux adaptées.  
  
 Vous pouvez toutefois spécifier qu'une colonne soit incluse en tant que régresseur en ajoutant le paramètre FORCE_REGRESSOR au modèle et en spécifiant les régresseurs à utiliser. Ce peut être le cas lorsque l'attribut a une signification même si l'effet est trop limité pour être détecté par le modèle, ou lorsque vous voulez vous assurer que l'attribut est inclus dans la formule.  
  
 La procédure suivante explique comment créer un modèle de régression linéaire simple, en utilisant le même exemple de données que celui utilisé pour le [didacticiel sur les réseaux neuronaux](../../tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md). Le modèle n'est pas nécessairement fiable, mais il montre comment utiliser le Concepteur d'exploration de données pour personnaliser un modèle de régression linéaire.  
  
### <a name="how-to-create-a-simple-linear-regression-model"></a>Procédure de création d'un modèle de régression linéaire simple  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], dans l’ **Explorateur de solutions**, développez **Structures d’exploration de données**.  
  
2.  Double-cliquez sur Call Center.dmm pour l'ouvrir dans le concepteur.  
  
3.  Dans le menu **Modèle d’exploration de données** , sélectionnez **Nouveau modèle d’exploration de données**.  
  
4.  Pour l’algorithme, sélectionnez **MLR (Microsoft Linear Regression)**. Pour le nom, tapez **Call Center Regression**.  
  
5.  Sous l’onglet **Modèles d’exploration de données** , modifiez l’utilisation des colonnes de la façon suivante. La valeur **Ignorer**doit être affectée à toutes les colonnes ne figurant pas dans la liste suivante, si ce n’est pas déjà fait.  
  
     FactCallCenterID**Key**  
  
     ServiceGrade**PredictOnly**  
  
     Total Operators**Input**  
  
     AverageTimePerIssue**Input**  
  
6.  Dans le menu **Modèle d’exploration de données** , sélectionnez **Définir les paramètres du modèle**.  
  
7.  Pour le paramètre FORCE_REGRESSOR, dans la colonne **Valeur** , tapez les noms de colonnes entre crochets et séparés par une virgule, comme suit :  
  
    ```  
    [Average Time Per Issue],[Total Operators]  
    ```  
  
    > [!NOTE]  
    >  L'algorithme détectera automatiquement les colonnes qui constituent les meilleurs régresseurs. Vous devez uniquement forcer l'utilisation des régresseurs lorsque vous voulez vous assurer qu'une colonne est incluse dans la formule finale.  
  
8.  Dans le menu **Modèle d’exploration de données** , sélectionnez **Traiter le modèle**.  
  
     Dans la visionneuse, le modèle est représenté sous la forme d'un nœud unique contenant la formule de régression. Vous pouvez afficher la formule dans la **Légende d’exploration de données**, ou extraire les coefficients de la formule à l’aide de requêtes.  
  
## <a name="see-also"></a>Voir aussi  
 [Algorithme de régression linéaire Microsoft](microsoft-linear-regression-algorithm.md)   
 [Requêtes d’exploration de données](data-mining-queries.md)   
 [Référence technique de l’algorithme de régression linéaire Microsoft](microsoft-linear-regression-algorithm-technical-reference.md)   
 [Contenu du modèle d’exploration de données pour les modèles de régression linéaire &#40;Analysis Services – Exploration de données&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)  
  
  

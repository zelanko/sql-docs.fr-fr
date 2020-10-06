---
description: Fonctions (DMX)
title: Fonctions (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 4b8e5d887195e27f706ef995ff92e32aa41b9149
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91726188"
---
# <a name="functions-dmx"></a>Fonctions (DMX)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Lorsque vous utilisez DMX (Data Mining Extensions) pour interroger des objets dans [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , vous pouvez utiliser des fonctions pour retourner plus d’informations que les valeurs des colonnes du modèle d’exploration de données ou du jeu de données d’entrée. Les requêtes DMX permettent de retourner, par exemple, non seulement la valeur de prévision d'une colonne, mais également la probabilité que la prévision est correcte. Outre les fonctions DMX, vous pouvez également utiliser les fonctions de Microsoft Visual Basic for Applications (VBA), Microsoft Excel et les procédures stockées.  
  
## <a name="dmx-functions"></a>Fonctions DMX  
 Les fonctions DMX permettent d'exécuter les tâches suivantes :  
  
-   Retourner des prévisions  
  
-   Retourner des statistiques sur une prévision, telles que la probabilité et la prise en charge.  
  
-   Filtrer les résultats de la requête.  
  
-   Réorganiser une expression de table.  
  
 Les plupart des fonctions DMX retournent une valeur scalaire, comme la prise en charge d'une prévision, mais certaines retournent un résultat tabulaire. Par exemple, la fonction PredictHistogram retourne une table qui contient la prise en charge et la probabilité pour chaque État de la colonne prévisible spécifiée. Les résultats sont affichés dans une nouvelle colonne tabulaire.  
  
 **Pour plus d’informations : fonctions de** [prédiction générales &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md), informations de référence sur la [fonction dmx&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)  
  
## <a name="visual-basic-for-applications-vba-and-excel-functions"></a>Fonctions Visual Basic for Applications (VBA) et Excel  
 Outre les fonctions DMX, il est également possible d'appeler un grand nombre de fonctions VBA et Excel à l'aide des instructions DMX. Par exemple, vous pouvez utiliser la fonction lCase pour modifier le mode d’affichage de la colonne Attribute_Name dans le contenu du modèle TM_Decision_Tree. Cela est illustré par l'exemple de code suivant.  
  
```  
SELECT lCase([Attribute_Name])   
FROM [TM_Decision_Tree].CONTENT  
```  
  
 Si la même fonction existe dans VBA et Excel, vous devez préfixer le nom de la fonction dans votre instruction DMX avec **VBA** ou **Excel**. Par exemple, imaginez que vous utilisiez `VBA!Log` ou `Excel!Log`. Si la fonction VBA ou Excel que vous souhaitez utiliser existe également dans le langage DMX ou MDX (Multidimensional Expressions), ou si elle contient le caractère dollar ($), vous devez utiliser des crochets ([]) pour l'isoler. Dans ce cas, l'appel de fonction sera `[VBA!Format]`.  
  
## <a name="stored-procedures"></a>Procédures stockées  
 Vous pouvez utiliser les langages de programmation clr (common langage runtime) pour créer des procédures stockées qui étendent les fonctionnalités de DMX. Par exemple, un modèle d’exploration de données d’arbre de régression retourne des coefficients, tels que A, B, etc., qui décrivent l’équation de régression, mais le modèle ne retourne pas l’équation elle-même, telle que + BX = y. Cependant, vous pouvez écrire une procédure stockée qui utilise l'objet de modèle d'exploration de données pour naviguer dans le schéma de contenu, et pour retourner l'équation de régression en tant que résultat. Une instruction DMX peut donc retourner la liste des équations de régression en tant que résultats de requête.  
  
 **Pour plus d’informations : gestion des assemblys de** [modèles multidimensionnels](/analysis-services/multidimensional-models/multidimensional-model-assemblies-management)  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-reference.md)   
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;les éléments de la syntaxe DMX&#41;](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX ](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  

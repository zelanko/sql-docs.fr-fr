---
title: Créer le jeu de test (Assistant exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.holdout.f1
ms.assetid: d0a44b59-ffbd-45fc-baa8-6b8046b1a2f5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fb970a24faf35b269af2c9972e4d604be57d0f88
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096349"
---
# <a name="create-testing-set-data-mining-wizard"></a>Créer un jeu de test (Assistant Exploration de données)
  Utilisez la page **Créer un jeu de test** pour spécifier la quantité des données à utiliser pour l’apprentissage et celle à réserver au jeu de test. La séparation des données dans un jeu d'apprentissage et de test lorsque vous créez une structure d'exploration de données facilite énormément l'évaluation de l'exactitude des modèles d'exploration de données que vous créez ultérieurement.  
  
 Vous pouvez spécifier la quantité de données de test sous la forme d'un pourcentage ou vous pouvez spécifier un nombre pour limiter le nombre de scénarios utilisé pour le test. Si vous spécifiez à la fois un pourcentage et un nombre maximal de scénarios à utiliser pour le test, les deux paramètres sont utilisés et le jeu de données de test contient le nombre de cas le plus petit. Par défaut, 30 pour cent des données sont utilisées pour le test, 70 pour cent pour l'apprentissage et il n'existe aucun nombre maximal de scénarios de test.  
  
 Par défaut, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] génère une valeur de départ numérique utilisée pour démarrer le partitionnement. Cette valeur de départ est basée sur le nom de la structure d'exploration de données. Si vous souhaitez veiller à ce que la partition reste la même, même si le nom de la structure d'exploration de données est modifié, vous pouvez spécifier une valeur pour la valeur de départ, en définissant la propriété HoldoutSeed de la structure d'exploration de données. Si vous modifiez la valeur de départ d'exclusion, vous devez retraiter la structure.  
  
 Si vous souhaitez ultérieurement modifier la quantité de données d’apprentissage ou de test, vous pouvez modifier le `HoldoutMaxCases` et `HoldoutMaxPercent` propriétés sur la structure d’exploration de données à l’aide de la **propriétés** fenêtre. Toutefois, après avoir apporté cette modification, vous devez retraiter la structure d'exploration de données et tous les modèles d'exploration de données associés. Les limitations suivantes s'appliquent également :  
  
-   Le partitionnement d'une structure d'exploration de données est pris en charge uniquement lorsque la structure d'exploration de données est stockée dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. Les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ne prennent pas en charge la mise en cache des informations de partition pour les structures d’exploration de données.  
  
-   Vous ne pouvez pas partitionner une structure d'exploration de données si elle contient une colonne Temps clé, ce qui est obligatoire pour les modèles d'exploration de données de séries chronologiques.  
  
-   Vous ne pouvez pas partitionner des données si vous essayez de prédire une valeur qui est stockée dans une table imbriquée.  
  
 **Pour plus d’informations, consultez**  [Test et validation &#40;exploration de données&#41;](data-mining/testing-and-validation-data-mining.md), [Créer une structure d’exploration de données relationnelle](data-mining/create-a-relational-mining-structure.md) et [Didacticiel sur l’exploration de données de base](../../2014/tutorials/basic-data-mining-tutorial.md)  
  
## <a name="options"></a>Options  
 **Pourcentage des données de test**  
 Cliquez sur les flèches vers le haut et le bas pour augmenter ou réduire le pourcentage de données à utiliser en tant que jeu d'apprentissage ou tapez une valeur comprise entre 0 et 100 dans la zone de texte.  
  
 **Nombre maximal de cas dans le jeu de données de test**  
 Tapez un nombre pour limiter le nombre de scénarios qui peuvent être utilisés à des fins de test.  
  
 Si vous spécifiez un nombre supérieur au nombre de scénarios réels dans les données, tous les cas seront utilisés.  
  
 La valeur par défaut est NULL. Ce signifie qu'il n'existe aucune limite.  
  
## <a name="see-also"></a>Voir aussi  
 [Données d’aide F1 de l’Assistant exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Suggérer des colonnes associées &#40;Assistant exploration de données&#41;](suggest-related-columns-data-mining-wizard.md)   
 [Spécifier les Types de tables &#40;Assistant exploration de données&#41;](specify-table-types-data-mining-wizard.md)   
 [Spécifier le contenu et le Type de données de la colonne &#40;Assistant exploration de données&#41;](specify-the-column-s-content-and-data-type-data-mining-wizard.md)  
  
  

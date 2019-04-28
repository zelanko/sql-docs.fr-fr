---
title: Spécification du Type de données et d’un Type de contenu (didacticiel d’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 72484d27-3ef1-4f16-813c-2f43231fc2da
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 583a6fda2dbb4698405a3d69f33955531b3c1c10
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62720047"
---
# <a name="specifying-the-data-type-and-content-type-basic-data-mining-tutorial"></a>Spécification du type de données et du type de contenu (Didacticiel sur l'exploration de données de base)
  Maintenant que vous avez sélectionné les colonnes à utiliser pour la génération de votre structure et l'apprentissage de vos modèles, apportez les modifications nécessaires aux données et aux types de contenu par défaut définis par l'Assistant.  
  
#### <a name="review-and-modify-content-type-and-data-type-for-each-column"></a>Examiner et modifier le type de contenu et le type de données de chaque colonne  
  
1.  Sur le **colonnes spécifier Type de contenu et données** , cliquez sur **détecter** pour exécuter un algorithme qui détermine les données par défaut et les types de contenu pour chaque colonne.  
  
2.  Passez en revue les entrées dans le **Type de contenu** et **Type de données** colonnes et les modifier si nécessaire, pour vous assurer que les paramètres sont les mêmes que ceux répertoriés dans le tableau suivant.  
  
     En général, l'Assistant détecte les nombres et attribue un type de données numériques approprié. Toutefois, dans de nombreux scénarios, vous pouvez souhaiter gérer un nombre comme texte. Par exemple, le **GeographyKey** doit être gérée en tant que texte, car il n’est pas adapté effectuer des opérations mathématiques sur cet identificateur.  
  
    |colonne|Type de contenu|Type de données|  
    |------------|------------------|---------------|  
    |**Adresse ligne1**|**Discrètes**|**Text**|  
    |**Adresse ligne2**|**Discrètes**|**Text**|  
    |**Âge**|**continue**|**Long**|  
    |**Bike Buyer**|**Discrètes**|**Long**|  
    |**Commute Distance**|**Discrètes**|**Text**|  
    |**CustomerKey**|**Clé**|**Long**|  
    |**DateLastPurchase**|**continue**|**Date**|  
    |**Email Address**|**Discrètes**|**Text**|  
    |**English Education**|**Discrètes**|**Text**|  
    |**English Occupation**|**Discrètes**|**Text**|  
    |**FirstName**|**Discrètes**|**Text**|  
    |**Gender**|**Discrètes**|**Text**|  
    |**Clé de zone géographique**|**Discrètes**|**Text**|  
    |**House Owner Flag**|**Discrètes**|**Text**|  
    |**Last Name**|**Discrètes**|**Text**|  
    |**Marital Status**|**Discrètes**|**Text**|  
    |**Number Cars Owned**|**Discrètes**|**Long**|  
    |**Number Children At Home**|**Discrètes**|**Long**|  
    |**Région**|**Discrètes**|**Text**|  
    |**Total Children**|**Discrètes**|**Long**|  
    |**Yearly Income**|**continue**|**Double**|  
  
3.  Cliquer sur **Suivant**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Spécification d’un jeu de données de test pour la Structure &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Création d’une Structure de modèle d’exploration de données publipostage ciblé &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Types de contenu &#40;Exploration de données&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)   
 [Types de données &#40;exploration de données&#41;](../../2014/analysis-services/data-mining/data-types-data-mining.md)  
  
  

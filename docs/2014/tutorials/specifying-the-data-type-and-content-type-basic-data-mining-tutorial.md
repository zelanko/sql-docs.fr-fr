---
title: Spécification du type de données et du type de contenu (didacticiel sur l’exploration de données de base) | Microsoft Docs
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62720047"
---
# <a name="specifying-the-data-type-and-content-type-basic-data-mining-tutorial"></a>Spécification du type de données et du type de contenu (Didacticiel sur l'exploration de données de base)
  Maintenant que vous avez sélectionné les colonnes à utiliser pour la génération de votre structure et l'apprentissage de vos modèles, apportez les modifications nécessaires aux données et aux types de contenu par défaut définis par l'Assistant.  
  
#### <a name="review-and-modify-content-type-and-data-type-for-each-column"></a>Examiner et modifier le type de contenu et le type de données de chaque colonne  
  
1.  Dans la page **spécifier le type de contenu et de données des colonnes** , cliquez sur **détecter** pour exécuter un algorithme qui détermine les types de données et de contenu par défaut pour chaque colonne.  
  
2.  Examinez les entrées dans les colonnes **type de contenu** et **type de données** et modifiez-les si nécessaire pour vous assurer que les paramètres sont les mêmes que ceux répertoriés dans le tableau suivant.  
  
     En général, l'Assistant détecte les nombres et attribue un type de données numériques approprié. Toutefois, dans de nombreux scénarios, vous pouvez souhaiter gérer un nombre comme texte. Par exemple, le **GeographyKey** doit être géré en tant que texte, car il n’est pas approprié d’effectuer des opérations mathématiques sur cet identificateur.  
  
    |Colonne|Type de contenu|Type de données|  
    |------------|------------------|---------------|  
    |**Adresse ligne1**|**Discret**|**Text**|  
    |**Adresse-ligne2**|**Discret**|**Text**|  
    |**Age**|**Continue**|**Long**|  
    |**Bike Buyer**|**Discret**|**Long**|  
    |**Commute Distance**|**Discret**|**Text**|  
    |**CustomerKey**|**Clé**|**Long**|  
    |**DateLastPurchase**|**Continue**|**Date**|  
    |**Adresse de messagerie**|**Discret**|**Text**|  
    |**English Education**|**Discret**|**Text**|  
    |**English Occupation**|**Discret**|**Text**|  
    |**FirstName**|**Discret**|**Text**|  
    |**Sexe**|**Discret**|**Text**|  
    |**Geography Key**|**Discret**|**Text**|  
    |**House Owner Flag**|**Discret**|**Text**|  
    |**Nom**|**Discret**|**Text**|  
    |**Marital Status**|**Discret**|**Text**|  
    |**Number Cars Owned**|**Discret**|**Long**|  
    |**Number Children At Home**|**Discret**|**Long**|  
    |**Région**|**Discret**|**Text**|  
    |**Total Children**|**Discret**|**Long**|  
    |**Yearly Income**|**Continue**|**Double**|  
  
3.  Cliquez sur **Suivant**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Spécification d’un jeu de données de test pour la structure &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Création d’une structure de modèle d’exploration de données de publipostage ciblée &#40;didacticiel sur l’exploration de données de base&#41;](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Types de contenu &#40;l’exploration de données&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)   
 [Types de données &#40;Exploration de données&#41;](../../2014/analysis-services/data-mining/data-types-data-mining.md)  
  
  

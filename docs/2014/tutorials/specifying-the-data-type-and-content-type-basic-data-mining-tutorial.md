---
title: Spécification du Type de données et d’un Type de contenu (didacticiel d’exploration de données de base) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 72484d27-3ef1-4f16-813c-2f43231fc2da
caps.latest.revision: 25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 578d47783f22e857bb2fb84949e9d22dd6ad0e85
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174951"
---
# <a name="specifying-the-data-type-and-content-type-basic-data-mining-tutorial"></a>Spécification du type de données et du type de contenu (Didacticiel sur l'exploration de données de base)
  Maintenant que vous avez sélectionné les colonnes à utiliser pour la génération de votre structure et l'apprentissage de vos modèles, apportez les modifications nécessaires aux données et aux types de contenu par défaut définis par l'Assistant.  
  
#### <a name="review-and-modify-content-type-and-data-type-for-each-column"></a>Examiner et modifier le type de contenu et le type de données de chaque colonne  
  
1.  Sur le **colonnes spécifier Type de contenu et données** , cliquez sur **détecter** pour exécuter un algorithme qui détermine les données par défaut et les types de contenu pour chaque colonne.  
  
2.  Passez en revue les entrées dans le **Type de contenu** et **Type de données** colonnes et les modifier si nécessaire, pour vous assurer que les paramètres sont les mêmes que ceux répertoriés dans le tableau suivant.  
  
     En général, l'Assistant détecte les nombres et attribue un type de données numériques approprié. Toutefois, dans de nombreux scénarios, vous pouvez souhaiter gérer un nombre comme texte. Par exemple, le **GeographyKey** doit être gérée en tant que texte, car il n’est pas adapté effectuer des opérations mathématiques sur cet identificateur.  
  
    |colonne|Type de contenu|Type de données|  
    |------------|------------------|---------------|  
    |**Adresse ligne1**|**Discrètes**|**Texte**|  
    |**Adresse ligne2**|**Discrètes**|**Texte**|  
    |**Âge**|**Continue**|**Long**|  
    |**Bike Buyer**|**Discrètes**|**Long**|  
    |**Commute Distance**|**Discrètes**|**Texte**|  
    |**CustomerKey**|**Clé**|**Long**|  
    |**DateLastPurchase**|**Continue**|**Date**|  
    |**Email Address**|**Discrètes**|**Texte**|  
    |**English Education**|**Discrètes**|**Texte**|  
    |**English Occupation**|**Discrètes**|**Texte**|  
    |**firstName**|**Discrètes**|**Texte**|  
    |**Gender**|**Discrètes**|**Texte**|  
    |**Clé de zone géographique**|**Discrètes**|**Texte**|  
    |**House Owner Flag**|**Discrètes**|**Texte**|  
    |**Last Name**|**Discrètes**|**Texte**|  
    |**Marital Status**|**Discrètes**|**Texte**|  
    |**Number Cars Owned**|**Discrètes**|**Long**|  
    |**Number Children At Home**|**Discrètes**|**Long**|  
    |**Région**|**Discrètes**|**Texte**|  
    |**Total Children**|**Discrètes**|**Long**|  
    |**Yearly Income**|**Continue**|**Double**|  
  
3.  Cliquez sur **Suivant**.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Spécification d’un jeu de données de test pour la Structure &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial.md)  
  
## <a name="previous-task-in-lesson"></a>Tâche précédente de la leçon  
 [Création d’une Structure de modèle d’exploration de données publipostage ciblé &#40;didacticiel d’exploration de données de base&#41;](../../2014/tutorials/creating-a-targeted-mailing-mining-model-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Types de contenu &#40;exploration de données&#41;](../../2014/analysis-services/data-mining/content-types-data-mining.md)   
 [Types de données &#40;exploration de données&#41;](../../2014/analysis-services/data-mining/data-types-data-mining.md)  
  
  

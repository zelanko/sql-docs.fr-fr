---
title: Spécifiez le nombre d’objets (Assistant Optimisation de l’utilisation) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 306c7c25-ae24-4852-ab8c-c82f68a4bc1f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a6f4bb5bcf2584cba8265fb175b7581b6b40ce08
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48154059"
---
# <a name="specify-object-counts-usage-based-optimization-wizard"></a>Spécifier le nombre d'objets (Assistant Optimisation de l'utilisation)
  La page **Spécifier le nombre d'objets** permet de calculer automatiquement le nombre d'objets inclus dans le cube ou d'entrer une estimation manuellement. L'Assistant Optimisation de l'utilisation utilise le nombre d'objets pour évaluer la capacité de stockage nécessaire.  
  
## <a name="options"></a>Options  
 **Objets de cube**  
 Affiche les dimensions et les attributs du cube. Seuls les attributs qui n’ont pas leur `AggregationUsage` propriété définie sur None dans le **l’utilisation d’agrégation de révision** page de l’Assistant sont affichés, car ce sont les seuls attributs qui requièrent des nombres spécifiés.  
  
 **Nombre estimé**  
 Affiche le nombre estimé de lignes dans le groupe de mesures et l'estimation du nombre de membres d'attribut dans les dimensions de base de données. Vous pouvez taper une valeur à utiliser comme nombre estimé ou vous pouvez calculer les valeurs du compteur estimées. Pour calculer les valeurs du compteur, tapez 0 dans le champ puis cliquez sur **Nombre**. Les champs qui affichent déjà un nombre ne sont pas mis à jour.  
  
 **Nombre de partitions**  
 (Facultatif) Tapez le nombre estimé de lignes dans le groupe de mesures et l'estimation du nombre de membres d'attribut dans les partitions.  
  
 **Count**  
 Calcule et remplit à nouveau les valeurs de la colonne **Nombre estimé** pour tous les champs vides. Les champs qui affichent déjà un nombre ne sont pas mis à jour.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide de F1 l’Assistant conception d’agrégation](aggregation-design-wizard-f1-help.md)   
 [Assistants Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  

---
title: Spécifiez le nombre d’objets (Assistant Optimisation de l’utilisation) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 306c7c25-ae24-4852-ab8c-c82f68a4bc1f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e0503192c3c948110f8301c8eb375e1c8203e42f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66068237"
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
  
 **Compter**  
 Calcule et remplit à nouveau les valeurs de la colonne **Nombre estimé** pour tous les champs vides. Les champs qui affichent déjà un nombre ne sont pas mis à jour.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide de F1 l’Assistant conception d’agrégation](aggregation-design-wizard-f1-help.md)   
 [Assistants Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  

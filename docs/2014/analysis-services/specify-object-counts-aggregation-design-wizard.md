---
title: Spécifiez le nombre d’objets (Assistant de conception d’agrégation) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 305d9d79-d1ab-4704-a7b5-3283842b3996
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3711c21f6d69a7b5fd93456811e4bd3874116774
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62746173"
---
# <a name="specify-object-counts-aggregation-design-wizard"></a>Spécifier le nombre d'objets (Assistant Conception d'agrégation)
  La page **Spécifier le nombre d'objets** permet de calculer automatiquement le nombre d'objets inclus dans le cube ou d'entrer une estimation manuellement. L'Assistant Conception d'agrégation utilise le nombre d'objets pour évaluer la capacité de stockage nécessaire.  
  
## <a name="options"></a>Options  
 **Objets de cube**  
 Affiche les dimensions et les attributs du cube. Seuls les attributs qui n’ont pas leur `AggregationUsage` propriété définie sur `None` dans le **l’utilisation d’agrégation de révision** page de l’Assistant sont affichés, car ce sont les seuls attributs qui requièrent les spécification des nombres.  
  
 **Nombre estimé**  
 Affiche le nombre estimé de lignes dans le groupe de mesures et l'estimation du nombre de membres d'attribut dans les dimensions de base de données. Vous pouvez taper une valeur à utiliser comme nombre estimé ou vous pouvez calculer les valeurs du compteur estimées. Pour calculer les valeurs du compteur, tapez `0` dans le champ puis cliquez sur **nombre**. Les champs qui affichent déjà un nombre ne sont pas mis à jour.  
  
 **Nombre de partitions**  
 (Facultatif) Tapez le nombre estimé de lignes dans le groupe de mesures et tapez l'estimation du nombre de membres d'attribut dans les partitions.  
  
 **Compter**  
 Calcule et remplit à nouveau les valeurs de la colonne **Nombre estimé** pour tous les champs vides. Les champs qui affichent déjà un nombre ne sont pas mis à jour.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide de F1 l’Assistant conception d’agrégation](aggregation-design-wizard-f1-help.md)   
 [Assistants Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  

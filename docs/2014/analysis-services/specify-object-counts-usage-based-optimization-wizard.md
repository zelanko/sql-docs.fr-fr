---
title: Spécifiez le nombre d’objets (Assistant Optimisation de l’utilisation) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.storagedesignwizard.calculatingobjectcounts.f1
ms.assetid: 306c7c25-ae24-4852-ab8c-c82f68a4bc1f
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5a8a027183180cfccc885311218a84a0aa3c8ddd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039174"
---
# <a name="specify-object-counts-usage-based-optimization-wizard"></a>Spécifier le nombre d'objets (Assistant Optimisation de l'utilisation)
  La page **Spécifier le nombre d'objets** permet de calculer automatiquement le nombre d'objets inclus dans le cube ou d'entrer une estimation manuellement. L'Assistant Optimisation de l'utilisation utilise le nombre d'objets pour évaluer la capacité de stockage nécessaire.  
  
## <a name="options"></a>Options  
 **Objets de cube**  
 Affiche les dimensions et les attributs du cube. Seuls les attributs qui n’ont pas leur `AggregationUsage` propriété définie sur None dans le **l’utilisation d’agrégation de révision** page de l’Assistant sont affichés, car ce sont les attributs qui requièrent une spécification des nombres.  
  
 **Nombre estimé**  
 Affiche le nombre estimé de lignes dans le groupe de mesures et l'estimation du nombre de membres d'attribut dans les dimensions de base de données. Vous pouvez taper une valeur à utiliser comme nombre estimé ou vous pouvez calculer les valeurs du compteur estimées. Pour calculer les valeurs du compteur, tapez 0 dans le champ puis cliquez sur **Nombre**. Les champs qui affichent déjà un nombre ne sont pas mis à jour.  
  
 **Nombre de partitions**  
 (Facultatif) Tapez le nombre estimé de lignes dans le groupe de mesures et l'estimation du nombre de membres d'attribut dans les partitions.  
  
 **Count**  
 Calcule et remplit à nouveau les valeurs de la colonne **Nombre estimé** pour tous les champs vides. Les champs qui affichent déjà un nombre ne sont pas mis à jour.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide F1 l’Assistant conception d’agrégation](aggregation-design-wizard-f1-help.md)   
 [Assistants Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
---
title: Passez en revue l’utilisation d’agrégation (Assistant d’optimisation basée sur l’utilisation) | Documents Microsoft
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
- sql12.asvs.storagedesignwizard.reviewaggregationusage.f1
ms.assetid: 49ce2094-c4dc-4e46-8cef-c17c5db084ca
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 21618aabe9c7e429c7d78a68c7fcfb9d61a0754c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052038"
---
# <a name="review-aggregation-usage-usage-based-optimiation-wizard"></a>Passer en revue l'utilisation d'agrégation (Assistant Optimisation de l'utilisation)
  Utilisez la page **Passer en revue l'utilisation d'agrégation** pour configurer des paramètres d'utilisation d'agrégation.  
  
## <a name="options"></a>Options  
 **Default**  
 Sélectionnez pour que le paramètre d'utilisation d'agrégation de l'attribut possède la valeur Par défaut. En utilisant ce paramètre, le concepteur applique une règle par défaut selon le type d'attribut et de dimension.  
  
 **Complet**  
 Sélectionnez pour que le paramètre d'utilisation d'agrégation de l'attribut soit Full. En utilisant ce paramètre, chaque agrégation pour le cube doit inclure cet attribut ou un attribut associé qui est inférieur dans la chaîne d'attribut. Le paramètre d'utilisation d'agrégation Full doit être évité lorsqu'un attribut contient de nombreux membres. S'il est spécifié pour plusieurs attributs ou pour des attributs qui ont de nombreux membres, ce paramètre peut empêcher la conception d'agrégations en raison d'une taille excessive.  
  
 **Aucun**  
 Sélectionnez pour que le paramètre d'utilisation d'agrégation de l'attribut soit Aucun. En utilisant ce paramètre, aucune agrégation pour le cube ne peut inclure cet attribut.  
  
 **Non restreint**  
 Sélectionnez pour que le paramètre d'utilisation d'agrégation de l'attribut soit Unrestricted. En utilisant ce paramètre, aucune restriction n'est placée sur le concepteur d'agrégation. Toutefois, l'attribut doit encore être évalué pour déterminer s'il s'agit d'un candidat d'agrégation important.  
  
 **Définir tout à la valeur par défaut**  
 Sélectionnez pour définir les paramètres d'utilisation d'agrégation de tous les attributs avec la valeur par défaut.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide F1 l’Assistant conception d’agrégation](aggregation-design-wizard-f1-help.md)   
 [Assistants Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-wizards-multidimensional-data.md)  
  
  
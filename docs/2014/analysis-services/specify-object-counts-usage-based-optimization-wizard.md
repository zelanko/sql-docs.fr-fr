---
title: Spécifier le nombre d’objets (Assistant Optimisation de l’utilisation) | Microsoft Docs
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
ms.openlocfilehash: 862be19f12308def815a280dba04f42f0cbe6878
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84940310"
---
# <a name="specify-object-counts-usage-based-optimization-wizard"></a>Spécifier le nombre d'objets (Assistant Optimisation de l'utilisation)
  La page **Spécifier le nombre d'objets** permet de calculer automatiquement le nombre d'objets inclus dans le cube ou d'entrer une estimation manuellement. L'Assistant Optimisation de l'utilisation utilise le nombre d'objets pour évaluer la capacité de stockage nécessaire.  
  
## <a name="options"></a>Options  
 **Objets de cube**  
 Affiche les dimensions et les attributs du cube. Seuls les attributs dont la propriété n’est pas `AggregationUsage` définie sur aucun dans la page **passer en revue l’utilisation** de l’agrégation de l’Assistant sont affichés, car il s’agit des seuls attributs dont le nombre est spécifié.  
  
 **Nombre estimé**  
 Affiche le nombre estimé de lignes dans le groupe de mesures et l'estimation du nombre de membres d'attribut dans les dimensions de base de données. Vous pouvez taper une valeur à utiliser comme nombre estimé ou vous pouvez calculer les valeurs du compteur estimées. Pour calculer les valeurs du compteur, tapez 0 dans le champ puis cliquez sur **Nombre**. Les champs qui affichent déjà un nombre ne sont pas mis à jour.  
  
 **Nombre de partitions**  
 (Facultatif) Tapez le nombre estimé de lignes dans le groupe de mesures et l'estimation du nombre de membres d'attribut dans les partitions.  
  
 **Count**  
 Calcule et remplit à nouveau les valeurs de la colonne **Nombre estimé** pour tous les champs vides. Les champs qui affichent déjà un nombre ne sont pas mis à jour.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l’Assistant conception d’agrégation](aggregation-design-wizard-f1-help.md)   
 [Analysis Services assistants &#40;&#41;de données multidimensionnelles](analysis-services-wizards-multidimensional-data.md)  
  
  

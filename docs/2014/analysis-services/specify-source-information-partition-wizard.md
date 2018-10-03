---
title: Spécifier les informations Source (Assistant Partition) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.partitionwizard.specifydsvandfacttables.f1
ms.assetid: b6c13587-c690-45d9-af90-b3d652afc55b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ef93edfe6e78dd86963c7e810d33ec413194746a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48120556"
---
# <a name="specify-source-information-partition-wizard"></a>Spécifier des informations sur la source (Assistant Partition)
  La page **Spécifier des informations sur la source** permet de sélectionner le groupe de mesures dans lequel doit être créée la partition ainsi que la vue de source de données et les tables filtrées se rapportant à cette dernière.  
  
> [!CAUTION]  
>  Si vous spécifiez une table dans **Tables disponibles** qui est déjà utilisée par une autre partition, vous devez définir une requête dans la page **Restreindre les lignes** . Sinon, vous risquez d’obtenir des données en double dans le cube.  
  
## <a name="options"></a>Options  
 **Groupe de mesures**  
 Permet de sélectionner un groupe de mesures destiné à cette partition.  
  
 **Look in**  
 Permet d'indiquer la source de données ou la vue de source de données contenant les tables source destinées à cette partition. La vue de source de données utilisée par le groupe de mesures est l'élément sélectionné par défaut.  
  
 **Filtrer les tables**  
 Permet d’entrer la chaîne utilisée pour restreindre les tables affichées dans **Tables disponibles**d’après leur nom.  
  
 **Rechercher des tables**  
 Permet d’actualiser la liste des tables répertoriées dans **Tables disponibles**, et d’affiner la liste d’après les critères d’une chaîne indiquée dans **Filtrer les tables**, le cas échéant.  
  
 **Tables disponibles**  
 Permet de sélectionner les tables à utiliser en tant que tables source pour les partitions. L' **Assistant Partition** crée une partition pour chaque table sélectionnée dans **Tables disponibles**.  
  
 Si aucun filtre n'est précisé dans **Filtrer les tables**, cette option répertorie alors toutes les tables de la source de données ou de la vue de source de données indiquées dans **Regarder dans** et dont la structure est similaire à la table de faits utilisée par le groupe de mesures mentionné dans **Groupe de mesures**.  
  
 Si un filtre est spécifié dans **Filtrer les tables**, la liste est plus restreinte encore en comparant le filtre aux noms des tables satisfaisant le critère précédent. Ainsi, seules les tables contenant la chaîne spécifiée dans **Filtrer les tables** sont affichées.  
  
> [!NOTE]  
>  Si plusieurs tables sont sélectionnées, la page **Restreindre les lignes** ne peut alors pas s'afficher et les lignes ne peuvent pas être restreintes pour les partitions créées à partir des tables sélectionnées. Dans ce cas, pour restreindre les lignes relatives à chaque partition, lancez l'Assistant Partition une fois pour chaque table à partir de laquelle une partition doit être créée.  
  
## <a name="see-also"></a>Voir aussi  
 [Partitions &#40;Analysis Services - données multidimensionnelles&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  

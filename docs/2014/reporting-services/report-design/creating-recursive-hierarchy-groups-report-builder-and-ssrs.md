---
title: Création de groupes de hiérarchies récursives (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 92412bbde8a1032b34264ca254560f31704281e8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63135573"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>Création de groupes de hiérarchies récursives (Générateur de rapports et SSRS)
  Pour afficher les données récursives où la relation entre parent et enfant est représentée par des champs dans le jeu de données, vous pouvez définir l’expression de groupe de région de données en fonction du champ enfant et définir la propriété Parent basée sur le champ parent.  
  
 Affichage de données hiérarchiques est une utilisation courante pour les groupes de hiérarchies récursives, par exemple, les employés dans un organigramme. Le jeu de données inclut une liste d’employés et les directeurs, où les noms de directeurs apparaissent également dans la liste des employés.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>Création de hiérarchies récursives  
 Pour créer une hiérarchie récursive dans une région de données de tableau matriciel, vous devez définir l’expression de groupe pour le champ qui spécifie les données enfants et la propriété Parent du groupe pour le champ qui spécifie les données parentes. Par exemple, pour un dataset qui inclut des champs pour l’ID d’employé et ID de directeur où employés rendent des comptent aux responsables, définir l’expression de groupe pour l’ID d’employé et de la propriété Parent au Gestionnaire de code.  
  
 Un groupe qui est défini comme une hiérarchie récursive (autrement dit, un groupe qui utilise la propriété Parent) peut avoir qu’une seule expression de groupe. Vous pouvez utiliser la fonction `Level` dans la définition de la marge intérieure de la zone de texte pour appliquer un retrait aux noms des employés en fonction du niveau que ceux-ci occupent dans la hiérarchie.  
  
 Pour plus d’informations, consultez [ajouter ou supprimer un groupe dans une région de données &#40;Générateur de rapports et SSRS&#41; ](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) et [créer un groupe de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).  
  
### <a name="aggregate-functions-that-support-recursion"></a>Fonctions d’agrégation qui prennent en charge la récursivité  
 Vous pouvez utiliser les fonctions d’agrégation Reporting Services qui acceptent le paramètre *récursive* pour calculer les données de synthèse d’une hiérarchie récursive. Les fonctions suivantes acceptent `Recursive` en tant que paramètre : [Somme](report-builder-functions-sum-function.md), [Avg](report-builder-functions-avg-function.md), [nombre](report-builder-functions-count-function.md), [CountDistinct](report-builder-functions-countdistinct-function.md), [CountRows](report-builder-functions-countrows-function.md), [Max](report-builder-functions-max-function.md), [Min](report-builder-functions-min-function.md), [StDev](report-builder-functions-stdev-function.md), [StDevP](report-builder-functions-stdevp-function.md), [somme](report-builder-functions-sum-function.md), [Var](report-builder-functions-var-function.md), et [VarP](report-builder-functions-varp-function.md) . Pour plus d’informations, consultez [référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tables, Matrices et listes &#40;Générateur de rapports et SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Région de données de tableau matriciel &#40;Générateur de rapports et SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)   
 [Tables &#40;Générateur de rapports et SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Matrices &#40;Générateur de rapports et SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Répertorie les &#40;Générateur de rapports et SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tables, Matrices et listes &#40;Générateur de rapports et SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  

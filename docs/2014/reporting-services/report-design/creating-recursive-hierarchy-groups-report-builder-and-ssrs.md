---
title: Création de groupes de hiérarchies récursives (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 06eccab6-4089-46e8-a84f-5bf3bbe0c23b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ea704f5ec6ab26db37bb56b86a42605ab50dd48b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66106119"
---
# <a name="creating-recursive-hierarchy-groups-report-builder-and-ssrs"></a>Création de groupes de hiérarchies récursives (Générateur de rapports et SSRS)
  Pour afficher les données récursives où la relation entre parent et enfant est représentée par des champs dans le jeu de données, vous pouvez définir l’expression de groupe de région de données en fonction du champ enfant et définir la propriété Parent basée sur le champ parent.  
  
 L'affichage de données hiérarchiques est couramment utilisé pour les groupes de hiérarchies récursives, par exemple des employés dans un graphique d'organisation. Le dataset inclut une liste d'employés et les directeurs, où les noms de directeurs apparaissent également dans la liste des employés.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="creating-recursive-hierarchies"></a>Création de hiérarchies récursives  
 Pour créer une hiérarchie récursive dans une région de données de tableau matriciel, vous devez définir l’expression de groupe en fonction du champ qui spécifie les données enfants et la propriété Parent du groupe en fonction du champ qui spécifie les données parents. Par exemple, pour un dataset qui comprend des champs pour l’ID d’employé et l’ID de responsables où les employés rendent des comptent aux responsables, affectez l’ID d’employé à l’expression de groupe et l’ID de responsable à la propriété Parent.  
  
 Un groupe défini en tant que hiérarchie récursive (c’est-à-dire un groupe qui utilise la propriété Parent) ne peut comporter qu’une seule expression de groupe. Vous pouvez utiliser la fonction `Level` dans la définition de la marge intérieure de la zone de texte pour appliquer un retrait aux noms des employés en fonction du niveau que ceux-ci occupent dans la hiérarchie.  
  
 Pour plus d’informations, consultez [Ajouter ou supprimer un groupe dans une région de données &#40;Générateur de rapports et SSRS&#41;](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md) et [Créer un groupe de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md).  
  
### <a name="aggregate-functions-that-support-recursion"></a>Fonctions d'agrégation qui prennent en charge la récursivité  
 Vous pouvez utiliser les fonctions d’agrégation Reporting Services qui acceptent le paramètre *Recursive* pour calculer les données de synthèse d’une hiérarchie récursive. Les fonctions suivantes acceptent `Recursive` en tant que paramètre : [Sum](report-builder-functions-sum-function.md), [Avg](report-builder-functions-avg-function.md), [Count](report-builder-functions-count-function.md), [CountDistinct](report-builder-functions-countdistinct-function.md), [CountRows](report-builder-functions-countrows-function.md), [Max](report-builder-functions-max-function.md), [Min](report-builder-functions-min-function.md), [StDev](report-builder-functions-stdev-function.md), [StDevP](report-builder-functions-stdevp-function.md), [Sum](report-builder-functions-sum-function.md), [Var](report-builder-functions-var-function.md) et [VarP](report-builder-functions-varp-function.md). Pour plus d’informations, consultez [Informations de référence sur les fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tables, matrices et listes &#40;Générateur de rapports et SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)   
 [Région de données de tableau matriciel &#40;Générateur de rapports et SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md)   
 [Informations de référence sur les fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)   
 [Tables &#40;Générateur de rapports et SSRS&#41;](tables-report-builder-and-ssrs.md)   
 [Matrices &#40;Générateur de rapports et SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md)   
 [Listes &#40;Générateur de rapports et SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [Tables, matrices et listes &#40;Générateur de rapports et SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  

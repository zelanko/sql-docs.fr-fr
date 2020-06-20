---
title: 'Tâche 11 : ajout d’une transformation de fractionnement conditionnel pour filtrer les doublons | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3094bd57-5cf4-4860-bf51-fadd1b309f94
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ad925c543cefaf7aed5a0ef355029312b3de7140
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85064794"
---
# <a name="task-11-adding-conditional-split-transform-to-filter-duplicates"></a>Tâche 11 : Ajout d’une transformation de fractionnement conditionnel pour filtrer les doublons
  Dans cette tâche, vous allez ajouter la transformation de fractionnement conditionnel au flux de données. Cette transformation vous permet de filtrer les doublons à partir d'un jeu d'enregistrements entrant. La transformation de regroupement probable regroupe les enregistrements qu'elle identifie comme étant correspondants et choisit l'un des enregistrements comme enregistrement pivot. Tous les enregistrements d'un groupe possèdent la même valeur _key_out. L'enregistrement pivot dans le groupe a un _key_in identique à la valeur _key_out. Les autres enregistrements du groupe ont des valeurs différentes pour _key_in et _key_out. Par conséquent, lorsque vous filtrez en utilisant la condition _key_in==_key_out, vous obtenez uniquement la ligne pivot du groupe.  
  
1.  Glissez-déplacez la transformation de **fractionnement conditionnel** de la section **commun** dans la **boîte à outils SSIS** vers l’onglet de **Workflow** .  
  
2.  Cliquez avec le bouton droit sur **transformation de fractionnement conditionnel** sous l’onglet **Flow Data** , puis cliquez sur **Renommer**. Tapez **Filtrer les doublons** et appuyez sur **entrée**.  
  
3.  Connectez **les fournisseurs avec des ID correspondants** pour **Filtrer les doublons**.  
  
4.  Double-cliquez sur **Filtrer les doublons** pour ouvrir la boîte de dialogue **éditeur de transformation de fractionnement conditionnel** .  
  
5.  Développez **colonnes** dans le volet en haut à gauche.  
  
6.  Glisser-déplacer **_key_in** vers la colonne **condition** .  
  
7.  Type = = (est égal à) en regard de **_key_in** et glisser-déplacer **_key_out**.  
  
8.  Cliquez sur **cas 1** dans la colonne **nom** de la sortie, tapez **enregistrements uniques**, puis appuyez sur **entrée**.  
  
     ![Éditeur de transformation de fractionnement conditionnel](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "Éditeur de transformation de fractionnement conditionnel")  
  
9. Cliquez sur **OK** pour fermer la boîte de dialogue **éditeur de transformation de fractionnement conditionnel** .  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 12 : Ajout d’une transformation de colonne dérivée pour ajouter les colonnes requises par MDS](../../2014/tutorials/task-12-adding-derived-column-transform-to-add-columns-required-by-mds.md)  
  
  

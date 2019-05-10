---
title: 'Tâche 11 : Ajout conditionnel fractionner transformation pour filtrer les doublons | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 3094bd57-5cf4-4860-bf51-fadd1b309f94
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 71b050e49440764d355d4658607600c135741f50
ms.sourcegitcommit: 5748d710960a1e3b8bb003d561ff7ceb56202ddb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476751"
---
# <a name="task-11-adding-conditional-split-transform-to-filter-duplicates"></a>Tâche 11 : Ajout d’une transformation de fractionnement conditionnel pour filtrer les doublons
  Dans cette tâche, vous allez ajouter la transformation de fractionnement conditionnel au flux de données. Cette transformation vous permet de filtrer les doublons à partir d'un jeu d'enregistrements entrant. La transformation de regroupement probable regroupe les enregistrements qu'elle identifie comme étant correspondants et choisit l'un des enregistrements comme enregistrement pivot. Tous les enregistrements d'un groupe possèdent la même valeur _key_out. L'enregistrement pivot dans le groupe a un _key_in identique à la valeur _key_out. Les autres enregistrements du groupe ont des valeurs différentes pour _key_in et _key_out. Par conséquent, lorsque vous filtrez en utilisant la condition _key_in==_key_out, vous obtenez uniquement la ligne pivot du groupe.  
  
1.  Glisser-déplacer **fractionnement conditionnel** transformer de **commune** section dans le **boîte à outils SSIS** à la **de flux de données** onglet.  
  
2.  Avec le bouton droit **transformation de fractionnement conditionnel** dans le **de flux de données** onglet, puis cliquez sur **renommer**. Type **filtrer les doublons** et appuyez sur **entrée**.  
  
3.  Se connecter **groupe fournisseurs avec des ID correspondants** à **filtrer les doublons**.  
  
4.  Double-cliquez sur **filtrer les doublons** pour lancer le **l’éditeur de transformation de fractionnement conditionnel** boîte de dialogue.  
  
5.  Développez **colonnes** dans le volet supérieur gauche.  
  
6.  Glisser-déplacer **_key_in** à la **Condition** colonne.  
  
7.  Type == (égal à) à côté **_key_in** et glissez-déposez **_key_out**.  
  
8.  Cliquez sur **cas 1** dans le **nom de sortie** colonne, tapez **enregistrements uniques**, puis appuyez sur **entrée**.  
  
     ![Éditeur de Transformation de fractionnement conditionnel](../../2014/tutorials/media/et-addingconditionalsplittransformtofilterduplicates.jpg "éditeur de Transformation de fractionnement conditionnel")  
  
9. Cliquez sur **OK** pour fermer la **éditeur de Transformation de fractionnement conditionnel** boîte de dialogue.  
  
## <a name="next-step"></a>Étape suivante  
 [Tâche 12 : Ajout d’une transformation de colonne à ajouter les colonnes requises par MDS dérivée](../../2014/tutorials/task-12-adding-derived-column-transform-to-add-columns-required-by-mds.md)  
  
  

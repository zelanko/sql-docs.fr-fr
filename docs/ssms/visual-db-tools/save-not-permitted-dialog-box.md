---
title: "Enregistrer (non autorisé), boîte de dialogue | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.table.tablerecreatenosave.f1
ms.assetid: 7efda8e3-739f-4c97-a497-b8808a0acbea
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f478b87102174266ff23733b20777df253240317
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="save-not-permitted-dialog-box"></a>Enregistrer (non autorisé), boîte de dialogue
La boîte de dialogue **Enregistrer** (non autorisé) vous prévient que l’enregistrement des modifications n’est pas autorisé car les modifications que vous avez apportées nécessitent la suppression et la recréation des tables répertoriées.  
  
Les actions suivantes peuvent nécessiter la recréation d'une table :  
  
-   Ajout d'une nouvelle colonne au milieu de la table  
  
-   Suppression d'une colonne  
  
-   Modification de la possibilité de valeur nulle d'une colonne  
  
-   Modification de l'ordre des colonnes  
  
-   Modification du type de données d'une colonne  
  
Pour modifier cette option, dans le menu **Outils** , cliquez sur **Options**, développez **Concepteurs**, puis cliquez sur **Concepteurs de bases de données et de tables**. Cochez ou décochez la case **Empêcher l’enregistrement de modifications qui nécessitent une recréation de la table** .  
  


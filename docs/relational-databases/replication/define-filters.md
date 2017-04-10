---
title: "D&#233;finir les filtres | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.replconflictviewer.definefilters.f1"
helpviewer_keywords: 
  - "boîte de dialogue Définir les filtres"
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# D&#233;finir les filtres
  La boîte de dialogue **Définir les filtres** vous permet de définir les filtres que vous appliquerez aux conflits de données afin d'afficher un sous-ensemble de conflits dans la grille. Pour définir un filtre, choisissez un opérateur dans le **opérateur** liste déroulante zone, puis entrez une valeur. Par exemple, pour afficher uniquement les conflits dans lesquels le perdant du conflit est serveur **ReplTest1**, sélectionnez **égal à** à partir de la **opérateur** liste déroulante zone, puis entrez **ReplTest1** dans la première **valeur** colonne.  
  
## Options  
 **Opérateur**  
 Sélectionnez un opérateur pour le filtre, tel que **inférieure ou égale à**.  
  
 **Valeur**  
 Entrez une valeur pour le filtre. La plupart des opérateurs nécessitent uniquement la saisie d'une valeur dans la première colonne **Valeur** , mais les opérateurs **Entre** et **Non compris entre** nécessitent une valeur dans les deux colonnes **Valeur** .  
  
 **Désactiver**  
 Cliquez sur ce bouton pour effacer tous les filtres précédemment définis.  
  
## Voir aussi  
 [Conflits de réplication de Microsoft & #40 ; La réplication de fusion & #41 ;](../../relational-databases/replication/microsoft-replication-conflict-viewer-merge-replication.md)   
 [Conflits de réplication de Microsoft & #40 ; La réplication transactionnelle & #41 ;](../../relational-databases/replication/microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  
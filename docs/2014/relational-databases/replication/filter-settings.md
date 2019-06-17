---
title: Paramètres du filtre | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bd4c6f3729d4d090854a48a65ce6d6a2465a98e2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62721210"
---
# <a name="filter-settings"></a>Paramètres du filtre
  La boîte de dialogue **Paramètres du filtre** vous permet de définir des filtres pour les grilles dans le Moniteur de réplication. Par exemple, pour afficher uniquement les abonnements qui sont actifs sous l'onglet **Tous les abonnements** , sélectionnez **État** dans la colonne **Nom de la colonne** , **Égal à** dans la colonne **Opérateur** , et **Actif** dans la colonne **Valeur1** . Une fois que vous avez défini un filtre basé sur une ou plusieurs colonnes, le filtre est appliqué afin que la grille affiche uniquement le sous-ensemble de lignes correspondant aux critères du filtre.  
  
## <a name="options"></a>Options  
 **Nom de la colonne**  
 Sélectionnez le nom de la colonne sur laquelle vous souhaitez baser le filtre. Vous pouvez baser un filtre sur une ou plusieurs colonnes.  
  
 **Opérateur**  
 Sélectionnez un opérateur pour le filtre, ex. : **Inférieur ou Égal à**.  
  
 **Valeur1** et **Valeur2**  
 Entrez ou sélectionnez une valeur pour le filtre. La plupart des opérateurs nécessitent uniquement la saisie d'une valeur dans la colonne **Valeur1** , mais les opérateurs **Entre** et **Non compris entre** nécessitent aussi une valeur dans la colonne **Valeur2** .  
  
 **Effacer le filtre**  
 Cliquez sur ce bouton pour effacer tous les filtres qui ont été définis. Pour supprimer un filtre unique, sélectionnez la ligne du filtre et appuyez sur la touche Suppr.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance de la réplication](monitoring-replication.md)  
  
  

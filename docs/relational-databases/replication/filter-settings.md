---
title: Paramètres du filtre | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.filtersettings.f1
ms.assetid: 1b401d7d-db8a-4ba1-acb1-b8dec14e3311
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a626e79a33c134a3bdde5880b68f2545c6dea78e
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54129639"
---
# <a name="filter-settings"></a>Paramètres du filtre
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
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
  
## <a name="see-also"></a> Voir aussi  
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  

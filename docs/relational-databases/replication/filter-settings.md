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
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: fbf94f1ef3926c43f44e293f783ba0f1ac57fac9
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68767705"
---
# <a name="filter-settings"></a>Paramètres du filtre
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
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
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  

---
description: Définir les filtres
title: Définir les filtres | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.replconflictviewer.definefilters.f1
helpviewer_keywords:
- Define Filters dialog box
ms.assetid: 1fa71d22-ce5a-4aae-ba05-4d755842aeac
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4834e78ec82a681faba9f6c0fa780d78f890def
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88498782"
---
# <a name="define-filters"></a>Définir les filtres
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
   La boîte de dialogue **Définir les filtres** vous permet de définir les filtres que vous appliquerez aux conflits de données afin d’afficher un sous-ensemble de conflits dans la grille. Pour définir un filtre, choisissez un opérateur dans la zone de liste déroulante **Opérateur** , puis entrez une valeur. Par exemple, pour afficher uniquement les conflits dans lesquels le perdant du conflit est le serveur **ReplTest1**, sélectionnez **Égal à** dans la zone de liste déroulante **Opérateur** et entrez **ReplTest1** dans la première colonne **Valeur** .  
  
## <a name="options"></a>Options  
 **Opérateur**  
 Sélectionnez un opérateur pour le filtre, ex. : **Inférieur ou Égal à**.
  
 **Valeur**  
 Entrez une valeur pour le filtre. La plupart des opérateurs nécessitent uniquement la saisie d'une valeur dans la première colonne **Valeur** , mais les opérateurs **Entre** et **Non compris entre** nécessitent une valeur dans les deux colonnes **Valeur** .  
  
 **Clear**  
 Cliquez sur ce bouton pour effacer tous les filtres précédemment définis.  
  
## <a name="see-also"></a>Voir aussi  
 [Visionneuse des conflits de réplication de Microsoft &#40;réplication de fusion&#41;](../../relational-databases/replication/microsoft-replication-conflict-viewer-merge-replication.md)   
 [Visionneuse des conflits de réplication de Microsoft &#40;réplication transactionnelle&#41;](../../relational-databases/replication/microsoft-replication-conflict-viewer-transactional-replication.md)  
  
  

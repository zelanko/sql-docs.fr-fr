---
title: Valider des repères de plan après la mise à niveau | Microsoft Docs
description: Quand vous mettez à niveau votre application vers une nouvelle version de SQL Server, nous vous recommandons de réévaluer et de tester les définitions des repères de plan.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- plan guides [SQL Server], validating after upgrade
ms.assetid: a55ebd88-6f58-454d-b1c4-991b88add522
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: bb7b3981c76e5bf8059d13afc74f3181d4b60cea
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86456862"
---
# <a name="validate-plan-guides-after-upgrade"></a>Valider des repères de plan après la mise à niveau
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Il est recommandé de réévaluer et de tester les définitions des repères de plan lorsque vous mettez à niveau votre application vers une nouvelle version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les contraintes liées au paramétrage des performances et le comportement de la mise en correspondance des repères de plan peuvent changer. Même si un repère de plan non valide n'entraîne pas l'échec d'une requête, le plan est compilé sans utiliser le repère de plan et peut ne pas être le meilleur choix. Après avoir mis à niveau une base de données vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], nous recommandons d'effectuer les tâches suivantes :  
  
-   Validez les repères de plan existants à l’aide de la fonction [sys.fn_validate_plan_guide](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md) .  
  
-   Faites appel à des événements étendus pour rechercher les plans erronés sur période déterminée à l’aide de l’événement [Plan Guide Unsuccessful](../../relational-databases/event-classes/plan-guide-unsuccessful-event-class.md) .  
  
  

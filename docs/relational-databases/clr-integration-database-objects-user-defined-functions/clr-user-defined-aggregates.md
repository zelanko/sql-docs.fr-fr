---
title: Agrégats CLR définis par l’utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
caps.latest.revision: 35
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: aef4fdcd15708efd9c849f7f5ebb2a37d72a0523
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="clr-user-defined-aggregates"></a>Agrégats CLR définis par l'utilisateur 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Les fonctions d'agrégation effectuent un calcul sur un ensemble de valeurs et retournent une valeur unique. En règle générale, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a pris en charge uniquement les fonctions d’agrégation intégrées, telles que **somme** ou **MAX**, qui opèrent sur un ensemble de valeurs scalaires d’entrée et générer une valeur d’agrégation unique à partir de cet ensemble. L'intégration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec le CLR (Common Language Runtime) de [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework permet à présent aux développeurs de créer des fonctions d'agrégation personnalisées en code managé et de mettre ces fonctions à la disposition de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'un autre code managé.  
  
 Le tableau suivant décrit les rubriques de cette section.  
  
 [Configuration requise pour les agrégats CLR définis par l’utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates-requirements.md)  
 Fournit une vue d'ensemble de la configuration requise pour l'implémentation des fonctions d'agrégation définies par l'utilisateur du CLR.  
  
 [Appel de fonctions d’agrégation définies par l’utilisateur CLR](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)  
 Explique comment appeler des agrégats définis par l'utilisateur.  
  
  

---
title: Agrégats CLR définis par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 59666e90a47d88762c6fc3bd1fabc0e71ea18f94
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62919580"
---
# <a name="clr-user-defined-aggregates"></a>Agrégats CLR définis par l'utilisateur
  Les fonctions d’agrégation effectuent un calcul sur un ensemble de valeurs et renvoient une valeur unique. Traditionnellement, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a pris en charge uniquement les fonctions d’agrégation intégrées, `SUM` telles `MAX`que ou, qui opèrent sur un ensemble de valeurs scalaires d’entrée et génèrent une valeur d’agrégation unique à partir de cet ensemble. L'intégration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec le CLR (Common Language Runtime) de [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework permet à présent aux développeurs de créer des fonctions d'agrégation personnalisées en code managé et de mettre ces fonctions à la disposition de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'un autre code managé.  
  
 Le tableau suivant décrit les rubriques de cette section.  
  
 [Conditions requises pour les agrégats CLR définis par l'utilisateur](clr-user-defined-aggregates-requirements.md)  
 Fournit une vue d'ensemble de la configuration requise pour l'implémentation des fonctions d'agrégation définies par l'utilisateur du CLR.  
  
 [Appel de fonctions d'agrégation CLR définies par l'utilisateur](clr-user-defined-aggregate-invoking-functions.md)  
 Explique comment appeler des agrégats définis par l'utilisateur.  
  
  

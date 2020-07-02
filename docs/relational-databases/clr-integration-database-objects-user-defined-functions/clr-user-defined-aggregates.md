---
title: Agrégats CLR définis par l’utilisateur | Microsoft Docs
description: SQL Server l’intégration du CLR vous permet de créer des fonctions d’agrégation personnalisées dans du code managé, qui effectuent un calcul sur un ensemble de valeurs et retournent une valeur.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
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
ms.openlocfilehash: 6775e9f4bda98f970fd5cdb666fb0bfdb8c1ac10
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727870"
---
# <a name="clr-user-defined-aggregates"></a>Agrégats CLR définis par l'utilisateur
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Les fonctions d’agrégation effectuent un calcul sur un ensemble de valeurs et renvoient une valeur unique. Traditionnellement, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend uniquement en charge les fonctions d'agrégation intégrées, telles que **SUM** ou **MAX**, qui opèrent sur un ensemble de valeurs d'entrée scalaires et génèrent une valeur d'agrégation unique à partir de cet ensemble. L'intégration de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec le CLR (Common Language Runtime) de [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework permet à présent aux développeurs de créer des fonctions d'agrégation personnalisées en code managé et de mettre ces fonctions à la disposition de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'un autre code managé.  
  
 Le tableau suivant décrit les rubriques de cette section.  
  
 [Conditions requises pour les agrégats CLR définis par l'utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates-requirements.md)  
 Fournit une vue d'ensemble de la configuration requise pour l'implémentation des fonctions d'agrégation définies par l'utilisateur du CLR.  
  
 [Appel de fonctions d'agrégation CLR définies par l'utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)  
 Explique comment appeler des agrégats définis par l'utilisateur.  
  
  

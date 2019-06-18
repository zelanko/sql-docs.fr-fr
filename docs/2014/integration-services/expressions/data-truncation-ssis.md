---
title: Troncation de données (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ce2b4a14d78c4e855c4af1d8b5fdd972b1d28c27
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62898328"
---
# <a name="data-truncation-ssis"></a>Troncation de données (SSIS)
  Une expression peut accidentellement tronquer des données. La troncation peut se produire dans les circonstances suivantes :  
  
-   Chaînes. Par exemple, la conversion de données de chaîne ayant pour type de données DT_WSTR en une chaîne de même longueur mesurée en caractères et de type de données DT_STR provoque une perte de données si la chaîne d'origine contient des caractères codés sur deux octets.  
  
-   Chiffres significatifs. Par exemple, la conversion d'un entier d'un type de données DT_I4 en un type de données DT_I2, ou d'un entier non signé en un entier signé.  
  
-   Chiffres non significatifs. Par exemple, la conversion d'un nombre réel d'un type de données DT_R8 en un type de données DT_R4, ou d'un entier d'un type de données DT_I4 en un type de données DT_R4.  
  
 L'évaluateur d'expression identifie les conversions explicites pouvant provoquer une troncation et émet un avertissement lorsque l'expression est analysée. Par exemple, l'évaluateur d'expression émet un avertissement si vous convertissez une chaîne de 30 caractères en une chaîne de 20 caractères.  
  
> [!NOTE]  
>  La troncation n'est pas vérifiée à l'exécution ; les données sont tronquées sans que vous en soyez averti. Toutefois, la plupart des transformations et des adaptateurs de données prennent en charge des sorties d'erreur pouvant gérer la disposition des lignes d'erreur. Pour plus d’informations sur la gestion de la troncation de données, consultez [gestion des erreurs dans les données](../data-flow/error-handling-in-data.md).  
  
  

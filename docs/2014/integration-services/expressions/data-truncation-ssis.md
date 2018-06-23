---
title: Troncation de données (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
caps.latest.revision: 32
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: e735659fb2898c2ab6bc428d7ad6fc0f5759f17c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142312"
---
# <a name="data-truncation-ssis"></a>Troncation de données (SSIS)
  Une expression peut accidentellement tronquer des données. La troncation peut se produire dans les circonstances suivantes :  
  
-   Chaînes. Par exemple, la conversion de données de chaîne ayant pour type de données DT_WSTR en une chaîne de même longueur mesurée en caractères et de type de données DT_STR provoque une perte de données si la chaîne d'origine contient des caractères codés sur deux octets.  
  
-   Chiffres significatifs. Par exemple, la conversion d'un entier d'un type de données DT_I4 en un type de données DT_I2, ou d'un entier non signé en un entier signé.  
  
-   Chiffres non significatifs. Par exemple, la conversion d'un nombre réel d'un type de données DT_R8 en un type de données DT_R4, ou d'un entier d'un type de données DT_I4 en un type de données DT_R4.  
  
 L'évaluateur d'expression identifie les conversions explicites pouvant provoquer une troncation et émet un avertissement lorsque l'expression est analysée. Par exemple, l'évaluateur d'expression émet un avertissement si vous convertissez une chaîne de 30 caractères en une chaîne de 20 caractères.  
  
> [!NOTE]  
>  La troncation n'est pas vérifiée à l'exécution ; les données sont tronquées sans que vous en soyez averti. Toutefois, la plupart des transformations et des adaptateurs de données prennent en charge des sorties d'erreur pouvant gérer la disposition des lignes d'erreur. Pour plus d’informations sur la troncation de la gestion des données, consultez [Error Handling in Data](../data-flow/error-handling-in-data.md).  
  
  
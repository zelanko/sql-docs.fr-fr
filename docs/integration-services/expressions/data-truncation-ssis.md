---
title: "Troncation de données (SSIS) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- truncating data
- data truncation [Integration Services]
- expressions [Integration Services], data truncation
- truncate options [Integration Services]
ms.assetid: 02461e15-49ca-445b-abb3-5c369c283ec2
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5bed8ab4de8d1fe868cf12ca9e90e1040857d858
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="data-truncation-ssis"></a>Troncation de données (SSIS)
  La conversion de valeurs de données d’un type vers un autre peut entraîner la troncation de certaines valeurs.  
  
 Cette troncation peut se produire dans les cas suivants :  
  
-   Conversion des données de chaîne du type *DT_WSTR* en données de type *DT_STR* avec la même longueur lorsque la chaîne d’origine contient des caractères codés sur deux octets.  
  
-   Conversion d’un entier du type *DT_I4* vers le type *DT_I2* (des chiffres significatifs risquent d’être perdus).  
  
-   Conversion d’un entier non signé en entier signé (des chiffres significatifs risquent d’être perdus).  
  
-   Conversion d’un nombre réel du type *DT_R8* vers le type *DT_R4* (des chiffres non significatifs risquent d’être perdus).  
  
-   Conversion d’un entier du type *DT_I4* vers le type *DT_R4* (des chiffres non significatifs risquent d’être perdus).  
  
 L'évaluateur d'expression identifie les conversions explicites pouvant provoquer une troncation et émet un avertissement lorsque l'expression est analysée. Par exemple, l'évaluateur d'expression émet un avertissement si vous convertissez une chaîne de 30 caractères en une chaîne de 20 caractères.  
  
 Toutefois, la troncation éventuelle des caractères n’est pas vérifiée au moment de l’exécution. Lors de l’exécution, les données sont tronquées sans avertissement. La plupart des transformations et des adaptateurs de données prennent en charge des sorties d’erreur pouvant gérer la disposition des lignes d’erreur.  
  
 Pour en savoir plus sur la gestion de la troncation des données, consultez [Gestion des erreurs dans les données](../../integration-services/data-flow/error-handling-in-data.md).  
  
  

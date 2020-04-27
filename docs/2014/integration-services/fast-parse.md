---
title: Analyse rapide | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- fast parse [Integration Services]
ms.assetid: 6688707d-3c5b-404e-aa2f-e13092ac8d95
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b13ddc498962ca23e6bc1f5e7a10d88af47ff7d6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66058870"
---
# <a name="fast-parse"></a>Analyse rapide
  L'analyse rapide propose un ensemble de routines simples et rapides d'analyse des données. Ces routines ne tiennent pas compte des paramètres régionaux et prennent en charge uniquement un sous-ensemble de formats de date, d'heure et d'entier.  
  
## <a name="requirements-and-limitations"></a>Limitations et exigences  
 En implémentant l'analyse rapide, un package perd sa capacité d'interpréter les données de type date, heure et nombre dans des formats régionaux et dans de nombreux formats de base et étendus ISO 9601 couramment utilisés, mais il améliore ses performances. Par exemple, l'analyse rapide prend uniquement en charge les formats de date les plus courants, tels que AAAAMMJJ et AAAA-MM-JJ, n'effectue aucune analyse des spécificités régionales, ne reconnaît pas les caractères spéciaux dans les devises et ne peut pas convertir les représentations hexadécimales ou scientifiques des entiers.  
  
 L'analyse rapide est disponible uniquement lorsque vous utilisez la source de fichier plat ou la transformation de conversion de données. L'amélioration des performances pouvant être significative, pensez à utiliser si possible l'analyse rapide dans ces composants de flux de données.  
  
 Si le flux de données du package requiert une analyse des spécificités régionales, il est préférable d'utiliser l'analyse standard. Par exemple, l'analyse rapide ne reconnaît pas les données qui incluent des symboles décimaux comme la virgule, les formats de date autres que année-mois-jour ou encore les symboles de devises.  
  
 Les représentations tronquées qui laissent supposer une ou plusieurs parties de la date, comme un siècle, une année ou un mois, ne sont pas reconnues par l'analyse rapide. Par exemple, l’analyse rapide ne reconnaît pas le format '**-AAMM**', qui indique une année et un mois dans un siècle implicite, ni le format '**--MM**', qui spécifie un mois dans une année implicite. Cependant, certaines représentations avec une précision réduite sont reconnues. Ainsi, l'analyse rapide reconnaît le format 'hhmm', qui indique les heures et les minutes uniquement, et '**AAAA**', qui indique l'année uniquement.  
  
 L'analyse rapide est spécifiée au niveau de la colonne. Dans la source de fichier plat et la transformation de conversion de données, vous pouvez spécifier l'analyse rapide sur les colonnes de sortie. Les entrées et les sorties peuvent inclure des colonnes respectant des spécificités régionales et des colonnes n'en respectant pas.  
  
 Pour plus d'informations sur les formats de données pris en charge par l'analyse rapide, consultez [Numeric Data Formats](../../2014/integration-services/numeric-data-formats.md) et [Date and Time Formats](../../2014/integration-services/date-and-time-formats.md).  
  
## <a name="related-tasks"></a>Tâches associées  
 [Définir l'analyse rapide](../../2014/integration-services/set-fast-parse.md)  
  
  

---
title: Options d’instruction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- custom statement options [ODBC]
- statement options [ODBC]
- ODBC driver for Oracle [ODBC], statement options
ms.assetid: cd73b769-c8b5-43e0-9f80-b3011b7a6162
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3bf99aace8b058e429898846466294cc42612070
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948831"
---
# <a name="statement-options"></a>Options des instructions
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Ces options permettent la personnalisation d’une instruction d’exécution spécifique au sein d’une application.  
  
|Option d’instruction|Notes|  
|----------------------|-----------|  
|SQL_BIND_TYPE|Ne peut pas dépasser 2 147 483 647 octets ou la mémoire disponible.|  
|SQL_CONCURRENCY|Pour connaître les valeurs autorisées, consultez le [Type de curseur et les combinaisons d’accès concurrentiel](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_CURSOR_TYPE|Le pilote ne permet pas de type SQL_CURSOR_DYNAMIC. Consultez [SQLSetScrollOptions](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) pour plus d’informations. Pour connaître les valeurs autorisées, consultez le [Type de curseur et les combinaisons d’accès concurrentiel](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_GET_BOOKMARK|Retourne une valeur d’entier 32 bits qui est le signet pour le numéro d’enregistrement en cours. Get uniquement ; Impossible de définir.|  
|SQL_KEYSET_SIZE|Peut être définie uniquement sur 0.|  
|SQL_MAX_ROWS|Le nombre maximal de lignes à retourner à partir d’un résultat défini.|  
|SQL_ROW_NUMBER|Retourne un entier 32 bits en spécifiant la position de la ligne actuelle dans le jeu de résultats. Get uniquement ; Impossible de définir.|  
|SQL_ROWSET_SIZE|Ne peut pas dépasser 4 294 967 296 lignes ; Toutefois, vous devez disposer de suffisamment de mémoire virtuelle sur votre ordinateur pour gérer votre demande.|  
|SQL_USE_BOOKMARKS|Prend en charge la définition de SQL_USE_BOOKMARKS sur SQL_UB_ON et expose des signets de longueur fixe.|

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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948831"
---
# <a name="statement-options"></a>Options des instructions
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Ces options permettent de personnaliser une instruction d’exécution spécifique au sein d’une application.  
  
|Option d’instruction|Notes|  
|----------------------|-----------|  
|SQL_BIND_TYPE|Ne peut pas dépasser 2 147 483 647 octets ou la mémoire disponible.|  
|SQL_CONCURRENCY|Pour connaître les valeurs autorisées, consultez le [type de curseur et les combinaisons d’accès concurrentiel](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_CURSOR_TYPE|Le pilote n’autorise pas les SQL_CURSOR_DYNAMIC. Pour plus d’informations, consultez [SQLSetScrollOptions](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) . Pour connaître les valeurs autorisées, consultez le [type de curseur et les combinaisons d’accès concurrentiel](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_GET_BOOKMARK|Retourne une valeur entière de 32 bits qui est le signet du numéro d’enregistrement actuel. Obtient uniquement. Impossible de définir.|  
|SQL_KEYSET_SIZE|Peut avoir la valeur 0 uniquement.|  
|SQL_MAX_ROWS|Nombre maximal de lignes à retourner à partir d’un jeu de résultats.|  
|SQL_ROW_NUMBER|Retourne un entier 32 bits spécifiant la position de la ligne actuelle dans le jeu de résultats. Obtient uniquement. Impossible de définir.|  
|SQL_ROWSET_SIZE|Ne peut pas dépasser 4 294 967 296 lignes ; Toutefois, vous devez disposer de suffisamment de mémoire virtuelle sur votre ordinateur pour gérer votre demande.|  
|SQL_USE_BOOKMARKS|Prend en charge la définition de SQL_USE_BOOKMARKS pour SQL_UB_ON et expose des signets de longueur fixe.|

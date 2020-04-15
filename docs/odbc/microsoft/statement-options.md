---
title: Options d’énoncés (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca40765dff98e9102fbe36e88c7e79535f311d97
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299209"
---
# <a name="statement-options"></a>Options des instructions
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Ces options permettent la personnalisation d’une déclaration d’exécution spécifique au sein d’une application.  
  
|Option d’énoncé|Notes|  
|----------------------|-----------|  
|SQL_BIND_TYPE|Impossible de dépasser 2 147 483 647 octets ou mémoire disponible.|  
|SQL_CONCURRENCY|Pour les valeurs autorisées, voir le [type cursor et les combinaisons de concurrence](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_CURSOR_TYPE|Le conducteur ne permet pas SQL_CURSOR_DYNAMIC. Voir [SQLSetScrollOptions](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md) pour plus d’informations. Pour les valeurs autorisées, voir le [type cursor et les combinaisons de concurrence](../../odbc/microsoft/cursor-type-and-concurrency-combinations.md).|  
|SQL_GET_BOOKMARK|Retourne une valeur d’intégrier 32 bits qui est le signet du nombre record actuel. Obtenez seulement; ne peut pas définir.|  
|SQL_KEYSET_SIZE|Peut être réglé seulement à 0.|  
|SQL_MAX_ROWS|Le nombre maximum de lignes à revenir d’un ensemble de résultats.|  
|SQL_ROW_NUMBER|Retourne un intégré 32 bits spécifiant la position de la ligne actuelle dans l’ensemble de résultats. Obtenez seulement; ne peut pas définir.|  
|SQL_ROWSET_SIZE|Ne peut pas dépasser 4 294 967 296 rangées; cependant, vous devez avoir assez de mémoire virtuelle dans votre ordinateur pour répondre à votre demande.|  
|SQL_USE_BOOKMARKS|Prend en charge le réglage SQL_USE_BOOKMARKS à SQL_UB_ON et expose les signets fixes.|

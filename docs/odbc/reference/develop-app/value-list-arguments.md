---
title: Arguments de la liste de valeurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], value list
- value list arguments [ODBC]
ms.assetid: 863837be-603b-4c7a-8b96-b71014037ee5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fd655bd745c3bb06923e047d4134b286cf64703e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306740"
---
# <a name="value-list-arguments"></a>Arguments de liste de valeurs
Un argument de liste de valeurs se compose d’une liste de valeurs séparées par des virgules à utiliser pour la correspondance. Il n’existe qu’un seul argument de liste de valeurs dans les fonctions de catalogue ODBC : l’argument *TABLETYPE* dans **SQLTables**. Le fait de définir *TABLETYPE* sur un pointeur null est le même que s’il est défini sur SQL_ALL_TABLE_TYPES, qui énumère tous les membres possibles de la liste de valeurs. Cet argument n’est pas affecté par l’attribut d’instruction SQL_ATTR_METADATA_ID. Pour plus d’informations, consultez la description de la fonction [SQLTables](../../../odbc/reference/syntax/sqltables-function.md) .

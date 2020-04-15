---
title: Arguments de liste de valeurs (en anglais) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306740"
---
# <a name="value-list-arguments"></a>Arguments de liste de valeurs
Un argument de liste de valeurs se compose d’une liste de valeurs séparées par virgule à utiliser pour l’appariement. Il n’y a qu’un seul argument de liste de valeurs dans les fonctions de catalogue ODBC : l’argument *de TableType* dans **SQLTables**. Définir *TableType* à un pointeur nul est le même que s’il est réglé pour SQL_ALL_TABLE_TYPES, ce qui énumère tous les membres possibles de la liste de valeurs. Cet argument n’est pas influencé par l’attribut de SQL_ATTR_METADATA_ID déclaration. Pour plus d’informations, consultez la description de la fonction [SQLTables.](../../../odbc/reference/syntax/sqltables-function.md)

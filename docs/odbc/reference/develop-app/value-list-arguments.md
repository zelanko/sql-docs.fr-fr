---
title: Valeur des Arguments de la liste | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a971da68a8f2a35df8fa513e68d1eba127e9c430
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208556"
---
# <a name="value-list-arguments"></a>Arguments de liste de valeurs
Un argument de liste valeur se compose d’une liste de séparées par des virgules des valeurs à utiliser pour la correspondance. Il est argument de liste qu’une seule valeur dans les fonctions de catalogue ODBC : le *TableType* argument dans **SQLTables**. Paramètre *TableType* à un pointeur null est identique comme si elle est définie sur SQL_ALL_TABLE_TYPES, qui énumère tous les membres possibles de la liste de valeurs. Cet argument n’est pas affecté par l’attribut d’instruction SQL_ATTR_METADATA_ID. Pour plus d’informations, consultez le [SQLTables](../../../odbc/reference/syntax/sqltables-function.md) description de fonction.

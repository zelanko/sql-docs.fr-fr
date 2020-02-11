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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 646d2724489140080a673f31e22429cc7ca39d4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68022100"
---
# <a name="value-list-arguments"></a>Arguments de liste de valeurs
Un argument de liste de valeurs se compose d’une liste de valeurs séparées par des virgules à utiliser pour la correspondance. Il n’existe qu’un seul argument de liste de valeurs dans les fonctions de catalogue ODBC : l’argument *TABLETYPE* dans **SQLTables**. Le fait de définir *TABLETYPE* sur un pointeur null est le même que s’il est défini sur SQL_ALL_TABLE_TYPES, qui énumère tous les membres possibles de la liste de valeurs. Cet argument n’est pas affecté par l’attribut d’instruction SQL_ATTR_METADATA_ID. Pour plus d’informations, consultez la description de la fonction [SQLTables](../../../odbc/reference/syntax/sqltables-function.md) .

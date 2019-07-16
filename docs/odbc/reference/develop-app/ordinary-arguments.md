---
title: Arguments ordinaires | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arguments in catalog functions [ODBC], ordinary
- catalog functions [ODBC], arguments
- ordinary arguments [ODBC]
ms.assetid: a18cdae1-6b85-41cb-875c-b5a01ec90aeb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 997604b4376656d36d2bc4bc31f1959aa6c8a229
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67987828"
---
# <a name="ordinary-arguments"></a>Arguments ordinaires
Quand un argument de chaîne de fonction de catalogue est un argument ordinaire, il est traité comme une chaîne littérale. Un argument ordinaire accepte un modèle de recherche de chaîne, ni une liste de valeurs. Le cas d’un argument ordinaire est significatif et les caractères de guillemets dans la chaîne sont pris littéralement. Ces arguments sont traités en tant qu’arguments ordinaires, si l’attribut d’instruction SQL_ATTR_METADATA_ID a la valeur SQL_FALSE ; ils sont traités en tant qu’arguments de l’identificateur à la place si cet attribut a la valeur SQL_TRUE.  
  
 Si un argument ordinaire est défini sur un pointeur null et que l’argument est un argument obligatoire, la fonction retourne SQL_ERROR et SQLSTATE HY009 (utilisation non valide d’un pointeur null). Si un argument ordinaire est défini sur un pointeur null et que l’argument n’est pas un argument obligatoire, le comportement de l’argument dépend du pilote. Les arguments requis sont répertoriés dans le tableau suivant.  
  
|Fonction|Arguments requis|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*PKTableName*, *FKTableName*|  
|**SQLPrimaryKeys**|*TableName*|  
|**SQLSpecialColumns**|*TableName*|  
|**SQLStatistics**|*TableName*|

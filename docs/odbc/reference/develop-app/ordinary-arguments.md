---
description: Arguments ordinaires
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6e4e7a30efe5735aa87665d7d0247bef06390ce
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429171"
---
# <a name="ordinary-arguments"></a>Arguments ordinaires
Lorsqu’un argument de chaîne de fonction de catalogue est un argument ordinaire, il est traité comme une chaîne littérale. Un argument ordinaire n’accepte ni un modèle de recherche de chaînes, ni une liste de valeurs. Le cas d’un argument ordinaire est significatif, et les guillemets dans la chaîne sont pris littéralement. Ces arguments sont traités comme des arguments ordinaires si l’attribut d’instruction SQL_ATTR_METADATA_ID est défini sur SQL_FALSE ; ils sont traités en tant qu’arguments d’identificateur à la place si cet attribut a la valeur SQL_TRUE.  
  
 Si un argument ordinaire est défini sur un pointeur null et que l’argument est un argument obligatoire, la fonction retourne SQL_ERROR et SQLSTATE HY009 (utilisation non valide du pointeur null). Si un argument ordinaire a pour valeur un pointeur null et que l’argument n’est pas un argument obligatoire, le comportement de l’argument est dépendant du pilote. Les arguments requis sont répertoriés dans le tableau suivant.  
  
|Fonction|Arguments obligatoires|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*PKTableName*, *FKTableName*|  
|**SQLPrimaryKeys**|*TableName*|  
|**SQLSpecialColumns**|*TableName*|  
|**SQLStatistics**|*TableName*|

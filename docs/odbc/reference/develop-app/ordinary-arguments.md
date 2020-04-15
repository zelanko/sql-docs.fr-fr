---
title: Arguments ordinaires (fr) Microsoft Docs
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
ms.openlocfilehash: 97362f93e91ccd8b592b4c05a0714b7602c1ba94
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282462"
---
# <a name="ordinary-arguments"></a>Arguments ordinaires
Quand un argument de chaîne de fonction de catalogue est un argument ordinaire, il est traité comme une chaîne littérale. Un argument ordinaire n’accepte ni un modèle de recherche de cordes ni une liste de valeurs. Le cas d’un argument ordinaire est significatif, et les caractères de citation dans la chaîne sont pris littéralement. Ces arguments sont traités comme des arguments ordinaires si l’attribut de déclaration SQL_ATTR_METADATA_ID est réglé pour SQL_FALSE; ils sont traités comme des arguments d’identification à la place si cet attribut est réglé pour SQL_TRUE.  
  
 Si un argument ordinaire est réglé à un pointeur nul et que l’argument est un argument requis, la fonction renvoie SQL_ERROR et SQLSTATE HY009 (utilisation invalide du pointeur nul). Si un argument ordinaire est réglé à un pointeur nul et que l’argument n’est pas un argument requis, le comportement de l’argument est dépendant du conducteur. Les arguments requis sont énumérés dans le tableau suivant.  
  
|Fonction|Arguments requis|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*PKTableName*, *FKTableName*|  
|**SQLPrimaryKeys**|*TableName*|  
|**SQLSpecialColumns**|*TableName*|  
|**SQLStatistics**|*TableName*|

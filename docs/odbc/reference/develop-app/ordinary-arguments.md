---
title: Arguments ordinaires | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- arguments in catalog functions [ODBC], ordinary
- catalog functions [ODBC], arguments
- ordinary arguments [ODBC]
ms.assetid: a18cdae1-6b85-41cb-875c-b5a01ec90aeb
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8cba3b5cb3f9da5963045d7fd8b015be4ed9f4cf
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="ordinary-arguments"></a>Arguments ordinaires
Quand un argument de chaîne de fonction de catalogue est un argument ordinaire, il est traité comme une chaîne littérale. Un argument ordinaire n’accepte ni un modèle de recherche de chaîne, ni une liste de valeurs. Le cas d’un argument ordinaire est significatif et caractères de guillemets dans la chaîne sont prises littéralement. Ces arguments sont traités en tant qu’arguments ordinaires, si l’attribut d’instruction SQL_ATTR_METADATA_ID a la valeur SQL_FALSE ; elles sont traitées en tant qu’arguments de l’identificateur à la place si cet attribut a la valeur SQL_TRUE.  
  
 Si un argument ordinaire est défini à un pointeur null et que l’argument est un argument obligatoire, la fonction retourne SQL_ERROR et SQLSTATE HY009 (utilisation non valide d’un pointeur null). Si un argument ordinaire est défini à un pointeur null et que l’argument n’est pas un argument obligatoire, le comportement de l’argument est dépendant du pilote. Les arguments requis sont répertoriés dans le tableau suivant.  
  
|Fonction|Arguments requis|  
|--------------|------------------------|  
|**SQLColumnPrivileges**|*TableName*|  
|**SQLForeignKeys**|*PKTableName*, *FKTableName*|  
|**SQLPrimaryKeys**|*TableName*|  
|**SQLSpecialColumns**|*TableName*|  
|**SQLStatistics**|*TableName*|

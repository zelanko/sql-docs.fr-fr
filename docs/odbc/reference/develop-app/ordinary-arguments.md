---
title: Arguments ordinaires | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- arguments in catalog functions [ODBC], ordinary
- catalog functions [ODBC], arguments
- ordinary arguments [ODBC]
ms.assetid: a18cdae1-6b85-41cb-875c-b5a01ec90aeb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a97c5c7125b24239d0eaae1a75efdd65c37d7b04
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
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

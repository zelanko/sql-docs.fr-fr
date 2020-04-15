---
title: Un jeu de résultats a-t-il été créé ? | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], determining if created
ms.assetid: 4a83b8cb-2d57-4e64-b497-80bd587ee1f9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c171a154dd16a291c5dbe1dcade8c01ea95fb084
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294547"
---
# <a name="was-a-result-set-created"></a>Un jeu de résultats a-t-il été créé ?
Dans la plupart des cas, les programmeurs d’applications savent si les déclarations de leur application seront définies. C’est le cas si l’application utilise des déclarations SQL codées en dur écrites par le programmeur. C’est généralement le cas lorsque l’application construit des relevés SQL au moment de l’exécution : le programmeur peut facilement inclure du code qui indique si une déclaration **SELECT** ou une déclaration **INSERT** est en cours de construction. Dans quelques cas, le programmeur ne peut pas savoir si une déclaration créera un ensemble de résultats. Cela est vrai si l’application fournit un moyen pour l’utilisateur d’entrer et d’exécuter une déclaration SQL. Il est également vrai lorsque l’application construit une déclaration au moment de l’exécution d’une procédure.  
  
 Dans de tels cas, l’application appelle **SQLNumResultCols** pour déterminer le nombre de colonnes dans l’ensemble de résultats. Si c’est 0, la déclaration n’a pas créé un ensemble de résultats; s’il s’agit d’un autre numéro, l’instruction a créé un ensemble de résultats.  
  
 L’application peut appeler **SQLNumResultCols** à tout moment après la déclaration est préparée ou exécutée. Cependant, comme certaines sources de données ne peuvent pas facilement décrire les ensembles de résultats qui seront créés par des énoncés préparés, les performances en souffriront si **SQLNumResultCols** est appelé après qu’une déclaration ne soit préparée, mais avant qu’elle ne soit exécutée.  
  
 Certaines sources de données appuient également la détermination du nombre de lignes qu’une déclaration SQL renvoie dans un ensemble de résultats. Pour ce faire, l’application appelle **SQLRowCount**. Exactement ce que le nombre de rangées représente est indiqué par le réglage de la SQL_DYNAMIC_CURSOR_ATTRIBUTES2, SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2, SQL_KEYSET_CURSOR_ATTRIBUTES2, ou SQL_STATIC_CURSOR_ATTRIBUTES2 option (selon le type de curseur) retourné par un appel à **SQLGetInfo**. Ce bitmask indique pour chaque type de curseur si le nombre de rangées retournés est exact, approximatif, ou n’est pas disponible du tout. Que le nombre de lignes pour les curseurs statiques ou à clé soit affecté par les modifications apportées par **SQLBulkOperations** ou **SQLSetPos**, ou par mise à jour ou suppression de relevés positionnés, dépend d’autres bits retournés par les mêmes arguments d’option énumérés précédemment. Pour plus d’informations, consultez la description de la fonction [SQLGetInfo.](../../../odbc/reference/syntax/sqlgetinfo-function.md)

---
title: Paramètres de liaison par nom (Paramètres nommés) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- named parameters [ODBC]
- binding parameters by name [ODBC]
ms.assetid: e2c3da5a-6c10-4dd5-acf9-e951eea71a6b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a1e214f50488c4600ed39f76e91618cc5ce53de4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306370"
---
# <a name="binding-parameters-by-name-named-parameters"></a>Liaison de paramètres par nom (paramètres nommés)
Certains DBMS permettent à une application de spécifier les paramètres d’une procédure stockée par nom plutôt que par position dans l’appel de procédure. Ces paramètres sont appelés *paramètres nommés*. ODBC prend en charge l’utilisation de paramètres nommés. Dans ODBC, les paramètres nommés ne sont utilisés que dans les appels aux procédures stockées et ne peuvent pas être utilisés dans d’autres relevés SQL.  
  
 Le conducteur vérifie la valeur du champ SQL_DESC_UNNAMED de l’IPD pour déterminer si les paramètres désignés sont utilisés. Si SQL_DESC_UNNAMED n’est pas configuré pour SQL_UNNAMED, le conducteur utilise le nom dans le champ SQL_DESC_NAME de l’IPD pour identifier le paramètre. Pour lier le paramètre, une application peut appeler **SQLBindParameter** pour spécifier les informations de paramètres, puis peut appeler **SQLSetDescField** pour définir le champ SQL_DESC_NAME de l’IPD. Lorsque les paramètres désignés sont utilisés, l’ordre du paramètre dans l’appel de procédure n’est pas important et le numéro d’enregistrement du paramètre est ignoré.  
  
 La différence entre les paramètres anonymes et les paramètres nommés réside dans la relation entre le nombre record du descripteur et le nombre de paramètres dans la procédure. Lorsque des paramètres anonymes sont utilisés, le premier marqueur de paramètre est lié au premier enregistrement du descripteur de paramètres, qui à son tour est lié au premier paramètre (dans l’ordre de création) dans l’appel de procédure. Lorsque des paramètres désignés sont utilisés, le premier marqueur de paramètre est toujours lié au premier enregistrement du descripteur de paramètres, mais la relation entre le nombre record du descripteur et le numéro de paramètre dans la procédure n’existe plus. Les paramètres nommés n’utilisent pas la cartographie du numéro d’enregistrement du descripteur à la position de paramètre de procédure; au lieu de cela, le nom d’enregistrement descripteur est cartographié au nom du paramètre de procédure.  
  
> [!NOTE]  
>  Si la population automatique de la DPI est activée, le conducteur peuplera le descripteur de telle sorte que l’ordre des dossiers du descripteur correspond à l’ordre des paramètres dans la définition de la procédure, même si des paramètres désignés sont utilisés.  
  
 Si un paramètre désigné est utilisé, tous les paramètres doivent être nommés paramètres. Si un paramètre n’est pas un paramètre nommé, aucun des paramètres ca être nommé paramètres. S’il y avait un mélange de paramètres nommés et de paramètres anonymes, le comportement serait dépendant du conducteur.  
  
 À titre d’exemple de paramètres nommés, supposons qu’une procédure stockée par le serveur SQL ait été définie comme suit :  
  
```  
CREATE PROCEDURE test @title_id int = 1, @quote char(30) AS <blah>  
```  
  
 Dans cette procédure, le @title_idpremier paramètre, , a une valeur par défaut de 1. Une application peut utiliser le code suivant pour invoquer cette procédure de telle sorte qu’elle ne spécifie qu’un seul paramètre dynamique. Ce paramètre est un paramètre nommé avec le nom «\@citation ».  
  
```  
// Prepare the procedure invocation statement.  
SQLPrepare(hstmt, "{call test(?)}", SQL_NTS);  
  
// Populate record 1 of ipd.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,  
                  30, 0, szQuote, 0, &cbValue);  
  
// Get ipd handle and set the SQL_DESC_NAMED and SQL_DESC_UNNAMED fields  
// for record #1.  
SQLGetStmtAttr(hstmt, SQL_ATTR_IMP_PARAM_DESC, &hIpd, 0, 0);  
SQLSetDescField(hIpd, 1, SQL_DESC_NAME, "@quote", SQL_NTS);  
  
// Assuming that szQuote has been appropriately initialized,  
// execute.  
SQLExecute(hstmt);  
```

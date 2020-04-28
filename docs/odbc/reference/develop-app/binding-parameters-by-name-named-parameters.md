---
title: Liaison de paramètres par nom (paramètres nommés) | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306370"
---
# <a name="binding-parameters-by-name-named-parameters"></a>Liaison de paramètres par nom (paramètres nommés)
Certains SGBD permettent à une application de spécifier les paramètres d’une procédure stockée par nom et non par position dans l’appel de procédure. Ces paramètres sont appelés *paramètres nommés*. ODBC prend en charge l’utilisation de paramètres nommés. Dans ODBC, les paramètres nommés sont utilisés uniquement dans les appels aux procédures stockées et ne peuvent pas être utilisés dans d’autres instructions SQL.  
  
 Le pilote vérifie la valeur du champ SQL_DESC_UNNAMED de l’IPD pour déterminer si des paramètres nommés sont utilisés. Si SQL_DESC_UNNAMED n’est pas défini sur SQL_UNNAMED, le pilote utilise le nom figurant dans le champ SQL_DESC_NAME de l’IPD pour identifier le paramètre. Pour lier le paramètre, une application peut appeler **SQLBindParameter** pour spécifier les informations de paramètre, puis appeler **SQLSetDescField** pour définir le champ SQL_DESC_NAME de l’IPD. Lorsque des paramètres nommés sont utilisés, l’ordre du paramètre dans l’appel de procédure n’est pas important et le numéro d’enregistrement du paramètre est ignoré.  
  
 La différence entre les paramètres sans nom et les paramètres nommés réside dans la relation entre le numéro d’enregistrement du descripteur et le numéro de paramètre de la procédure. Lorsque des paramètres sans nom sont utilisés, le premier marqueur de paramètre est lié au premier enregistrement dans le descripteur de paramètre, qui est à son tour associé au premier paramètre (dans l’ordre de création) dans l’appel de procédure. Lorsque des paramètres nommés sont utilisés, le premier marqueur de paramètre est toujours lié au premier enregistrement du descripteur de paramètre, mais la relation entre le numéro d’enregistrement du descripteur et le numéro de paramètre de la procédure n’existe plus. Les paramètres nommés n’utilisent pas le mappage du numéro d’enregistrement du descripteur à la position du paramètre de procédure. au lieu de cela, le nom de l’enregistrement du descripteur est mappé au nom du paramètre de procédure.  
  
> [!NOTE]  
>  Si le remplissage automatique de l’IPD est activé, le pilote remplit le descripteur de telle sorte que l’ordre des enregistrements de descripteur corresponde à l’ordre des paramètres dans la définition de la procédure, même si des paramètres nommés sont utilisés.  
  
 Si un paramètre nommé est utilisé, tous les paramètres doivent être des paramètres nommés. Si un paramètre n’est pas un paramètre nommé, aucun des paramètres de l’autorité de certification n’est nommé Parameters. S’il existait un mélange de paramètres nommés et de paramètres sans nom, le comportement serait dépendant du pilote.  
  
 À titre d’exemple de paramètres nommés, supposons qu’une procédure stockée SQL Server a été définie comme suit :  
  
```  
CREATE PROCEDURE test @title_id int = 1, @quote char(30) AS <blah>  
```  
  
 Dans cette procédure, le premier paramètre, @title_id, a une valeur par défaut de 1. Une application peut utiliser le code suivant pour appeler cette procédure de façon à ce qu’elle spécifie un seul paramètre dynamique. Ce paramètre est un paramètre nommé portant le nom «\@quote ».  
  
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

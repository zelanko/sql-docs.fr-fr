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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 68dfb8976312016ee7f2e42fc4fcdecb93fd28cf
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63199377"
---
# <a name="binding-parameters-by-name-named-parameters"></a>Liaison de paramètres par nom (paramètres nommés)
Certains SGBD permettre à une application spécifier les paramètres à une procédure stockée par nom plutôt que par position dans l’appel de procédure. Ces paramètres sont appelés *des paramètres nommés*. ODBC prend en charge l’utilisation des paramètres nommés. Dans ODBC, les paramètres nommés sont utilisés uniquement dans les appels aux procédures stockées et ne peut pas être utilisés dans d’autres instructions SQL.  
  
 Le pilote vérifie la valeur du champ SQL_DESC_UNNAMED de l’IPD pour déterminer si nommé paramètres sont utilisés. Si la définition de SQL_DESC_UNNAMED n’est pas défini sur la valeur SQL_UNNAMED, le pilote utilise le nom du champ SQL_DESC_NAME de l’IPD pour identifier le paramètre. Pour lier le paramètre, une application peut appeler **SQLBindParameter** pour spécifier les informations de paramètre et peut alors appeler **SQLSetDescField** pour définir le champ SQL_DESC_NAME de l’IPD. Lorsque les paramètres nommés sont utilisés, l’ordre du paramètre dans l’appel de procédure n’est pas important et numéro d’enregistrement du paramètre est ignoré.  
  
 La différence entre les paramètres sans nom et des paramètres nommés réside dans la relation entre le numéro d’enregistrement du descripteur et le numéro de paramètre dans la procédure. Lorsque des paramètres sans nom sont utilisés, le premier marqueur de paramètre est lié au premier enregistrement dans le descripteur de paramètre, qui à son tour est lié au premier paramètre (dans l’ordre de création) dans l’appel de procédure. Lorsque les paramètres nommés sont utilisés, le premier marqueur de paramètre est toujours lié vers le premier enregistrement du descripteur de paramètre, mais la relation entre le numéro d’enregistrement du descripteur et le numéro de paramètre dans la procédure n’existe plus. Paramètres nommés n’utilisent pas le mappage de numéro d’enregistrement de descripteur à la position du paramètre de procédure ; au lieu de cela, le nom d’enregistrement de descripteur est mappé au nom du paramètre de procédure.  
  
> [!NOTE]  
>  Si le remplissage automatique de l’IPD est activé, le pilote remplira le descripteur de telle sorte que l’ordre des enregistrements de descripteur correspond à l’ordre des paramètres dans la définition de procédure, même si les paramètres nommés sont utilisés.  
  
 Si un paramètre nommé est utilisé, tous les paramètres doivent être des paramètres nommés. Si aucun paramètre n’est pas un paramètre nommé, puis none de l’autorité de certification paramètres être des paramètres nommés. Si vous rencontrez un mélange de paramètres nommés et des paramètres sans nom, le comportement serait dépendant du pilote.  
  
 Par exemple des paramètres nommés, supposons qu’un serveur SQL de procédure stockée a été définie comme suit :  
  
```  
CREATE PROCEDURE test @title_id int = 1, @quote char(30) AS <blah>  
```  
  
 Dans cette procédure, le premier paramètre, @title_id, a la valeur par défaut de 1. Une application peut utiliser le code suivant pour appeler cette procédure telle qu’elle n'indique qu’un paramètre dynamique. Ce paramètre est un paramètre nommé avec le nom «\@devis ».  
  
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

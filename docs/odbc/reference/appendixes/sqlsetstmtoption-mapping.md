---
title: Cartographie SQLSetStmtOption (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLSetStmtOption
- SQLSetStmtOption function [ODBC], mapping
ms.assetid: 6a9921aa-8a53-4668-9b13-87164062f1e5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 91264cee0dfceeb7195e2bad40d1638a88e1e01a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304900"
---
# <a name="sqlsetstmtoption-mapping"></a>SQLSetStmtOption, mappage
Lorsqu’une application appelle **SQLSetStmtOption** par l’intermédiaire d’un conducteur *ODBC 3.x,* l’appel à  
  
```  
SQLSetStmtOption(StatementHandle, fOption, vParam)  
```  
  
 résultatra comme suit :  
  
-   Si *fOption* indique un attribut de relevé défini par L’ODBC qui est une chaîne, le gestionnaire de conducteur appelle  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, SQL_NTS)  
    ```  
  
-   Si *fOption* indique un attribut de relevé défini par L’ODBC qui retourne une valeur d’intégration 32 bits, le gestionnaire de conducteur appelle  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, 0)  
    ```  
  
-   Si *fOption* indique un attribut de relevé défini par le conducteur, le gestionnaire de conducteur appelle  
  
    ```  
    SQLSetStmtAttr(StatementHandle, fOption, ValuePtr, BufferLength)  
    ```  
  
 Dans les trois cas précédents, **l’argument de StatementHandle** est réglé à la valeur en *hstmt*, *l’argument d’attribut* est réglé à la valeur dans *fOption*, et l’argument *ValuePtr* est réglé à la valeur comme *vParam*.  
  
 Étant donné que le gestionnaire de conducteur ne sait pas si l’attribut de déclaration défini par le conducteur a besoin d’une valeur d’intégrateur de chaîne ou de 32 bits, il doit passer dans une valeur valide pour *l’argument StringLength* de **SQLSetStmtAttr**. Si le conducteur a défini la sémantique spéciale pour les attributs de déclaration définis par le conducteur et doit être appelé à l’aide **de SQLSetStmtOption**, il doit prendre en charge **SQLSetStmtOption**.  
  
 Si une application appelle **SQLSetStmtOption** pour définir une option d’instruction spécifique au conducteur dans un pilote ODBC *3.x* et que l’option a été définie dans une version ODBC *2.x* du conducteur, une nouvelle constante manifeste doit être définie pour l’option dans le pilote ODBC *3.x.* Si l’ancienne constante manifeste est utilisée dans l’appel à **SQLSetStmtOption**, le Driver Manager appellera **SQLSetStmtAttr** avec *l’argument StringLength* réglé 0.  
  
 Lorsqu’une application appelle **SQLSetStmtAttr** pour SQL_ATTR_USE_BOOKMARKS pour SQL_UB_ON dans un pilote ODBC *3.x,* l’attribut de déclaration SQL_ATTR_USE_BOOKMARKS est réglé pour SQL_UB_FIXED. SQL_UB_ON est la même constante que SQL_UB_FIXED. Le Driver Manager passe SQL_UB_FIXED au conducteur. SQL_UB_FIXED a été déprécié dans ODBC *3.x*, mais un pilote ODBC *3.x* doit l’implémenter pour travailler avec ODBC *2.x* applications qui utilisent des signets de longueur fixe.  
  
 Pour un conducteur ODBC *3.x,* le gestionnaire de conducteur ne vérifie plus si *Option* est entre SQL_STMT_OPT_MIN et SQL_STMT_OPT_MAX, ou est plus grande que SQL_CONNECT_OPT_DRVR_START.

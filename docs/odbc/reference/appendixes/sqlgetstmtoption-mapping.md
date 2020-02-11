---
title: Mappage SQLGetStmtOption | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLGetStmtOption
ms.assetid: fa599517-3f3e-4dad-a65a-b8596ae3f330
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2973455ff4ee7e8dc51b2cd07a6423c9b1c36346
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68073811"
---
# <a name="sqlgetstmtoption-mapping"></a>SQLGetStmtOption, mappage
Quand une application appelle **SQLGetStmtOption** à un pilote ODBC *3. x* qui ne la prend pas en charge, l’appel à  
  
```  
SQLGetStmtOption(hstmt, fOption, pvParam)  
```  
  
 se produit comme suit :  
  
-   Si *fOption* indique une option d’instruction définie par ODBC qui retourne une chaîne, le gestionnaire de pilotes appelle  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Si *fOption* indique une option d’instruction définie par ODBC qui retourne une valeur entière de 32 bits, le gestionnaire de pilotes appelle  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Si *fOption* indique une option d’instruction définie par le pilote, le gestionnaire de pilotes appelle  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 Dans les trois cas précédents, l’argument *StatementHandle* est défini sur la valeur dans *HSTMT*, l’argument d' *attribut* est défini sur la valeur de *fOption*et l’argument *ValuePtr* est défini sur la même valeur que *pvParam*.  
  
 Pour les options de connexion de chaîne définies par ODBC, le gestionnaire de pilotes définit l’argument *BufferLength* dans l’appel à **SQLGetConnectAttr** sur la longueur maximale prédéfinie (SQL_MAX_OPTION_STRING_LENGTH); pour une option de connexion sans chaîne, *BufferLength* a la valeur 0.  
  
 L’option d’instruction SQL_GET_BOOKMARK est dépréciée dans ODBC *3. x*. Pour qu’un pilote ODBC *3. x* fonctionne avec les applications ODBC *2. x* qui utilisent SQL_GET_BOOKMARK, il doit prendre en charge les SQL_GET_BOOKMARK. Pour qu’un pilote ODBC *3. x* fonctionne avec les applications ODBC *2. x* , il doit prendre en charge la définition de SQL_USE_BOOKMARKS pour SQL_UB_ON et doit exposer des signets de longueur fixe. Si un pilote ODBC *3. x* prend en charge uniquement les signets de longueur variable, pas les signets de longueur fixe, il doit retourner SQLSTATE HYC00 (fonctionnalité facultative non implémentée) si une application ODBC *2. x* tente de définir SQL_USE_BOOKMARKS sur SQL_UB_ON.  
  
 Pour un pilote ODBC *3. x* , le gestionnaire de pilotes ne vérifie plus si l' *option* est comprise entre SQL_STMT_OPT_MIN et SQL_STMT_OPT_MAX, ou est supérieure à SQL_CONNECT_OPT_DRVR_START. Le pilote doit vérifier cela.

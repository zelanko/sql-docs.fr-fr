---
title: Sqlgetstmtoption, mappage | Microsoft Docs
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073811"
---
# <a name="sqlgetstmtoption-mapping"></a>SQLGetStmtOption, mappage
Lorsqu’une application appelle **SQLGetStmtOption** à une application ODBC *3.x* pilote qui ne prend pas en charge cela, l’appel à  
  
```  
SQLGetStmtOption(hstmt, fOption, pvParam)  
```  
  
 entraîne comme suit :  
  
-   Si *fOption* indique une option d’instruction ODBC-défini qui retourne une chaîne, les appels du Gestionnaire de pilotes  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Si *fOption* indique une option d’instruction ODBC-défini qui retourne une valeur d’entier 32 bits, les appels du Gestionnaire de pilotes  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Si *fOption* indique une option d’instruction définis par le pilote, les appels du Gestionnaire de pilotes  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 Dans les trois cas précédents, le *au paramètre StatementHandle* argument est défini à la valeur de *hstmt*, le *attribut* argument est défini à la valeur de *fOption* et le *ValuePtr* argument est défini sur la même valeur que *pvParam*.  
  
 Pour les options de connexion de chaîne définie par ODBC, le Gestionnaire de pilotes définit le *BufferLength* argument dans l’appel à **SQLGetConnectAttr** à la longueur maximale prédéfinie (SQL_MAX_OPTION_STRING_LENGTH) ; une option de connexion sans chaînes, *BufferLength* est définie sur 0.  
  
 L’option d’instruction SQL_GET_BOOKMARK a été déconseillée dans ODBC *3.x*. Pour une application ODBC *3.x* pilote fonctionne avec ODBC *2.x* les applications qui utilisent SQL_GET_BOOKMARK, il doit prendre en charge SQL_GET_BOOKMARK. Pour une application ODBC *3.x* pilote fonctionne avec ODBC *2.x* applications, il doit prendre en charge affectant SQL_USE_BOOKMARKS SQL_UB_ON et doivent exposer des signets de longueur fixe. Si une application ODBC *3.x* pilote prend en charge uniquement des signets de longueur variable, les signets de longueur pas fixe, elle doit retourner SQLSTATE HYC00 (fonctionnalité facultative non implémentée) si une application ODBC *2.x* tente d’application la valeur SQL_USE_BOOKMARKS SQL_UB_ON.  
  
 Pour une application ODBC *3.x* pilote, le Gestionnaire de pilotes ne vérifie plus pour voir si *Option* est comprise entre SQL_STMT_OPT_MIN et SQL_STMT_OPT_MAX, ou est supérieure à SQL_CONNECT_OPT_DRVR_START. Le pilote doit vérifier cela.

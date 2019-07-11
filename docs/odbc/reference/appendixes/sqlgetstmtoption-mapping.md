---
title: SQLGetStmtOption Mapping | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 98bbdcf66ed9ee8f2d716d8953fde8f4a888fca0
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792849"
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

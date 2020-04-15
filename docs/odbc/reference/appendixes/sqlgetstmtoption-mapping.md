---
title: Cartographie SQLGetStmtOption (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68819269d41407f2ce9dee172c889f7d7f286793
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300599"
---
# <a name="sqlgetstmtoption-mapping"></a>SQLGetStmtOption, mappage
Lorsqu’une demande appelle **SQLGetStmtOption** à un conducteur ODBC *3.x* qui ne la prend pas en charge, l’appel à  
  
```  
SQLGetStmtOption(hstmt, fOption, pvParam)  
```  
  
 résultatra comme suit :  
  
-   Si *fOption* indique une option d’instruction définie par ODBC qui renvoie une chaîne, le gestionnaire de conducteur appelle  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   Si *fOption* indique une option d’instruction définie par ODBC qui retourne une valeur d’intégrage 32 bits, le gestionnaire de conducteur appelle  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   Si *fOption* indique une option d’instruction définie par le conducteur, le gestionnaire de conducteur appelle  
  
    ```  
    SQLGetStmtAttr(StatementHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 Dans les trois cas précédents, *l’argument de StatementHandle* est réglé à la valeur en *hstmt*, *l’argument d’attribut* est réglé à la valeur dans *fOption*, et l’argument *ValuePtr* est réglé à la même valeur que *pvParam*.  
  
 Pour les options de connexion à cordes définies par ODBC, le gestionnaire de conducteur définit *l’argument de bufferLength* dans l’appel à **SQLGetConnectAttr** à la longueur maximale prédéfinie (SQL_MAX_OPTION_STRING_LENGTH); pour une option de connexion noncordante, *BufferLength* est réglé à 0.  
  
 L’option SQL_GET_BOOKMARK déclaration a été dépréciée dans ODBC *3.x*. Pour qu’un pilote ODBC *3.x* travaille avec des applications ODBC *2.x* qui utilisent SQL_GET_BOOKMARK, il doit prendre en charge SQL_GET_BOOKMARK. Pour qu’un pilote ODBC *3.x* travaille avec des applications ODBC *2.x,* il doit prendre en charge le réglage SQL_USE_BOOKMARKS pour SQL_UB_ON et doit exposer des signets à longueur fixe. Si un conducteur ODBC *3.x* ne prend en charge que des signets à longueur variable, et non des signets fixes, il doit retourner SQLSTATE HYC00 (fonction facultative non mise en œuvre) si une application ODBC *2.x* tente de régler SQL_USE_BOOKMARKS pour SQL_UB_ON.  
  
 Pour un conducteur ODBC *3.x,* le gestionnaire de conducteur ne vérifie plus si *Option* est entre SQL_STMT_OPT_MIN et SQL_STMT_OPT_MAX, ou est plus grande que SQL_CONNECT_OPT_DRVR_START. Le conducteur doit vérifier ça.

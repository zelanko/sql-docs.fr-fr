---
title: Cartographie SQLSetScrollOptions (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLSetScrollOptions
ms.assetid: a0fa4510-8891-4a61-a867-b2555bc35f05
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 77050df283b10abd17ba62a48bd366d6c1b3f601
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300499"
---
# <a name="sqlsetscrolloptions-mapping"></a>SQLSetScrollOptions, mappage
Lorsqu’une application appelle **SQLSetScrollOptions** par l’intermédiaire d’un conducteur ODBC *3.x* et que le conducteur ne prend pas en charge **SQLSetScrollOptions**, l’appel à  
  
```  
SQLSetScrollOptions(StatementHandle, Concurrency, KeysetSize, RowsetSize)  
```  
  
 résultatra comme suit :  
  
-   Un appel à  
  
    ```  
    SQLGetInfo(ConnectionHandle, InfoType, InfoValuePtr, BufferLength, StringLengthPtr)  
    ```  
  
     avec l’argument *InfoType* fixé à l’une des valeurs dans le tableau suivant, en fonction de la valeur de *l’argument KeysetSize* dans **SQLSetScrollOptions**.  
  
    |*KeysetSize argument*|*Argument InfoType*|  
    |---------------------------|-------------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_STATIC|SQL_STATIC_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
    |SQL_SCROLL_DYNAMIC|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
    |Une valeur supérieure à l’argument *RowsetSize*|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
  
     Si la valeur de l’argument *de KeysetSize* n’est pas indiquée dans le tableau précédent, l’appel à **SQLSetScrollOptions** renvoie SQLSTATE S1107 (valeur de la ligne hors de portée) et aucune des étapes suivantes n’est effectuée.  
  
     Le gestionnaire de conducteur vérifie ensuite si le bit approprié est fixé dans la valeur*InfoValuePtr* retourné par l’appel à **SQLGetInfo**, selon la valeur de *l’argument De concurrence* dans **SQLSetScrollOptions**.  
  
    |*Argument de concordance*|*Réglage InfoType*|  
    |----------------------------|------------------------|  
    |SQL_CONCUR_READ_ONLY|SQL_CA2_READ_ONLY_CONCURRENCY|  
    |SQL_CONCUR_LOCK|SQL_CA2_LOCK_CONCURRENCY|  
    |SQL_CONCUR_ROWVER|SQL_CA2_ROWVER_CONCURRENCY|  
    |SQL_CONCUR_VALUES|SQL_CA2_VALUES_CONCURRENCY|  
  
     Si *l’argument de la Concordence* n’est pas l’une des valeurs du tableau précédent, l’appel à **SQLSetScrollOptions** renvoie SQLSTATE S1108 (option de concordance hors de portée) et aucune des étapes suivantes n’est effectuée. Si le bit approprié (comme indiqué dans le tableau précédent) n’est pas fixé dans*l’InfoValuePtr* à l’une des valeurs correspondant à *l’argument de concurrence,* l’appel à **SQLSetScrollOptions** renvoie SQLSTATE S1C00 (Pilote non capable) et aucune des étapes suivantes n’est effectuée.  
  
-   Un appel à  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CURSOR_TYPE, ValuePtr, 0)  
    ```  
  
     * \*valuePtr* mis à l’une des valeurs dans le tableau suivant, selon la valeur de *l’argument KeysetSize* dans **SQLSetScrollOptions**.  
  
    |*KeysetSize* argument|*\*ValuePtr (en)*|  
    |---------------------------|------------------|  
    |SQL_SCROLL_FORWARD_ONLY|SQL_CURSOR_FORWARD_ONLY|  
    |SQL_SCROLL_STATIC|SQL_CURSOR_STATIC|  
    |SQL_SCROLL_KEYSET_DRIVEN|SQL_CURSOR_KEYSET_DRIVEN|  
    |SQL_SCROLL_DYNAMIC|SQL_CURSOR_DYNAMIC|  
    |Une valeur supérieure à l’argument *RowsetSize*|SQL_CURSOR_KEYSET_DRIVEN|  
  
-   Un appel à  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_CONCURRENCY, ValuePtr, 0)  
    ```  
  
     * \*valuePtr* mis à l’argument *De concurrency* dans **SQLSetScrollOptions**.  
  
-   Si l’argument *keysetSize* dans l’appel à **SQLSetScrollOptions** est positif, un appel à  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ATTR_KEYSET_SIZE, ValuePtr, 0)  
    ```  
  
     avec * \*ValuePtr* réglé à *l’argument KeysetSize* dans **SQLSetScrollOptions**.  
  
-   Un appel à  
  
    ```  
    SQLSetStmtAttr(StatementHandle, SQL_ROWSET_SIZE, ValuePtr, 0)  
    ```  
  
     avec * \*ValuePtr* réglé à l’argument *RowsetSize* dans **SQLSetScrollOptions**.  
  
    > [!NOTE]  
    >  Lorsque le gestionnaire de chauffeur cartes **SQLSetScrollOptions** pour une application de travail avec un pilote ODBC *3.x* qui ne prend pas en charge **SQLSetScrollOptions**, le gestionnaire de conducteur définit l’option de déclaration SQL_ROWSET_SIZE, et non l’attribut de déclaration SQL_ATTR_ROW_ARRAY_SIZE, à l’argument *RowsetSize* dans **SQLSetScrollOption**. Par conséquent, **SQLSetScrollOptions** ne peut pas être utilisé par une application lorsqu’il s’agit d’aller chercher plusieurs rangées par un appel à **SQLFetch** ou **SQLFetchScroll**. Il ne peut être utilisé que lorsque vous allez chercher plusieurs rangées par un appel à **SQLExtendedFetch**.

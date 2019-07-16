---
title: SQLFreeStmt, mappage | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeStmt function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeStmt
ms.assetid: 267d95f2-4f0c-47ab-9411-5afe105215a2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a92af35d8a1b1e98a484c69d7d2e66bf5bef3196
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68086081"
---
# <a name="sqlfreestmt-mapping"></a>SQLFreeStmt, mappage
Lorsqu’une application appelle **SQLFreeStmt** avec un *Option* argument de SQL_DROP via une application ODBC *3.x* pilote, l’appel à  
  
```  
SQLFreeStmt(hstmt, SQL_DROP)   
```  
  
 est mappé à  
  
```  
SQLFreeHandle(SQL_HANDLE_STMT,Handle)  
```  
  
 avec le *gérer* affectée à la valeur de l’argument *hstmt*.

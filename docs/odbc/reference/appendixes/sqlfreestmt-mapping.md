---
title: SQLFreeStmt Mapping | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 6b12c5286522bd0f1f8fbb40f101302aaa481cb8
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792602"
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

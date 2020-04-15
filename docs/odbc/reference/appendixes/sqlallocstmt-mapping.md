---
title: Cartographie SQLAllocStmt (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLAllocStmt
- SQLAllocStmt function [ODBC], mapping
ms.assetid: a2449dbb-1b6c-4b49-81b9-ebdddd4442fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 447233a3ba014a5ef92f2f49840ad302f8aeccf0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305482"
---
# <a name="sqlallocstmt-mapping"></a>SQLAllocStmt, mappage
Lorsqu’une application appelle **SQLAllocStmt** par l’intermédiaire d’un conducteur *ODBC 3.x,* l’appel à :  
  
```  
SQLAllocStmt(hdbc, phstmt)  
```  
  
 est cartographié à **SQLAllocHandle** par le gestionnaire de conducteur dans le conducteur comme suit:  
  
```  
SQLAllocHandle(SQL_HANDLE_STMT, InputHandle, OutputHandlePtr)  
```  
  
 avec *InputHandle* réglé à *hdbc* et *OutputHandlePtr* mis à *phstmt*.

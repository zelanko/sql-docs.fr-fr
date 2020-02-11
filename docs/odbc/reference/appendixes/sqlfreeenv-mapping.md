---
title: Mappage Sqlfreeenv, | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeEnv
ms.assetid: c0f76455-d072-4bae-bee7-452277dfa479
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ef89943f95a6492614972c3e89fe2129becc1aa5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086422"
---
# <a name="sqlfreeenv-mapping"></a>SQLFreeEnv, mappage
Quand une application appelle **sqlfreeenv,** via un pilote ODBC *3. x* , l’appel à  
  
```  
SQLFreeEnv(henv)   
```  
  
 est mappé à  
  
```  
SQLFreeHandle(SQL_HANDLE_ENV,Handle)  
```  
  
 avec l’argument *descripteur* défini sur la valeur dans *henv*.

---
title: SQLAllocConnect Mapping | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocConnect function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocConnect
ms.assetid: ac89dd1f-c565-47cc-8fa3-6fa5f80b5d63
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bdb63e9610d00c0736f640b6f4c4d743f3335c7d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63280979"
---
# <a name="sqlallocconnect-mapping"></a>SQLAllocConnect, mappage
Lorsqu’une application appelle **SQLAllocConnect** via un ODBC 3. *x* pilote, l’appel à **SQLAllocConnect**(*henv*, *phdbc*) est mappé à **SQLAllocHandle** comme suit :  
  
1.  Le Gestionnaire de pilotes alloue une connexion et le renvoie à l’application.  
  
2.  Lorsque l’application établit une connexion, le Gestionnaire de pilotes appelle  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     dans le pilote avec *InputHandle* définie sur *henv*, et *OutputHandlePtr* définie sur *phdbc*.

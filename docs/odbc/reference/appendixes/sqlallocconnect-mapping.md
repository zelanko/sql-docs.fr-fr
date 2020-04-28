---
title: Mappage SQLAllocConnect | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 25e72cd3830cea8504983f4348f6c200261490f4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305520"
---
# <a name="sqlallocconnect-mapping"></a>SQLAllocConnect, mappage
Quand une application appelle **SQLAllocConnect** via ODBC 3. *x* , l’appel à **SQLAllocConnect**(*henv*, *phdbc*) est mappé à **SQLAllocHandle** comme suit :  
  
1.  Le gestionnaire de pilotes alloue une connexion et le renvoie à l’application.  
  
2.  Lorsque l’application établit une connexion, le gestionnaire de pilotes appelle  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     dans le pilote avec *InputHandle* défini sur *henv*, et *OutputHandlePtr* défini sur *phdbc*.

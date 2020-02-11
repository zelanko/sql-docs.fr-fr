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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 65c23f41ea9176c460c8fb32ece5e74dfb803541
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68065022"
---
# <a name="sqlallocconnect-mapping"></a>SQLAllocConnect, mappage
Quand une application appelle **SQLAllocConnect** via ODBC 3. *x* , l’appel à **SQLAllocConnect**(*henv*, *phdbc*) est mappé à **SQLAllocHandle** comme suit :  
  
1.  Le gestionnaire de pilotes alloue une connexion et le renvoie à l’application.  
  
2.  Lorsque l’application établit une connexion, le gestionnaire de pilotes appelle  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     dans le pilote avec *InputHandle* défini sur *henv*, et *OutputHandlePtr* défini sur *phdbc*.

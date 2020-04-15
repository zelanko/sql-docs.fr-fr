---
title: Cartographie SQLAllocConnect (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305520"
---
# <a name="sqlallocconnect-mapping"></a>SQLAllocConnect, mappage
Lorsqu’une application appelle **SQLAllocConnect** par l’intermédiaire d’un ODBC 3. *x* pilote, l’appel à **SQLAllocConnect**(*henv*, *phdbc*) est cartographié à **SQLAllocHandle** comme suit:  
  
1.  Le gestionnaire de conducteur alloue une connexion et la renvoie à l’application.  
  
2.  Lorsque l’application établit une connexion, le gestionnaire de conducteur appelle  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     dans le conducteur avec *InputHandle* mis à *henv*, et *OutputHandlePtr* mis à *phdbc*.

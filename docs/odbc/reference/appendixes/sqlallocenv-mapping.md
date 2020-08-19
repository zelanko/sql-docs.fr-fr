---
description: SQLAllocEnv, mappage
title: Mappage SQLAllocEnv | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5783eaa717b5716dd6021f34b7a904ba3994759d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429511"
---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv, mappage
Quand une application appelle **SQLAllocEnv** via un pilote ODBC *3. x* , l’appel à **SQLAllocEnv**(*phenv*) est mappé à **SQLAllocHandle** comme suit :  
  
1.  Le gestionnaire de pilotes alloue un handle d’environnement et le retourne à l’application. Le gestionnaire de pilotes appelle **SQLSetEnvAttr** pour définir l’attribut d’environnement SQL_ATTR_ODBC_VERSION sur SQL_OV_ODBC2.  
  
2.  Lorsque l’application établit la première connexion à un pilote, le gestionnaire de pilotes appelle  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     dans le pilote avec *OutputHandlePtr* défini sur *phenv*.

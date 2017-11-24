---
title: Mappage de SQLAllocEnv | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1061472d46a49ca105fb970b19a2f2d950470a12
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sqlallocenv-mapping"></a>Mappage de SQLAllocEnv
Lorsqu’une application appelle **SQLAllocEnv** via un ODBC 3*.x* pilote, l’appel à **SQLAllocEnv**(*phenv*) est mappée à **SQLAllocHandle** comme suit :  
  
1.  Le Gestionnaire de pilotes alloue un handle d’environnement et le retourne à l’application. Les appels du Gestionnaire de pilotes **SQLSetEnvAttr** à la valeur de l’attribut d’environnement SQL_ATTR_ODBC_VERSION SQL_OV_ODBC2.  
  
2.  Lorsque l’application établit la première connexion à un pilote, le Gestionnaire de pilotes appelle  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     dans le pilote avec *OutputHandlePtr* la valeur *phenv*.

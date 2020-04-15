---
title: Cartographie SQLAllocEnv (fr) Microsoft Docs
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
ms.openlocfilehash: cb26e3443fabda2d6490c071b1f2668895e66b8d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304040"
---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv, mappage
Lorsqu’une application appelle **SQLAllocEnv** par l’intermédiaire d’un conducteur *ODBC 3.x,* l’appel à **SQLAllocEnv**(*phénv*) est cartographié à **SQLAllocHandle** comme suit :  
  
1.  Le gestionnaire de conducteur alloue une poignée d’environnement et la renvoie à l’application. Le Gestionnaire de chauffeur appelle **SQLSetEnvAttr** pour définir l’attribut SQL_ATTR_ODBC_VERSION environnement à SQL_OV_ODBC2.  
  
2.  Lorsque la demande établit la première connexion à un conducteur, le gestionnaire de conducteur appelle  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     dans le conducteur avec *OutputHandlePtr* mis à *phénv*.

---
title: SQLAllocEnv Mapping | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 841310d1e51084ae6a61c629b8782a8b84c665f8
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793580"
---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv, mappage
Lorsqu’une application appelle **SQLAllocEnv** via une application ODBC *3.x* pilote, l’appel à **SQLAllocEnv**(*phenv*) est mappé à **SQLAllocHandle** comme suit :  
  
1.  Le Gestionnaire de pilotes alloue un handle d’environnement et le renvoie à l’application. Les appels du Gestionnaire de pilotes **SQLSetEnvAttr** à la valeur de l’attribut d’environnement SQL_ATTR_ODBC_VERSION SQL_OV_ODBC2.  
  
2.  Lorsque l’application établit la première connexion à un pilote, le Gestionnaire de pilotes appelle  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     dans le pilote avec *OutputHandlePtr* définie sur *phenv*.

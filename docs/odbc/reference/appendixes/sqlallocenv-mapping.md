---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: afbd1404cb40408166ecfc59993db7b183ae5ed2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68065016"
---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv, mappage
Quand une application appelle **SQLAllocEnv** via un pilote ODBC *3. x* , l’appel à **SQLAllocEnv**(*phenv*) est mappé à **SQLAllocHandle** comme suit :  
  
1.  Le gestionnaire de pilotes alloue un handle d’environnement et le retourne à l’application. Le gestionnaire de pilotes appelle **SQLSetEnvAttr** pour définir l’attribut d’environnement SQL_ATTR_ODBC_VERSION sur SQL_OV_ODBC2.  
  
2.  Lorsque l’application établit la première connexion à un pilote, le gestionnaire de pilotes appelle  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     dans le pilote avec *OutputHandlePtr* défini sur *phenv*.

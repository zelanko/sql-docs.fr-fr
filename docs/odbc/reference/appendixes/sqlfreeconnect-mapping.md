---
description: SQLFreeConnect, mappage
title: Mappage Sqlfreeconnect, | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLFreeConnect
- SQLFreeConnect function [ODBC], mapping
ms.assetid: 8a844538-93c0-4709-bab6-35c45e771d80
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7ad5c2e5b1f519986ec59535699320aa8c11595c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461631"
---
# <a name="sqlfreeconnect-mapping"></a>SQLFreeConnect, mappage
Quand une application appelle **sqlfreeconnect,** via un pilote ODBC *3. x* , l’appel à  
  
```  
SQLFreeConnect(hdbc)   
```  
  
 est mappé à  
  
```  
SQLFreeHandle(SQL_HANDLE_DBC,Handle)  
```  
  
 avec l’argument *descripteur* défini sur la valeur de *hdbc*.

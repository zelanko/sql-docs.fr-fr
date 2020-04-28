---
title: SQLSetConnectOption (pilote Paradox) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLSetConnectOption
ms.assetid: 050ee2be-594e-4dbd-af67-8b6aae756cd1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 06a90a83e2cbf24e6e85a67d961684c230bca924
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301490"
---
# <a name="sqlsetconnectoption-paradox-driver"></a>SQLSetConnectOption (pilote Paradox)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Paradox. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Comment|  
|-------------|-------------|  
|SQL_ACCESS_MODE|Le SQL_ACCESS_MODE fOption peut être défini sur SQL_MODE_READ_ONLY ou SQL_MODE_READ_WRITE. Toutefois, le pilote n’empêche pas les mises à jour si SQL_ACCESS_MODE est défini sur SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Le pilote Paradox prend uniquement en charge les SQL_AUTOCOMMIT ayant la valeur ON (État par défaut), car ils ne prennent pas en charge les transactions.|  
|SQL_CURRENT_QUALIFIER|Pris en charge.|  
|SQL_LOGIN_TIMEOUT|Non pris en charge.|  
|SQL_OPT_TRACE|Pris en charge.|  
|SQL_OPT_TRACEFILE|Pris en charge.|  
|SQL_PACKET_SIZE|Non pris en charge.|  
|SQL_QUIET_MODE|Non pris en charge.|  
|SQL_TRANSLATE_DLL|Non pris en charge.|  
|SQL_TRANSLATION_OPTION|Non pris en charge.|  
|SQL_TXN_ISOLATION|Non pris en charge.|

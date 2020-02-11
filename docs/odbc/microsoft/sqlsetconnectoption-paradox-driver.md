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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0cf6d01650b86fca4c782521fe3c368f729e6b42
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67897769"
---
# <a name="sqlsetconnectoption-paradox-driver"></a>SQLSetConnectOption (pilote Paradox)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Paradox. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Commentaire|  
|-------------|-------------|  
|SQL_ACCESS_MODE|Le SQL_ACCESS_MODE fOption peut être défini sur SQL_MODE_READ_ONLY ou SQL_MODE_READ_WRITE. Toutefois, le pilote n’empêche pas les mises à jour si SQL_ACCESS_MODE est défini sur SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Le pilote Paradox prend uniquement en charge les SQL_AUTOCOMMIT ayant la valeur ON (État par défaut), car ils ne prennent pas en charge les transactions.|  
|SQL_CURRENT_QUALIFIER| Pris en charge.|  
|SQL_LOGIN_TIMEOUT|Non pris en charge.|  
|SQL_OPT_TRACE| Pris en charge.|  
|SQL_OPT_TRACEFILE| Pris en charge.|  
|SQL_PACKET_SIZE|Non pris en charge.|  
|SQL_QUIET_MODE|Non pris en charge.|  
|SQL_TRANSLATE_DLL|Non pris en charge.|  
|SQL_TRANSLATION_OPTION|Non pris en charge.|  
|SQL_TXN_ISOLATION|Non pris en charge.|

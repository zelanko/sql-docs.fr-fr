---
title: SQLSetConnectOption (pilote dBASE) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DBase driver [ODBC], SQLSetConnectOption
- SQLSetConnectOption function [ODBC], dBASE Driver
ms.assetid: b1924c33-6820-4566-b716-6897807edd0f
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 25585d7719eeb615dab2ec3f55c58b240b8e1bbc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqlsetconnectoption-dbase-driver"></a>SQLSetConnectOption (pilote dBASE)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote de dBASE. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Commentaire|  
|-------------|-------------|  
|SQL_ACCESS_MODE|La fOption SQL_ACCESS_MODE peut être définie à SQL_MODE_READ_ONLY ou SQL_MODE_READ_WRITE. Toutefois, le pilote n’empêche pas les mises à jour si SQL_ACCESS_MODE est défini sur SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Le pilote dBASE prend uniquement en charge SQL_AUTOCOMMIT définie sur (l’état par défaut), car il ne prend pas en charge les transactions.|  
|SQL_CURRENT_QUALIFIER|Pris en charge.|  
|SQL_LOGIN_TIMEOUT|Non pris en charge.|  
|SQL_OPT_TRACE|Pris en charge.|  
|SQL_OPT_TRACEFILE|Pris en charge.|  
|SQL_PACKET_SIZE|Non pris en charge.|  
|SQL_QUIET_MODE|Non pris en charge.|  
|SQL_TRANSLATE_DLL|Non pris en charge.|  
|SQL_TRANSLATION_OPTION|Non pris en charge.|  
|SQL_TXN_ISOLATION|Non pris en charge.|

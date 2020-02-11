---
title: SQLSetConnectOption (pilote Access) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLSetConnectOption
- SQLSetConnectOption function [ODBC], Access Driver
ms.assetid: 58399bc4-d0b1-4eaa-a474-c92b2d5855ea
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bea124a78e2a180180c59de3577fe1db7637e110
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67897786"
---
# <a name="sqlsetconnectoption-access-driver"></a>SQLSetConnectOption (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote d’accès. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Commentaire|  
|-------------|-------------|  
|SQL_ACCESS_MODE|Le SQL_ACCESS_MODE fOption peut être défini sur SQL_MODE_READ_ONLY ou SQL_MODE_READ_WRITE. Toutefois, le pilote n’empêche pas les mises à jour si SQL_ACCESS_MODE est défini sur SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Lorsque le pilote Microsoft Access est utilisé, l’option SQL_AUTOCOMMIT peut avoir la valeur SQL_AUTOCOMMIT_ON ou SQL_AUTOCOMMIT_OFF, car le pilote Microsoft Access prend en charge les transactions [1].|  
|SQL_CURRENT_QUALIFIER| Pris en charge.|  
|SQL_LOGIN_TIMEOUT|Non pris en charge.|  
|SQL_OPT_TRACE| Pris en charge.|  
|SQL_OPT_TRACEFILE| Pris en charge.|  
|SQL_PACKET_SIZE|Non pris en charge.|  
|SQL_QUIET_MODE|Non pris en charge.|  
|SQL_TRANSLATE_DLL|Non pris en charge.|  
|SQL_TRANSLATION_OPTION|Non pris en charge.|  
|SQL_TXN_ISOLATION|SQL_TXN_ISOLATION est toujours SQL_TXN_READ_COMMITTED.|  
  
 [1] les transactions atomiques ne sont pas prises en charge par le pilote Microsoft Access. Lors de la validation d’une transaction à l’aide du pilote Microsoft Access, il existe un délai limité entre le moment où la transaction est validée et l’heure à laquelle les valeurs sont écrites sur le disque. Ce délai est déterminé par un délai inhérent au moteur Microsoft Jet. Le délai d’attente de la page ne sera pas inférieur à une valeur minimale, même si l’option PageTimeout est définie au-dessous de cette valeur. En conséquence, il n’y a aucune garantie que les données validées sont stables, car des modifications peuvent être apportées pendant le délai.

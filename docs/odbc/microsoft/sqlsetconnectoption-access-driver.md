---
title: SQLSetConnectOption (Access Driver) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8e5f15575d34031d9886219af5677b4fc5f1d5aa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301532"
---
# <a name="sqlsetconnectoption-access-driver"></a>SQLSetConnectOption (pilote Access)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Access Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Commentaire|  
|-------------|-------------|  
|SQL_ACCESS_MODE|Le SQL_ACCESS_MODE fOption peut être réglé à SQL_MODE_READ_ONLY ou SQL_MODE_READ_WRITE. Toutefois, le conducteur n’empêche pas les mises à jour si SQL_ACCESS_MODE est configuré pour SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Lorsque le pilote Microsoft Access est utilisé, l’option SQL_AUTOCOMMIT peut être définie à SQL_AUTOCOMMIT_ON ou SQL_AUTOCOMMIT_OFF, parce que le pilote Microsoft Access prend en charge les transactions[1].|  
|SQL_CURRENT_QUALIFIER|Pris en charge.|  
|SQL_LOGIN_TIMEOUT|Non pris en charge.|  
|SQL_OPT_TRACE|Pris en charge.|  
|SQL_OPT_TRACEFILE|Pris en charge.|  
|SQL_PACKET_SIZE|Non pris en charge.|  
|SQL_QUIET_MODE|Non pris en charge.|  
|SQL_TRANSLATE_DLL|Non pris en charge.|  
|SQL_TRANSLATION_OPTION|Non pris en charge.|  
|SQL_TXN_ISOLATION|SQL_TXN_ISOLATION est toujours SQL_TXN_READ_COMMITTED.|  
  
 [1] Les transactions atomiques ne sont pas prises en charge par le pilote Microsoft Access. Lors de l’engagement d’une transaction à l’aide du pilote Microsoft Access, un délai limité existe entre le moment où la transaction est engagée et le moment où les valeurs sont écrites sur disque. Ce retard est déterminé par un retard inhérent au moteur Microsoft Jet. Le délai d’attente de page ne sera pas inférieur à une valeur minimale, même si l’option PageTimeout est définie en dessous de cette valeur. Par conséquent, il n’y a aucune garantie que les données validées sont stables, puisque des modifications peuvent être apportées pendant le délai.

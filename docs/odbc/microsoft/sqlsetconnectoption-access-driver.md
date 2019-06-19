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
manager: craigg
ms.openlocfilehash: 18950d49afdab8517b95c59df8841c33b5d3d086
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63305641"
---
# <a name="sqlsetconnectoption-access-driver"></a>SQLSetConnectOption (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations d’accès spécifiques au pilote. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|fOption|Commentaire|  
|-------------|-------------|  
|SQL_ACCESS_MODE|La fOption SQL_ACCESS_MODE peut être définie à SQL_MODE_READ_ONLY ou SQL_MODE_READ_WRITE. Toutefois, le pilote n’empêche pas les mises à jour si SQL_ACCESS_MODE est défini sur SQL_MODE_READ_ONLY.|  
|SQL_AUTOCOMMIT|Lorsque le pilote Microsoft Access est utilisé, l’option SQL_AUTOCOMMIT peut être la valeur SQL_AUTOCOMMIT_ON ou SQL_AUTOCOMMIT_OFF, étant donné que le pilote Microsoft Access prend en charge des transactions [1].|  
|SQL_CURRENT_QUALIFIER|Pris en charge.|  
|SQL_LOGIN_TIMEOUT|Non pris en charge.|  
|SQL_OPT_TRACE|Pris en charge.|  
|SQL_OPT_TRACEFILE|Pris en charge.|  
|SQL_PACKET_SIZE|Non pris en charge.|  
|SQL_QUIET_MODE|Non pris en charge.|  
|SQL_TRANSLATE_DLL|Non pris en charge.|  
|SQL_TRANSLATION_OPTION|Non pris en charge.|  
|SQL_TXN_ISOLATION|SQL_TXN_ISOLATION est toujours SQL_TXN_READ_COMMITTED.|  
  
 [1] transactions atomiques ne sont pas pris en charge par le pilote Microsoft Access. Lors de la validation d’une transaction en utilisant le pilote Microsoft Access, un délai limité existe entre l’heure de la transaction est validée et le temps que les valeurs sont écrites sur le disque. Ce délai est déterminé par un délai inhérent dans le moteur Microsoft Jet. Le délai d’expiration de la page pas sera inférieur à une valeur minimale, même si l’option PageTimeout est définie en dessous de cette valeur. Par conséquent, il est aucune garantie que la validation des données n’est stable, étant donné que les modifications peuvent être passées pendant le délai.

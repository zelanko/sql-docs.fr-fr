---
title: SQLError (le pilote ODBC Visual FoxPro) | Documents Microsoft
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
- SQLError function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8315ec16-1c22-447a-a577-39bd94f61070
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7b18b8a103df01f0ff6200b2a5630ef6dca8ae68
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complet  
  
 Conformité d’API ODBC : Niveau principal  
  
 Retourne des informations d’erreur ou d’état sur la dernière erreur. Le pilote gère une pile ou une liste d’erreurs qui peuvent être retournées pour le *hstmt*, *pas*, et *henv* arguments, selon la manière dont l’appel à **SQLError** est effectuée. La file d’attente de l’erreur est vidé après chaque instruction.  
  
 Le tableau suivant décrit les **SQLError** arguments et valeurs de retour utilisées par le pilote.  
  
|SQLError argument|Description de la valeur de retour|  
|-----------------------|------------------------------|  
|*szSQLState*|La valeur de la variable SQLSTATE représentée par l’erreur.|  
|*pfNativeError*|Une valeur différente de zéro indique un [Visual FoxPro ODBC Driver natif Message d’erreur](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md). La valeur zéro indique l’erreur a été détectée par le pilote et mappé approprié [Code d’erreur ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).|  
|*szErrorMsg*|Le texte de l’erreur native ou erreur ODBC.|  
|*pcbErrorMsg*|La longueur du texte du message ainsi que la longueur des identificateurs.|  
  
 Pour plus d’informations sur les messages d’erreur de pilote, consultez [présentation des Messages d’erreur](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md). Pour plus d’informations sur cette fonction, consultez [SQLError](../../odbc/reference/syntax/sqlerror-function.md) dans les *de référence du programmeur ODBC*.

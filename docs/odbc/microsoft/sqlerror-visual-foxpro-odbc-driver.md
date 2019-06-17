---
title: SQLError (pilote ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLError function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8315ec16-1c22-447a-a577-39bd94f61070
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3014c5c2af1a0ef8e5f485c790089e4807834446
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63313278"
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Complète  
  
 Conformité d’API ODBC : Niveau principal  
  
 Retourne des informations d’erreur ou d’état sur la dernière erreur. Le pilote gère une pile ou une liste d’erreurs qui peuvent être retournées pour le *hstmt*, *pas*, et *henv* arguments, en fonction de la l’appel à **SQLError**  est effectuée. La file d’attente de l’erreur est vidé après chaque instruction.  
  
 Le tableau suivant décrit les **SQLError** arguments et valeurs de retour utilisés par le pilote.  
  
|SQLError argument|Description de la valeur de retour|  
|-----------------------|------------------------------|  
|*szSQLState*|La valeur de la variable SQLSTATE représentée par l’erreur.|  
|*pfNativeError*|Une valeur différente de zéro indique un [Visual FoxPro ODBC pilote natif Message d’erreur](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md). La valeur zéro indique l’erreur a été détectée par le pilote et mappé appropriés [Code d’erreur ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).|  
|*szErrorMsg*|Le texte de l’erreur native ou erreur ODBC.|  
|*pcbErrorMsg*|La longueur du texte du message ainsi que la longueur des identificateurs.|  
  
 Pour plus d’informations sur les messages d’erreur de pilote, consultez [présentation des Messages d’erreur](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md). Pour plus d’informations sur cette fonction, consultez [SQLError](../../odbc/reference/syntax/sqlerror-function.md) dans le *de référence du programmeur ODBC*.

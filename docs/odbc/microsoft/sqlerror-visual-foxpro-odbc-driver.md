---
title: SQLError (Visual FoxPro ODBC Driver) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0d1247217905187cfb2dbaca6d7b7b562d0175bd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298679"
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Complet  
  
 Conformité API ODBC : Niveau de base  
  
 Renvoie les informations d’erreur ou de statut sur la dernière erreur. Le conducteur maintient une pile ou une liste d’erreurs qui peuvent être retournées pour le *hstmt*, *hdbc*, et *henv* arguments, en fonction de la façon dont l’appel à **SQLError** est faite. La file d’attente d’erreur est rincée après chaque instruction.  
  
 Le tableau suivant décrit les arguments **SQLError** et les valeurs de retour utilisées par le conducteur.  
  
|Argument DE SQLError|Description de la valeur de retour|  
|-----------------------|------------------------------|  
|*szSQLState*|La valeur pour le SQLSTATE représenté par l’erreur.|  
|*pfNativeError*|Une valeur non zéro indique un [message d’erreur native visual FoxPro ODBC Driver](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md). Une valeur de zéro indique que l’erreur a été détectée par le conducteur et cartographiée au [code d’erreur ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md)approprié .|  
|*szErrorMsg*|Le texte pour l’erreur native ou l’erreur ODBC.|  
|*pcbErrorMsg*|La durée du texte du message plus la longueur des identificateurs.|  
  
 Pour plus d’informations sur les messages d’erreur du conducteur, voir [Aperçu des messages d’erreur](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md). Pour plus d’informations sur cette fonction, voir [SQLError](../../odbc/reference/syntax/sqlerror-function.md) dans la *référence du programmeur ODBC*.

---
description: SQLError (pilote ODBC Visual FoxPro)
title: SQLError (pilote ODBC Visual FoxPro) | Microsoft Docs
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
ms.openlocfilehash: 09f901b72d292f962076bff2aa521c8214e8f0e7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340255"
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau principal  
  
 Retourne des informations d’erreur ou d’État sur la dernière erreur. Le pilote gère une pile ou une liste d’erreurs qui peuvent être retournées pour les arguments *HSTMT*, *hdbc*et *henv* , en fonction de la façon dont l’appel à **SQLError** est effectué. La file d’attente d’erreurs est vidée après chaque instruction.  
  
 Le tableau suivant décrit les arguments **SQLError** et les valeurs de retour utilisées par le pilote.  
  
|Argument SQLError|Description de la valeur de retour|  
|-----------------------|------------------------------|  
|*szSQLState*|Valeur de l’argument SQLSTATE représenté par l’erreur.|  
|*pfNativeError*|Une valeur différente de zéro indique un [message d’erreur natif du pilote ODBC Visual FoxPro](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md). La valeur zéro indique que l’erreur a été détectée par le pilote et mappée au [code d’erreur ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md)approprié.|  
|*szErrorMsg*|Texte de l’erreur native ou de l’erreur ODBC.|  
|*pcbErrorMsg*|Longueur du texte du message plus la longueur des identificateurs.|  
  
 Pour plus d’informations sur les messages d’erreur du pilote, consultez [Présentation des messages d’erreur](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md). Pour plus d’informations sur cette fonction, consultez [SQLError](../../odbc/reference/syntax/sqlerror-function.md) dans le *Guide de référence du programmeur ODBC*.

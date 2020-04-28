---
title: SQLSetConnectOption (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5a35449e-4694-4ee5-9fa1-45d5a8fe7823
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2af208663f1e91250faad0ca9538b76bcec43b06
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301500"
---
# <a name="sqlsetconnectoption-visual-foxpro-odbc-driver"></a>SQLSetConnectOption (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : partielle  
  
 Conformité de l’API ODBC : niveau 1  
  
 Définit des options qui régissent les aspects des connexions. Cette fonction est partiellement prise en charge : le pilote prend en charge toutes les valeurs pour l’argument *fOption* , mais ne prend pas en charge certaines des valeurs *vParam* pour l’argument *fOption* SQL_TXN_ISOLATION.  
  
 Le tableau suivant décrit uniquement les arguments avec un comportement spécifique à l’implémentation du pilote ODBC Visual FoxPro de **SQLSetConnectOption**.  
  
|*fOption*|Notes|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Si vous choisissez SQL_AUTOCOMMIT_OFF, votre application doit valider ou restaurer explicitement des transactions avec [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); le pilote ODBC Visual FoxPro ne valide pas automatiquement une instruction qui peut être validée après l’achèvement. Le pilote commence une transaction si l’instruction est une instruction.|  
|SQL_CURRENT_QUALIFIER|Peut être un nom [de base de données](../../odbc/microsoft/visual-foxpro-terminology.md) complet ou un chemin d’accès complet à un répertoire contenant zéro ou plusieurs [tables libres](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|SQL_LOGINTIMEOUT|Retourne l’erreur « pilote non conforme ».|  
|SQL_CURSORS|Retourne l’erreur « pilote non conforme ».|  
|SQL_PACKET_SIZE|Retourne l’erreur « pilote non conforme ».|  
|SQL_TXN_ISOLATION|Le pilote autorise uniquement SQL_TXN_READ_COMMITTED.<br /><br /> Les *vParam*s suivants ne sont pas pris en charge :<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Pour plus d’informations, consultez [SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md) dans le *Guide de référence du programmeur ODBC*.

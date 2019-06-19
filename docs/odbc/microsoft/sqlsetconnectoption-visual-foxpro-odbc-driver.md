---
title: SQLSetConnectOption (pilote ODBC de Visual FoxPro) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 398d098615a0453cb016286867836388fd817540
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63473024"
---
# <a name="sqlsetconnectoption-visual-foxpro-odbc-driver"></a>SQLSetConnectOption (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Partielle  
  
 Conformité d’API ODBC : Niveau 1  
  
 Définit les options qui régissent les aspects de connexions. Cette fonction est partiellement prises en charge : Le pilote prend en charge toutes les valeurs pour le *fOption* argument mais ne prend ne pas en charge certaines des *vParam* valeurs pour le *fOption* argument SQL_TXN_ISOLATION.  
  
 Le tableau suivant décrit uniquement les arguments avec un comportement spécifique à l’implémentation pilote ODBC Visual FoxPro de **SQLSetConnectOption**.  
  
|*fOption*|Notes|  
|---------------|-------------|  
|SQL_AUTOCOMMIT|Si vous choisissez SQL_AUTOCOMMIT_OFF, votre application doit explicitement valider ou restaurer les transactions avec [SQLTransact](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md); le pilote ODBC Visual FoxPro ne valide pas automatiquement une instruction transactable à l’achèvement. Le pilote commence une transaction si l’instruction est transactable.|  
|SQL_CURRENT_QUALIFIER|Peut être qualifié complet [base de données](../../odbc/microsoft/visual-foxpro-terminology.md) nom ou chemin d’accès complet à un répertoire contenant zéro ou plusieurs [gratuit tables](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|SQL_LOGINTIMEOUT|Retourne « Pilote non compatibles avec le » erreur.|  
|SQL_CURSORS|Retourne « Pilote non compatibles avec le » erreur.|  
|SQL_PACKET_SIZE|Retourne « Pilote non compatibles avec le » erreur.|  
|SQL_TXN_ISOLATION|Le pilote autorise uniquement SQL_TXN_READ_COMMITTED.<br /><br /> Ce qui suit *vParam*s ne sont pas prises en charge :<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
  
 Pour plus d’informations, consultez [SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md) dans le *de référence du programmeur ODBC*.

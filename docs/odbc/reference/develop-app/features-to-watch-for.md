---
title: Fonctionnalités à surveiller | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], writing interoperable applications
ms.assetid: 0fb1693b-11c3-43b1-bb16-c3323b7b2d45
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f48a3c7568a9db8b599f6d5a1997607fb16e6020
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68069882"
---
# <a name="features-to-watch-for"></a>Fonctionnalités à considérer avec attention
Cette section décrit un certain nombre de fonctionnalités qui sont souvent accordées aux développeurs d’applications. En fait, ces fonctionnalités varient largement en matière de prise en charge et de mode de prise en charge entre les SGBD. l’échec du code pour ceux-ci risque de provoquer des problèmes dans les applications interopérables.  
  
 Cette section ne répertorie pas toutes les fonctionnalités que les développeurs d’applications doivent prendre en compte. Pour plus d’informations, consultez les descriptions des fonctions [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)et [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) , [annexe C : grammaire SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)et les sections de ce manuel qui décrivent chaque fonctionnalité.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Numéro de version](../../../odbc/reference/develop-app/version-number.md)  
  
-   [Instructions et connexions multiples actives simultanément](../../../odbc/reference/develop-app/multiple-active-statements-and-connections.md)  
  
-   [Prise en charge des transactions dans les SGBD](../../../odbc/reference/develop-app/transaction-support-in-dbmss.md)  
  
-   [Comportement de validation et d’annulation](../../../odbc/reference/develop-app/commit-and-rollback-behavior.md)  
  
-   [NOT NULL dans les instructions CREATE TABLE](../../../odbc/reference/develop-app/not-null-in-create-table-statements.md)  
  
-   [Types de données pris en charge](../../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)  
  
-   [Grammaire SQL d’ODBC](../../../odbc/reference/develop-app/odbc-sql-grammar.md)  
  
-   [Traitement par lots](../../../odbc/reference/develop-app/batch-processing.md)

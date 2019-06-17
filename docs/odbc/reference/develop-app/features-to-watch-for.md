---
title: Fonctionnalités à considérer avec attention | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: fe5bce7a8a13c7296ce08f84ea4b0c60c2eb5261
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63061607"
---
# <a name="features-to-watch-for"></a>Fonctionnalités à considérer avec attention
Cette section décrit un certain nombre de fonctionnalités qui application adoptent souvent les développeurs pour reçoivent. En fait, ces fonctionnalités varient largement prise en charge et la manière de prise en charge entre les SGBD ; Échec pour qu’il est susceptible de causer des problèmes dans les applications interopérables.  
  
 Cette section ne répertorie pas toutes les fonctionnalités dont les développeurs d’applications ont besoin à prendre en compte. Pour plus d’informations, consultez le [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md), et [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) fonction descriptions, [annexe c : Grammaire SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)et les sections de ce manuel qui décrivent chaque fonction.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Numéro de version](../../../odbc/reference/develop-app/version-number.md)  
  
-   [Instructions et connexions multiples actives simultanément](../../../odbc/reference/develop-app/multiple-active-statements-and-connections.md)  
  
-   [Prise en charge des transactions dans les SGBD](../../../odbc/reference/develop-app/transaction-support-in-dbmss.md)  
  
-   [Comportement de validation et d’annulation](../../../odbc/reference/develop-app/commit-and-rollback-behavior.md)  
  
-   [NOT NULL dans les instructions CREATE TABLE](../../../odbc/reference/develop-app/not-null-in-create-table-statements.md)  
  
-   [Types de données pris en charge](../../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)  
  
-   [Grammaire SQL d’ODBC](../../../odbc/reference/develop-app/odbc-sql-grammar.md)  
  
-   [Traitement par lots](../../../odbc/reference/develop-app/batch-processing.md)

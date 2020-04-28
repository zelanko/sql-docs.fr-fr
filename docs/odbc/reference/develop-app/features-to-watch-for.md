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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 10fa5df8a47837e92d4215f558d52711a0df3440
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305680"
---
# <a name="features-to-watch-for"></a>Fonctionnalités à considérer avec attention
Cette section décrit un certain nombre de fonctionnalités qui sont souvent accordées aux développeurs d’applications. En fait, ces fonctionnalités varient largement en matière de prise en charge et de mode de prise en charge entre les SGBD. l’échec du code pour ceux-ci risque de provoquer des problèmes dans les applications interopérables.  
  
 Cette section ne répertorie pas toutes les fonctionnalités que les développeurs d’applications doivent prendre en compte. Pour plus d’informations, consultez les descriptions des fonctions [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md), [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)et [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) , [annexe C : grammaire SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)et les sections de ce manuel qui décrivent chaque fonctionnalité.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Numéro de version](../../../odbc/reference/develop-app/version-number.md)  
  
-   [Instructions et connexions multiples actives simultanément](../../../odbc/reference/develop-app/multiple-active-statements-and-connections.md)  
  
-   [Prise en charge des transactions dans les SGBD](../../../odbc/reference/develop-app/transaction-support-in-dbmss.md)  
  
-   [Comportement de validation et d’annulation](../../../odbc/reference/develop-app/commit-and-rollback-behavior.md)  
  
-   [NOT NULL dans les instructions CREATE TABLE](../../../odbc/reference/develop-app/not-null-in-create-table-statements.md)  
  
-   [Types de données pris en charge](../../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md)  
  
-   [Grammaire SQL d’ODBC](../../../odbc/reference/develop-app/odbc-sql-grammar.md)  
  
-   [Traitement par lots](../../../odbc/reference/develop-app/batch-processing.md)

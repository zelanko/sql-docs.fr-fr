---
title: SQLSetCursorName (le pilote ODBC Visual FoxPro) | Documents Microsoft
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
ms.topic: conceptual
helpviewer_keywords:
- SQLSetCursorName function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 2ac5a8b5-f084-405b-b0d7-546284dfa111
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 714e9ee12ae262eac34be684541d6ba0839ddbeb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetcursorname-visual-foxpro-odbc-driver"></a>SQLSetCursorName (le pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complet  
  
 Conformité d’API ODBC : Niveau principal  
  
 Associe un nom de curseur avec un handle d’instruction active, *hstmt*. **SQLSetCursorName** est inclus dans l’API du pilote Visual FoxPro ODBC, car il fait partie de la fonctionnalité de l’API d’ODBC niveau principale ; il ne peut pas être utilisé avec d’autres fonctions d’API, car le pilote ne prend pas en charge les mises à jour positionnées.  
  
 Pour plus d’informations, consultez [SQLSetCursorName](../../odbc/reference/syntax/sqlsetcursorname-function.md) dans les *de référence du programmeur ODBC*.

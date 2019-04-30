---
title: SQLGetFunctions (pilote ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetFunctions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8102932a-88b3-49d8-bf7a-c766f54878c0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0ae7b8eb0468dd401009ef58c83b87606b0679a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63313070"
---
# <a name="sqlgetfunctions-visual-foxpro-odbc-driver"></a>SQLGetFunctions (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Complète  
  
 Conformité d’API ODBC : Niveau 1  
  
 Retourne TRUE pour toutes les fonctions prises en charge.  
  
 Le pilote ODBC Visual FoxPro prend en charge les fonctions de toutes les API niveau principal ODBC et niveau 1. Le tableau suivant indique si le pilote prend en charge une fonction spécifique de niveau 2.  
  
|*Fonction*|Pris en charge|  
|----------------|---------------|  
|SQL_API_SQLBROWSECONNECT|Non|  
|SQL_API_SQLCOLUMNPRIVELEGES|Non|  
|SQL_API_SQLDATASOURCES|Oui|  
|SQL_API_SQLDESCRIBEPARAM|Non|  
|SQL_API_SQLDRIVERS|Oui|  
|SQL_API_SQLEXTENDEDFETCH|Oui|  
|SQL_API_SQLFOREIGNKEYS|Non|  
|SQL_API_SQLMORERESULTS|Oui|  
|SQL_API_SQLNATIVESQL|Non|  
|SQL_API_SQLNUMPARAMS|Oui|  
|SQL_API_SQLPARAMOPTIONS|Oui|  
|SQL_API_SQLPRIMARYKEYS|Oui|  
|SQL_API_SQLPROCEDURECOLUMNS|Non|  
|SQL_API_SQLPROCEDURES|Non|  
|SQL_API_SQLSETPOS|Oui|  
|SQL_API_SQLSETSCROLLOPTIONS|Oui|  
|SQL_API_SQLTABLEPRIVILEGES|Non|  
  
 Pour plus d’informations, consultez [SQLGetFunctions](../../odbc/reference/syntax/sqlgetfunctions-function.md) dans le *de référence du programmeur ODBC*.

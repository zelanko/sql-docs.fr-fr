---
description: SQLGetFunctions (pilote ODBC Visual FoxPro)
title: SQLGetFunctions (pilote ODBC Visual FoxPro) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df1413b657ec4631390525a702a625ba480e9f7e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340115"
---
# <a name="sqlgetfunctions-visual-foxpro-odbc-driver"></a>SQLGetFunctions (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau 1  
  
 Retourne la valeur TRUE pour toutes les fonctions prises en charge.  
  
 Le pilote ODBC Visual FoxPro prend en charge toutes les fonctions de base de l’API ODBC et de niveau 1. Le tableau suivant indique si le pilote prend en charge une fonction spécifique de niveau 2.  
  
|*Fonction*|Prise en charge|  
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
  
 Pour plus d’informations, consultez [SQLGetFunctions](../../odbc/reference/syntax/sqlgetfunctions-function.md) dans le *Guide de référence du programmeur ODBC*.

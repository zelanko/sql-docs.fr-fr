---
title: SQLGetTypeInfo (Visual FoxPro ODBC Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5f25e20b-a4ef-42da-aeb6-00e0510fb1cc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 23db0350f0f7271f85e2bc5c6a9e6c8767443a85
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299519"
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Complet  
  
 Conformité API ODBC: Niveau 1  
  
 Renvoie des informations sur les types de données pris en charge par une source de données. Le conducteur renvoie l’information dans un ensemble de résultats SQL. Le tableau suivant répertorie les types de données ODBC et le type de données Visual FoxPro correspondant.  
  
|Type ODBC|Type FoxPro visuel|  
|---------------|------------------------|  
|SQL_BIGINT|Non pris en charge. Il n’y a pas de type FoxPro visuel 64 bits.|  
|SQL_BIT|Logical|  
|SQL_CHAR|Caractère|  
|SQL_DATE|Date|  
|SQL_DECIMAL|Numérique|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Integer|  
|SQL_LONGVARBINARY|Mémo (binaire)|  
|SQL_LONGVARCHAR|Mémo|  
|SQL_NUMERIC|Numeric, Monnaie, Flotteur|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Integer|  
|SQL_TIME|Non pris en charge. Il n’y a pas de type *temps* FoxPro visuel.|  
|SQL_TIMESTAMP|DateTime|  
|SQL_TINYINT|Integer|  
|SQL_VARBINARY|Mémo (binaire), Général|  
|SQL_VARCHAR|Caractère|  
  
 Type par défaut  
  
 Pour plus d’informations sur les types de données Visual FoxPro, voir [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md). Pour plus d’informations sur cette fonction, voir [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md) dans la *référence du programmeur ODBC*.

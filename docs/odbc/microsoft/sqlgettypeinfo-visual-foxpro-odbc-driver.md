---
title: SQLGetTypeInfo (pilote ODBC de Visual FoxPro) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05cc6dc2647b5297b8d7176cd4bc70261b78cb71
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181416"
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : Complète  
  
 Conformité d’API ODBC : Niveau 1  
  
 Retourne des informations sur les types de données pris en charge par une source de données. Le pilote retourne les informations dans un jeu de résultats SQL. Le tableau suivant répertorie les types de données ODBC et le type de données Visual FoxPro.  
  
|Type ODBC|Type de Visual FoxPro|  
|---------------|------------------------|  
|SQL_BIGINT|Non pris en charge. Il n’existe aucun type de Visual FoxPro 64 bits.|  
|SQL_BIT|Logical|  
|SQL_CHAR|Caractère|  
|SQL_DATE|Date|  
|SQL_DECIMAL|Numeric|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Entier|  
|SQL_LONGVARBINARY|Mémo (binaire)|  
|SQL_LONGVARCHAR|Mémo|  
|SQL_NUMERIC|Numérique *, devise, Float|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Entier|  
|SQL_TIME|Non pris en charge. Il n’existe aucun Visual FoxPro *temps* type.|  
|SQL_TIMESTAMP|DateTime|  
|SQL_TINYINT|Entier|  
|SQL_VARBINARY|Mémo (binaire) *, général|  
|SQL_VARCHAR|Caractère|  
  
 \* Type par défaut  
  
 Pour plus d’informations sur les types de données Visual FoxPro, consultez [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md). Pour plus d’informations sur cette fonction, consultez [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md) dans le *de référence du programmeur ODBC*.

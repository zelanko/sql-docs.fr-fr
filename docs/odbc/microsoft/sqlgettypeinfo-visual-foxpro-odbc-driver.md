---
title: SQLGetTypeInfo (pilote ODBC Visual FoxPro) | Microsoft Docs
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "81299519"
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Cette rubrique contient des informations spécifiques au pilote ODBC Visual FoxPro. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Prise en charge : complète  
  
 Conformité de l’API ODBC : niveau 1  
  
 Retourne des informations sur les types de données pris en charge par une source de données. Le pilote retourne les informations dans un jeu de résultats SQL. Le tableau suivant répertorie les types de données ODBC et le type de données Visual FoxPro correspondant.  
  
|Type ODBC|Type Visual FoxPro|  
|---------------|------------------------|  
|SQL_BIGINT|Non pris en charge. Il n’existe pas de type Visual FoxPro 64 bits.|  
|SQL_BIT|Logical|  
|SQL_CHAR|Caractère|  
|SQL_DATE|Date|  
|SQL_DECIMAL|Numérique|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Integer|  
|SQL_LONGVARBINARY|Mémo (binaire)|  
|SQL_LONGVARCHAR|Mémo|  
|SQL_NUMERIC|Numérique *, devise, virgule flottante|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Integer|  
|SQL_TIME|Non pris en charge. Il n’existe aucun type de *temps* Visual FoxPro.|  
|SQL_TIMESTAMP|DateTime|  
|SQL_TINYINT|Integer|  
|SQL_VARBINARY|MEMO (binaire) *, General|  
|SQL_VARCHAR|Caractère|  
  
 * Type par défaut  
  
 Pour plus d’informations sur les types de données Visual FoxPro, consultez [Create table](../../odbc/microsoft/create-table-sql-command.md). Pour plus d’informations sur cette fonction, consultez [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md) dans le *Guide de référence du programmeur ODBC*.

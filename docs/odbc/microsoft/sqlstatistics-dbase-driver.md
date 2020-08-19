---
description: SQLStatistics (pilote dBASE)
title: SQLStatistics (pilote dBASE) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLStatistics function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLStatistics
ms.assetid: 631cec1b-66b7-4103-b9a7-ffd81da3c442
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9285f78bbafb7594e3a9cbab2845cedeff0c1af9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421563"
---
# <a name="sqlstatistics-dbase-driver"></a>SQLStatistics (pilote dBASE)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote dBASE. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Colonne|Commentaires|  
|------------|--------------|  
|TABLE_QUALIFIER|Chemin d’accès à un répertoire.<br /><br /> Les critères spéciaux ne sont pas pris en charge dans l’argument *szTableQualifier* .|  
|TABLE_OWNER|La valeur NULL est retournée dans cette colonne, car le nom du propriétaire n’est pas pris en charge.|  
|TABLE_NAME|Nom de table sans délimiteur.<br /><br /> Les critères spéciaux ne sont pas pris en charge dans l’argument *szTableName* .|  
|INDEX_QUALIFIER|NULL est toujours retourné.|  
|INDEX_NAME|Dépendant de l’index.|  
|TYPE|Seul SQL_TABLE_STAT ou SQL_INDEX_OTHER sera retourné pour le TYPE.|  
|SEQ_IN_INDEX|Dépendant de l’index.|  
|COLUMN_NAME|Dépendant de l’index.|  
|COLLATION|Dépendant de l’index.|  
|PAGES|NULL est toujours retourné.|  
  
 Le filtrage est basé sur l’unicité (l’argument *fUnique* ). Le paramètre *fAccuracy* est ignoré.

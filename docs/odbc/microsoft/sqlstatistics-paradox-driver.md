---
description: SQLStatistics (pilote Paradox)
title: SQLStatistics (pilote Paradox) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Paradox driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Paradox Driver
ms.assetid: 886cab83-d599-4fbc-9c88-e8cb833aac4b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc76e6d2b076a9188850f9a41124311fd2658814
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421553"
---
# <a name="sqlstatistics-paradox-driver"></a>SQLStatistics (pilote Paradox)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Paradox. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
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

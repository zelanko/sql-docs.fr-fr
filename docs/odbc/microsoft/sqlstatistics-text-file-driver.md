---
title: SQLStatistics (pilote de fichier texte) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Text File Driver
ms.assetid: 311afc01-d656-425f-be43-4a8e7cbc9a97
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 76b9810236b4ec415f8abb8ecefca748c13b51c8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299309"
---
# <a name="sqlstatistics-text-file-driver"></a>SQLStatistics (pilote de fichier texte)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote de fichier texte. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
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

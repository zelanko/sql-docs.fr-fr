---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d60296a73367b4718c4da5df036befa0cd34b505
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114370"
---
# <a name="sqlstatistics-paradox-driver"></a>SQLStatistics (pilote Paradox)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Paradox. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|colonne|Commentaires|  
|------------|--------------|  
|TABLE_QUALIFIER|Le chemin d’accès à un répertoire.<br /><br /> Critères spéciaux n’est pas pris en charge dans les *szTableQualifier* argument.|  
|TABLE_OWNER|Valeur NULL est retournée dans cette colonne, car le nom du propriétaire n’est pas pris en charge.|  
|TABLE_NAME|Nom de la table sans délimitation.<br /><br /> Critères spéciaux n’est pas pris en charge dans les *szTableName* argument.|  
|INDEX_QUALIFIER|Toujours la valeur NULL est retournée.|  
|INDEX_NAME|Index dépendant.|  
|TYPE|Uniquement SQL_TABLE_STAT ou SQL_INDEX_OTHER s’affichera pour le TYPE.|  
|SEQ_IN_INDEX|Index dépendant.|  
|COLUMN_NAME|Index dépendant.|  
|COLLATION|Index dépendant.|  
|PAGES|Toujours la valeur NULL est retournée.|  
  
 De filtrage est basé sur l’unicité (le *fUnique* argument). Le *fAccuracy* paramètre est ignoré.

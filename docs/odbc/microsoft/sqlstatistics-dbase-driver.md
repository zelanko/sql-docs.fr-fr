---
title: SQLStatistics (pilote dBASE) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLStatistics function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLStatistics
ms.assetid: 631cec1b-66b7-4103-b9a7-ffd81da3c442
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 29d7759aa941a04014a3ed87ac75c5794ef2ad29
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlstatistics-dbase-driver"></a>SQLStatistics (pilote dBASE)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote de dBASE. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Colonne|Commentaires|  
|------------|--------------|  
|TABLE_QUALIFIER|Le chemin d’accès à un répertoire.<br /><br /> Recherche de correspondance n’est pas pris en charge dans les *szTableQualifier* argument.|  
|TABLE_OWNER|Valeur NULL est retournée dans cette colonne, car le nom du propriétaire n’est pas pris en charge.|  
|TABLE_NAME|Nom de table et sans délimitation.<br /><br /> Recherche de correspondance n’est pas pris en charge dans les *szTableName* argument.|  
|INDEX_QUALIFIER|NULL est toujours retournée.|  
|INDEX_NAME|Index dépendant.|  
|TYPE|Uniquement SQL_TABLE_STAT ou SQL_INDEX_OTHER sera retourné pour le TYPE.|  
|SEQ_IN_INDEX|Index dépendant.|  
|COLUMN_NAME|Index dépendant.|  
|COLLATION|Index dépendant.|  
|PAGES|NULL est toujours retournée.|  
  
 Le filtrage est basé sur l’unicité (le *fUnique* argument). Le *fAccuracy* paramètre est ignoré.


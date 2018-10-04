---
title: SQLStatistics (pilote Access) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Access Driver
ms.assetid: 6117ac77-1020-4f0c-8eed-e671c34c1f21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bc5a354aeaf186b4baeabd96e7424939fe463bfb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47777417"
---
# <a name="sqlstatistics-access-driver"></a>SQLStatistics (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations d’accès spécifiques au pilote. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|colonne|Commentaires|  
|------------|--------------|  
|TABLE_QUALIFIER|Le chemin d’accès à un fichier de base de données est retournée pour Microsoft Access.<br /><br /> Critères spéciaux n’est pas pris en charge dans les *szTableQualifier* argument.|  
|TABLE_OWNER|Valeur NULL est retournée dans cet article, car le nom du propriétaire n’est pas pris en charge.|  
|TABLE_NAME|Nom de la table sans délimitation.<br /><br /> Critères spéciaux n’est pas pris en charge dans les *szTableName* argument.|  
|INDEX_QUALIFIER|Toujours la valeur NULL est retournée.|  
|INDEX_NAME|Index dépendant.|  
|TYPE|Uniquement SQL_TABLE_STAT ou SQL_INDEX_OTHER s’affichera pour le TYPE.|  
|SEQ_IN_INDEX|Index dépendant.|  
|COLUMN_NAME|Index dépendant.|  
|COLLATION|Index dépendant.|  
|CARDINALITY|Retournée uniquement pour Microsoft Access.|  
|PAGES|Toujours la valeur NULL est retournée.|  
  
 De filtrage est basé sur l’unicité (le *fUnique* argument). Le *fAccuracy* paramètre est ignoré.

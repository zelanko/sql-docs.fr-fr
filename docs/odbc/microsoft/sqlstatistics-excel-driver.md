---
title: SQLStatistics (Excel Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLStatistics
- SQLStatistics function [ODBC], Excel Driver
ms.assetid: 02506664-8dcc-4bd0-a8bb-d49fcbdd5722
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 51b7e59fa811dd7b4ac69f1e9c8d39b4d482c437
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299339"
---
# <a name="sqlstatistics-excel-driver"></a>SQLStatistics (pilote Excel)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Excel Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Colonne|Commentaires|  
|------------|--------------|  
|TABLE_QUALIFIER|Le chemin vers un répertoire.<br /><br /> L’appariement de modèle n’est pas pris en charge dans *l’argument szTableQualifier.*|  
|TABLE_OWNER|NULL est retourné dans cette colonne parce que le nom du propriétaire n’est pas pris en charge.|  
|TABLE_NAME|Nom de table nonimidé.<br /><br /> L’appariement des motifs n’est pas pris en charge dans *l’argument szTableName.*|  
|INDEX_QUALIFIER|NULL est toujours retourné.|  
|INDEX_NAME|Index-dépendant.|  
|TYPE|Seuls SQL_TABLE_STAT ou SQL_INDEX_OTHER seront retournés pour TYPE.|  
|SEQ_IN_INDEX|Index-dépendant.|  
|COLUMN_NAME|Index-dépendant.|  
|COLLATION|Index-dépendant.|  
|PAGES|NULL est toujours retourné.|  
  
 Le filtrage est basé sur l’unicité *(l’argument fUnique).* Le *paramètre fAccuracy* est ignoré.

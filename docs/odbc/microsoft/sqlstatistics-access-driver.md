---
title: SQLStatistics (Access Driver) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f75f41bf63cbf224772955effa0f120b5d384111
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299359"
---
# <a name="sqlstatistics-access-driver"></a>SQLStatistics (pilote Access)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Access Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Colonne|Commentaires|  
|------------|--------------|  
|TABLE_QUALIFIER|Le chemin vers un fichier de base de données est retourné pour Microsoft Access.<br /><br /> L’appariement de modèle n’est pas pris en charge dans *l’argument szTableQualifier.*|  
|TABLE_OWNER|NULL est retourné dans cette colonne, parce que le nom du propriétaire n’est pas pris en charge.|  
|TABLE_NAME|Nom de table nonimidé.<br /><br /> L’appariement des motifs n’est pas pris en charge dans *l’argument szTableName.*|  
|INDEX_QUALIFIER|NULL est toujours retourné.|  
|INDEX_NAME|Index-dépendant.|  
|TYPE|Seuls SQL_TABLE_STAT ou SQL_INDEX_OTHER seront retournés pour TYPE.|  
|SEQ_IN_INDEX|Index-dépendant.|  
|COLUMN_NAME|Index-dépendant.|  
|COLLATION|Index-dépendant.|  
|CARDINALITY|Retourné pour Microsoft Access uniquement.|  
|PAGES|NULL est toujours retourné.|  
  
 Le filtrage est basé sur l’unicité *(l’argument fUnique).* Le *paramètre fAccuracy* est ignoré.

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
ms.openlocfilehash: 523f44924858af182e953aa1ce2b72e20cf97a45
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68047078"
---
# <a name="sqlstatistics-access-driver"></a>SQLStatistics (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote d’accès. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Colonne|Commentaires|  
|------------|--------------|  
|TABLE_QUALIFIER|Le chemin d’accès à un fichier de base de données est retourné pour Microsoft Access.<br /><br /> Les critères spéciaux ne sont pas pris en charge dans l’argument *szTableQualifier* .|  
|TABLE_OWNER|La valeur NULL est retournée dans cette colonne, car le nom du propriétaire n’est pas pris en charge.|  
|TABLE_NAME|Nom de table sans délimiteur.<br /><br /> Les critères spéciaux ne sont pas pris en charge dans l’argument *szTableName* .|  
|INDEX_QUALIFIER|NULL est toujours retourné.|  
|INDEX_NAME|Dépendant de l’index.|  
|TYPE|Seul SQL_TABLE_STAT ou SQL_INDEX_OTHER sera retourné pour le TYPE.|  
|SEQ_IN_INDEX|Dépendant de l’index.|  
|COLUMN_NAME|Dépendant de l’index.|  
|COLLATION|Dépendant de l’index.|  
|CARDINALITY|Retourné pour Microsoft Access uniquement.|  
|PAGES|NULL est toujours retourné.|  
  
 Le filtrage est basé sur l’unicité (l’argument *fUnique* ). Le paramètre *fAccuracy* est ignoré.

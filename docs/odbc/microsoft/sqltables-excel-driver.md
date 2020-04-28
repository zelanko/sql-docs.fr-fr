---
title: SQLTables (pilote Excel) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLTables
- SQLTables function [ODBC], Excel Driver
ms.assetid: 9410b686-4b5b-4b51-b5ef-f9d2e7a48faa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c436a1f52a862cda753d8c043515f5584607d98c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299299"
---
# <a name="sqltables-excel-driver"></a>SQLTables (pilote Excel)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Excel. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner*|Le seul argument valide pour *szTableOwner* est null, car aucun des pilotes ne prend en charge les noms de propriétaire. Si *szTableOwner* a la valeur null, toutes les tables sont retournées. La valeur NULL est retournée dans la colonne TABLE_OWNER.|  
|*szTableQualifier*|Lorsque le pilote Microsoft Excel 3,0 ou 4,0 est utilisé, si vous appelez **SQLTables** avec une valeur pour *szTableQualifier* qui n’est pas le nom d’une table existante, le pilote crée une table portant ce nom.<br /><br /> Dans la colonne TABLE_QUALIFIER, **SQLTables** retourne le chemin d’accès à un répertoire.|  
|*SzTableType*|Pour Microsoft Excel 3,0 ou 4,0, « TABLE » est le seul type de table pris en charge.<br /><br /> Pour les versions ultérieures des fichiers Microsoft Excel, la « TABLE système » est retournée pour les noms de feuille (tables avec un « $ » à la fin) et « TABLE » est retourné pour les tables dans les feuilles de calcul.|

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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 89157178aa9c134bdb1b9518343007adb1e1e05f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68132422"
---
# <a name="sqltables-excel-driver"></a>SQLTables (pilote Excel)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Excel. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner*|Le seul argument valide pour *szTableOwner* est null, car aucun des pilotes ne prend en charge les noms de propriétaire. Si *szTableOwner* a la valeur null, toutes les tables sont retournées. La valeur NULL est retournée dans la colonne TABLE_OWNER.|  
|*szTableQualifier*|Lorsque le pilote Microsoft Excel 3,0 ou 4,0 est utilisé, si vous appelez **SQLTables** avec une valeur pour *szTableQualifier* qui n’est pas le nom d’une table existante, le pilote crée une table portant ce nom.<br /><br /> Dans la colonne TABLE_QUALIFIER, **SQLTables** retourne le chemin d’accès à un répertoire.|  
|*SzTableType*|Pour Microsoft Excel 3,0 ou 4,0, « TABLE » est le seul type de table pris en charge.<br /><br /> Pour les versions ultérieures des fichiers Microsoft Excel, la « TABLE système » est retournée pour les noms de feuille (tables avec un « $ » à la fin) et « TABLE » est retourné pour les tables dans les feuilles de calcul.|

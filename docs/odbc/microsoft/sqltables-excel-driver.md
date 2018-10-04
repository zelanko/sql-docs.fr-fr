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
manager: craigg
ms.openlocfilehash: 23ce67350b7fa7d0a88f3d51e618ce9bb9f9ebcf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796217"
---
# <a name="sqltables-excel-driver"></a>SQLTables (pilote Excel)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Excel. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner*|Le seul argument valide pour *szTableOwner* a la valeur NULL, car aucun des pilotes prend en charge les noms de propriétaire. Avec *szTableOwner* la valeur NULL, toutes les tables sont retournées. Dans la colonne TABLE_OWNER la valeur NULL est retournée.|  
|*szTableQualifier*|Lorsque Microsoft Excel 3.0 ou 4.0 pilote sert, si vous appelez **SQLTables** avec une valeur pour *szTableQualifier* qui n’est pas le nom d’une table existante, le pilote crée une table portant ce nom.<br /><br /> Dans la colonne TABLE_QUALIFIER, **SQLTables** retourne le chemin d’accès à un répertoire.|  
|*SzTableType*|Pour Microsoft Excel 3.0 ou 4.0, « TABLE » est le seul type de table pris en charge.<br /><br /> Pour les versions ultérieures des fichiers Microsoft Excel, « TABLE système » est retournée pour les noms de feuille (tables par « $» à la fin) et « TABLE » est retournée pour les tables dans des feuilles de calcul.|

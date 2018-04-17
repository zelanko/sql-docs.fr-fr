---
title: SQLTables (pilote Excel) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Excel driver [ODBC], SQLTables
- SQLTables function [ODBC], Excel Driver
ms.assetid: 9410b686-4b5b-4b51-b5ef-f9d2e7a48faa
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9f7dbfc5174b832b5878096868bc2498105ae212
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqltables-excel-driver"></a>SQLTables (pilote Excel)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Excel. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner*|Le seul argument valide pour *szTableOwner* a la valeur NULL, car aucun des pilotes prend en charge les noms de propriétaire. Avec *szTableOwner* la valeur NULL, toutes les tables sont retournées. NULL est retourné dans la colonne TABLE_OWNER.|  
|*szTableQualifier*|Lorsque Microsoft Excel 3.0 ou 4.0 pilote sert, si vous appelez **SQLTables** avec une valeur pour *szTableQualifier* qui n’est pas le nom d’une table existante, le pilote crée une table portant ce nom.<br /><br /> Dans la colonne TABLE_QUALIFIER, **SQLTables** retourne le chemin d’accès à un répertoire.|  
|*SzTableType*|Pour Microsoft Excel 3.0 ou 4.0, « TABLE » est le seul type de table pris en charge.<br /><br /> Pour les versions ultérieures des fichiers Microsoft Excel, « TABLE système » est retournée pour les noms de feuille (tables avec un « $» à la fin) et « TABLE » est retournée pour les tables dans des feuilles de calcul.|

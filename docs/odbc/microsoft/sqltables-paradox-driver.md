---
title: SQLTables (pilote Paradox) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Paradox driver [ODBC], SQLTables
- SQLTables function [ODBC], Paradox Driver
ms.assetid: d68adad6-97bd-4b47-bcf9-0102aafb00d4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c845bd2e5e3ec5e52cfd6d1c0891f8825af1e148
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62735196"
---
# <a name="sqltables-paradox-driver"></a>SQLTables (pilote Paradox)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Paradox. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner*|Le seul argument valide pour *szTableOwner* a la valeur NULL, car aucun des pilotes prend en charge les noms de propriétaire. Avec *szTableOwner* la valeur NULL, toutes les tables sont retournées. Dans la colonne TABLE_OWNER la valeur NULL est retournée.|  
|*szTableQualifier*|Dans la colonne TABLE_QUALIFIER, **SQLTables** retourne le chemin d’accès à un répertoire.|  
|*SzTableType*|Pour les fichiers Paradox, « TABLE » est le seul type de table pris en charge.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQLTables, fonction](../../odbc/reference/syntax/sqltables-function.md)

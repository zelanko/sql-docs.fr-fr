---
title: SQLTables (pilote Paradox) | Documents Microsoft
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
- Paradox driver [ODBC], SQLTables
- SQLTables function [ODBC], Paradox Driver
ms.assetid: d68adad6-97bd-4b47-bcf9-0102aafb00d4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: df4a9a3c8543b3ae9c89eeb79795f51a62bd45a3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqltables-paradox-driver"></a>SQLTables (pilote Paradox)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote de Corel. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner*|Le seul argument valide pour *szTableOwner* a la valeur NULL, car aucun des pilotes prend en charge les noms de propriétaire. Avec *szTableOwner* la valeur NULL, toutes les tables sont retournées. NULL est retourné dans la colonne TABLE_OWNER.|  
|*szTableQualifier*|Dans la colonne TABLE_QUALIFIER, **SQLTables** retourne le chemin d’accès à un répertoire.|  
|*SzTableType*|Pour les fichiers Paradox, « TABLE » est le seul type de table pris en charge.|  
  
## <a name="see-also"></a>Voir aussi  
 [SQLTables, fonction](../../odbc/reference/syntax/sqltables-function.md)

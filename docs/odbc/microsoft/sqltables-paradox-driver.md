---
title: SQLTables (Pilote Paradox) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aa13b5395d8f3c2cb470a4eff1b1ef02a43bad53
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299285"
---
# <a name="sqltables-paradox-driver"></a>SQLTables (pilote Paradox)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Paradox Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner (en)*|Le seul argument valable pour *szTableOwner* est NULL parce qu’aucun des noms de propriétaire de soutien des conducteurs. Avec *szTableOwner* réglé à NULL, toutes les tables sont retournées. NULL est retourné dans la colonne TABLE_OWNER.|  
|*szTableQualifier*|Dans la colonne TABLE_QUALIFIER, **SQLTables** retournera le chemin à un répertoire.|  
|*SzTableType (en)*|Pour les fichiers Paradox, "TABLE" est le seul type de table pris en charge.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLTables](../../odbc/reference/syntax/sqltables-function.md)

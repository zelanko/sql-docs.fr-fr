---
title: SQLTables (Chauffeur d’accès) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Access Driver
- Access driver [ODBC], SQLTables
ms.assetid: 94423cf9-341a-4db6-bb10-8f5448df7fc3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df3a23af365efbef6a0f0da2c52568501425ecb3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306090"
---
# <a name="sqltables-access-driver"></a>SQLTables (pilote Access)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Access Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner (en)*|Le seul argument valable pour *szTableOwner* est NULL parce qu’aucun des noms de propriétaire de soutien des conducteurs. Avec *szTableOwner* réglé à NULL, toutes les tables sont retournées. NULL est retourné dans la colonne TABLE_OWNER.|  
|*szTableQualifier*|Dans la colonne TABLE_QUALIFIER, **SQLTables** retournera le chemin vers un fichier de base de données.|  
|*SzTableType (en)*|Lorsque le pilote Microsoft Access est utilisé, "SYSTEM TABLE" est pris en charge pour *szTableType* pour les tables système, "SYNONYM" est pris en charge pour les tables jointes, et "VIEW" est pris en charge pour les requêtes de retour en ligne.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLTables](../../odbc/reference/syntax/sqltables-function.md)

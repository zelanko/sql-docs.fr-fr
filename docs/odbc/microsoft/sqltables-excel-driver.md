---
title: SQLTables (Excel Driver) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299299"
---
# <a name="sqltables-excel-driver"></a>SQLTables (pilote Excel)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques à Excel Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner (en)*|Le seul argument valable pour *szTableOwner* est NULL parce qu’aucun des noms de propriétaire de soutien des conducteurs. Avec *szTableOwner* réglé à NULL, toutes les tables sont retournées. NULL est retourné dans la colonne TABLE_OWNER.|  
|*szTableQualifier*|Lorsque le pilote Microsoft Excel 3.0 ou 4.0 est utilisé, si vous appelez **SQLTables** avec une valeur pour *szTableQualifier qui n’est* pas le nom d’une table existante, le pilote va créer une table avec ce nom.<br /><br /> Dans la colonne TABLE_QUALIFIER, **SQLTables** retournera le chemin à un répertoire.|  
|*SzTableType (en)*|Pour Microsoft Excel 3.0 ou 4.0, "TABLE" est le seul type de table pris en charge.<br /><br /> Pour les versions ultérieures des fichiers Microsoft Excel, "SYSTEM TABLE" est retourné pour les noms de feuilles (tables avec un "$" à la fin), et "TABLE" est retourné pour les tables dans les feuilles de travail.|

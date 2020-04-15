---
title: SQLTables (Text File Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLTables
- SQLTables function [ODBC], Text File Driver
ms.assetid: f47fd1a4-5bd8-4b2e-8ae3-e595e49f4f95
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 938ceba5da25d176628d5c1d9875383d977e3aec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299329"
---
# <a name="sqltables-text-file-driver"></a>SQLTables (pilote de fichier texte)
> [!NOTE]  
>  Ce sujet fournit des informations spécifiques au fichier texte. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner (en)*|Le seul argument valable pour *szTableOwner* est NULL parce qu’aucun des noms de propriétaire de soutien des conducteurs. Avec *szTableOwner* réglé à NULL, toutes les tables sont retournées. NULL est retourné dans la colonne TABLE_OWNER.|  
|*szTableQualifier*|Dans la colonne TABLE_QUALIFIER, **SQLTables** retournera le chemin à un répertoire.|  
|*SzTableType (en)*|"TABLE" est le seul type de table pris en charge.<br /><br /> Lorsque le pilote de texte est utilisé, la liste des fichiers retournés par **SQLTables** est déterminée par les extensions de fichiers dans la boîte **de liste d’extensions** dans la boîte de dialogue **ODBC Text Setup.**|

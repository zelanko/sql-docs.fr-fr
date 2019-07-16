---
title: SQLTables (pilote de fichier texte) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7fcdf9cc41a55d1e529001ae7183ef9fa833363b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67949015"
---
# <a name="sqltables-text-file-driver"></a>SQLTables (pilote de fichier texte)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote fichier texte. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner*|Le seul argument valide pour *szTableOwner* a la valeur NULL, car aucun des pilotes prend en charge les noms de propriétaire. Avec *szTableOwner* la valeur NULL, toutes les tables sont retournées. Dans la colonne TABLE_OWNER la valeur NULL est retournée.|  
|*szTableQualifier*|Dans la colonne TABLE_QUALIFIER, **SQLTables** retourne le chemin d’accès à un répertoire.|  
|*SzTableType*|« TABLE » est le seul type de table pris en charge.<br /><br /> Lorsque le pilote de texte est utilisé, la liste des fichiers retournées par **SQLTables** est déterminée par les extensions de fichier dans le **liste des Extensions** zone le **le programme d’installation de ODBC texte** boîte de dialogue.|

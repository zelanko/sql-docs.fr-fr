---
title: Sys.external_languages (Transact-SQL) - SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: dphansen
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- external_languages
- external_languages_TSQL
- sys.external_languages
- sys.external_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_languages catalog view
author: nelgson
ms.author: negust
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1cef52f066a07032240d17f88297b02ba3f7e5fb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65995117"
---
# <a name="sysexternallanguages-transact-sql"></a>sys.external_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet affichage catalogue fournit une liste des langues dans la base de données externes. **R** et **Python** étant des noms réservés, aucun langage externe ne peut être créé avec ces derniers.

## <a name="sysexternallanguages"></a>sys.external_languages

Le sys.external_languages de vue de catalogue répertorie une ligne pour chaque langage dans la base de données externe.

|Nom de colonne |Type de données | Description|
|------|------|------|
|external_language_id |INT | ID de la langue externe|
|langage |sysname |Nom du langage externe. Unique dans la base de données. R et Python sont des noms réservés par instance|
|create_date |datetime2 |Date et heure de création|
|principal_id |INT |ID du principal qui possède cette bibliothèque externe|

## <a name="see-also"></a>Voir aussi  

+ [sys.external_language_files](sys-external-language-files-transact-sql.md)  
+ [CRÉER DE LANGAGE EXTERNE](../../t-sql/statements/create-external-language-transact-sql.md) 

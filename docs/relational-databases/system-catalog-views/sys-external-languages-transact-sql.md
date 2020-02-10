---
title: sys. external_languages (Transact-SQL)-SQL Server | Microsoft Docs
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "65995117"
---
# <a name="sysexternal_languages-transact-sql"></a>sys. external_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet affichage catalogue fournit une liste des langues externes dans la base de données. **R** et **python** sont des noms réservés et aucune langue externe ne peut être créée avec ces noms spécifiques.

## <a name="sysexternal_languages"></a>sys.external_languages

L’affichage catalogue sys. external_languages répertorie une ligne pour chaque langue externe de la base de données.

|Nom de la colonne |Type de données | Description|
|------|------|------|
|external_language_id |int | ID de la langue externe|
|langage |sysname |Nom de la langue externe. Unique dans la base de données. R et Python sont des noms réservés par instance|
|create_date |datetime2 |Date et heure de création|
|principal_id |int |ID du principal propriétaire de cette bibliothèque externe|

## <a name="see-also"></a>Voir aussi  

+ [sys.external_language_files](sys-external-language-files-transact-sql.md)  
+ [CRÉER UNE LANGUE EXTERNE](../../t-sql/statements/create-external-language-transact-sql.md) 

---
title: Sys.external_language_files (Transact-SQL) - SQL Server | Microsoft Docs
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
ms.openlocfilehash: 0d1325311ef0b708f5a3abd5f4494e099863efc2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65995087"
---
# <a name="sysexternallanguagefiles-transact-sql"></a>sys.external_language_files (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet affichage catalogue fournit une liste des fichiers d’extension de langage externe dans la base de données. **R** et **Python** étant des noms réservés, aucun langage externe ne peut être créé avec ces derniers.

Lorsqu’un langage externe est créé à partir d’un file_spec, l’extension elle-même et ses propriétés sont répertoriées dans cette vue. Cette vue contient une seule entrée par langue, selon le système d’exploitation.

## <a name="sysexternallanguages"></a>sys.external_languages

Le sys.external_language_files de vue de catalogue répertorie une ligne pour chaque extension de langage externe dans la base de données. Paramètres

|Nom de colonne |Type de données | Description|
|------|------|------|
|external_language_id |INT | ID de la langue externe|
|content|varbinary(max) |Contenu du fichier d’extension de langage externe|
|file_name|nvarchar(266)|Nom du fichier d’extension de langage|
|Plateforme|TINYINT|ID de la plateforme hôte sur lequel SQL Server est installé|
|platform_desc |nvarchar(60)|Nom de la plateforme hôte. Les valeurs valides sont « WINDOWS », « LINUX ».|
|Paramètres|nvarchar(4000)|Langage externe prameters|
|environment_variables |nvarchar(4000)|Variables d’environnement de langage externe|

## <a name="see-also"></a>Voir aussi  

+ [sys.external_languages](sys-external-languages-transact-sql.md)  
+ [CRÉER DE LANGAGE EXTERNE](../../t-sql/statements/create-external-language-transact-sql.md)  

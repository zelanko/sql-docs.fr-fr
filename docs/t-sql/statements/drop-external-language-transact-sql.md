---
title: DROP EXTERNAL LANGUAGE (Transact-SQL) - SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 08/08/2019
ms.prod: sql
ms.technology: language-extensions
ms.topic: language-reference
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 3767bec1807b68df3eb3f82287a5c871d653a286
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68892982"
---
# <a name="drop-external-library-transact-sql"></a>DROP EXTERNAL LIBRARY (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Supprime un langage externe existant.

## <a name="syntax"></a>Syntaxe

```text
DROP EXTERNAL LANGUAGE <language_name>
```

### <a name="arguments"></a>Arguments

**language_name**

Les langages sont des objets dont l’étendue est limitée à la base de données. Les noms de langage doivent être uniques dans la base de données.

## <a name="permissions"></a>Autorisations

La suppression d’un langage réclame le privilège ALTER ANY EXTERNAL LANGUAGE. Par défaut, le propriétaire de la base de données ou de l’objet peut également supprimer un langage externe.

> [!NOTE]
> Notez qu’avant de supprimer un langage externe, vous devez supprimer les bibliothèques externes qui le référencent.

### <a name="return-values"></a>Valeurs retournées

Un message d’information est retourné si l’instruction a réussi.

## <a name="remarks"></a>Notes

Avant de pouvoir supprimer un langage externe, vous devez supprimer toutes les bibliothèques externes pour le langage spécifié.

## <a name="examples"></a>Exemples

Créer un langage externe **Java** :

```sql
CREATE EXTERNAL LANGUAGE Java 
FROM (CONTENT = N'<path-to-zip>', FILE_NAME = 'javaextension.dll');
GO
```

Supprimer le langage externe :

```sql
DROP EXTERNAL LANGUAGE Java;
```

## <a name="see-also"></a>Voir aussi

[CREATE EXTERNAL LANGUAGE (Transact-SQL)](create-external-language-transact-sql.md)  
[ALTER EXTERNAL LANGUAGE (Transact-SQL)](alter-external-language-transact-sql.md)  
[sys.external_languages](../../relational-databases/system-catalog-views/sys-external-languages-transact-sql.md)  
[sys.external_language_files](../../relational-databases/system-catalog-views/sys-external-language-files-transact-sql.md)  

---
description: DROP EXTERNAL LANGUAGE (Transact-SQL) - SQL Server
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
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15'
ms.openlocfilehash: 785aaff078085fd5c202e7b3c043ab87e273472f
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97481800"
---
# <a name="drop-external-language-transact-sql"></a>DROP EXTERNAL LANGUAGE (Transact-SQL)  
[!INCLUDE [SQL Server 2019 and later](../../includes/applies-to-version/sqlserver2019.md)]

Supprime un langage externe existant.

## <a name="syntax"></a>Syntaxe

```syntaxsql
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

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

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

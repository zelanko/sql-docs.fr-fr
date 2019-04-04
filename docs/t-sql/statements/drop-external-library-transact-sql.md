---
title: DROP EXTERNAL LIBRARY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/27/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP EXTERNAL LIBRARY
- DROP_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP EXTERNAL LIBRARY
author: dphansen
ms.author: davidph
manager: cgronlund
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 86609c0cb3e66397c4c8c8f3a09fba64b14089e4
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58492821"
---
# <a name="drop-external-library-transact-sql"></a>DROP EXTERNAL LIBRARY (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Supprime une bibliothèque de package existante. Des bibliothèques de packages sont utilisées par les runtimes externes pris en charge, comme R, Python ou Java.

> [!NOTE]
> Dans SQL Server 2017, le langage R et la plateforme Windows sont pris en charge. R, Python et Java sur les plateformes Windows et Linux sont pris en charge dans SQL Server 2019 CTP 2.4. 

## <a name="syntax"></a>Syntaxe

```sql
DROP EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ];
```

### <a name="arguments"></a>Arguments

**library_name**

Spécifie le nom d’une bibliothèque de package existante.

Les bibliothèques sont limitées à l’utilisateur. Les noms de bibliothèques doivent être uniques dans le contexte d’un utilisateur ou d’un propriétaire donné.

**owner_name**

Spécifie le nom de l’utilisateur ou du rôle propriétaire de la bibliothèque externe.

Les propriétaires de base de données peuvent supprimer les bibliothèques créées par les autres utilisateurs.

## <a name="permissions"></a>Autorisations

Supprimer une bibliothèque réclame le privilège ALTER ANY EXTERNAL LIBRARY. Par défaut, le propriétaire de la base de données ou de l’objet peut également supprimer une bibliothèque externe.

### <a name="return-values"></a>Valeurs retournées

Un message d’information est retourné si l’instruction a réussi.

## <a name="remarks"></a>Notes 

Contrairement à d’autres instructions `DROP` de SQL Server, cette instruction prend en charge la spécification d’une clause d’autorisation facultative. Cela permet au **propriétaire de la base de données** et aux utilisateurs disposant du rôle **db_owner** de supprimer une bibliothèque de package chargée par un utilisateur standard dans la base de données.

## <a name="examples"></a>Exemples

Ajoutez le package R personnalisé, `customPackage`, à une base de données :

```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM (CONTENT = 'C:\temp\customPackage_v1.1.zip')
WITH (LANGUAGE = 'R');
GO
```

Supprimez la bibliothèque `customPackage`.

```sql
DROP EXTERNAL LIBRARY customPackage;
```

## <a name="see-also"></a>Voir aussi

[CREATE EXTERNAL LIBRARY (Transact-SQL)](create-external-library-transact-sql.md)  
[ALTER EXTERNAL LIBRARY (Transact-SQL)](alter-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  


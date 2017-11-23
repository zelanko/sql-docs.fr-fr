---
title: "ALTER bibliothèque externe (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-non-specified
ms.prod_service: 
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL LIBRARY
- ALTER_EXTERNAL_LIBRARY_TSQL
dev_langs: TSQL
helpviewer_keywords: ALTER EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: 8365e364c9769af139be2b8dd4e7f5943afc58ff
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="alter-external-library-transact-sql"></a>ALTER bibliothèque externe (Transact-SQL)  

[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

Modifie le contenu d’une bibliothèque externe package existante.

## <a name="syntax"></a>Syntaxe

```
ALTER EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ]
SET <file_spec>
WITH ( LANGUAGE = 'R' )
[ ; ]

<file_spec> ::=
{
(CONTENT = { <client_library_specifier> | <library_bits> | NONE}
[, PLATFORM = WINDOWS )
}

<client_library_specifier> :: =
  '[\\computer_name\]share_name\[path\]manifest_file_name'
| '[local_path\]manifest_file_name'
| '<relative_path_in_external_data_source>'

<library_bits> :: =
{ varbinary_literal | varbinary_expression }
```

### <a name="arguments"></a>Arguments

**nom_librairie**

Spécifie le nom d’une bibliothèque de package existante. Les bibliothèques sont limités à l’utilisateur. Autrement dit, les noms de bibliothèque sont considérées comme uniques dans le contexte d’un utilisateur spécifique ou un propriétaire.

**owner_name**

Spécifie le nom de l’utilisateur ou le rôle de propriétaire de la bibliothèque externe.

**file_spec**

Spécifie le contenu du package pour une plateforme spécifique. Artefact qu’un seul fichier par la plateforme est pris en charge.

Le fichier peut être spécifié sous la forme d’un chemin d’accès local ou un chemin d’accès réseau. Si l’option de source de données est spécifiée, le nom de fichier peut être un chemin d’accès relatif en ce qui concerne le conteneur référencé dans le `EXTERNAL DATA SOURCE`.

Si vous le souhaitez, une plateforme de système d’exploitation pour le fichier peut être spécifiée. Les artefacts qu’un seul fichier ou le contenu est autorisé pour chaque plate-forme de système d’exploitation pour une langue spécifique ou d’un runtime.

**DATA_SOURCE = external_data_source_name**

Spécifie le nom de la source de données externe qui contient l’emplacement du fichier de bibliothèque. Cet emplacement doit faire référence à un chemin d’accès de stockage blob Azure. Pour créer une source de données externe, utilisez [créer une SOURCE de données externe (Transact-SQL)](create-external-data-source-transact-sql.md).

> [!IMPORTANT] 
> Actuellement, les objets BLOB n’est pas pris en charge comme source de données dans la version de SQL Server 2017.

**library_bits**

Spécifie le contenu du package comme un littéral hexadécimal, similaire aux assemblys. Cette option permet aux utilisateurs de créer une bibliothèque pour modifier la bibliothèque s’ils ont l’autorisation requise, mais que vous n’ont pas de chemins d’accès de fichier à n’importe quel dossier sur que le serveur peut accéder.

**PLATEFORME = WINDOWS**

Spécifie la plateforme pour le contenu de la bibliothèque. Cette valeur est requise lors de la modification d’une bibliothèque existante pour ajouter une autre plateforme. Windows est la seule plateforme prise en charge.

## <a name="remarks"></a>Notes

Pour le langage R, les packages doivent être préparées sous la forme de fichiers d’archive ZIP avec le. Extension ZIP pour Windows. Actuellement, seule la plate-forme Windows est prise en charge.  

La `ALTER EXTERNAL LIBRARY` instruction télécharge uniquement les bits de la bibliothèque à la base de données. La bibliothèque modifiée n’est pas installée jusqu'à ce qu’un utilisateur exécute un script externe par la suite, en exécutant [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

## <a name="permissions"></a>Permissions

Nécessite le `ALTER ANY EXTERNAL LIBRARY` autorisation. Les utilisateurs qui a créé une bibliothèque externe peut modifier cette bibliothèque externe.

## <a name="examples"></a>Exemples

Les exemples suivants modifie une bibliothèque externe appelée customPackage.

### <a name="a-replace-the-contents-of-a-library-using-a-file"></a>A. Remplacez le contenu d’une bibliothèque à l’aide d’un fichier

L’exemple suivant modifie une bibliothèque externe appelée customPackage, à l’aide d’un fichier compressé qui contient les bits mis à jour.

```sql
ALTER EXTERNAL LIBRARY customPackage 
SET 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip')
WITH (LANGUAGE = 'R');
```  

Pour installer la bibliothèque de mise à jour, exécutez la procédure stockée `sp_execute_external_script`.

```sql   
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'
# load customPackage
library(customPackage)
# call customPackageFunc
OutputDataSet <- customPackageFunc()
'
WITH RESULT SETS (([result] int));
```

### <a name="b-alter-an-existing-library-using-a-byte-stream"></a>B. Modifier une bibliothèque existante à l’aide d’un flux d’octets

L’exemple suivant modifie la bibliothèque existante en passant les bits de nouveau en tant qu’un hexadécimal littéral.

```SQL
ALTER EXTERNAL LIBRARY customLibrary FROM (CONTENT = 0xabc123) WITH (LANGUAGE = 'R');
```

## <a name="see-also"></a>Voir aussi  

[CRÉER la bibliothèque externe (Transact-SQL)](create-external-library-transact-sql.md)
[supprimer la bibliothèque externe (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  

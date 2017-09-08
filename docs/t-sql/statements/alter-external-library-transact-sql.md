---
title: "ALTER bibliothèque externe (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL LIBRARY
- ALTER_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 541419770828e01cca82fb33ead1b22170f8e4f3
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-external-library-transact-sql"></a>ALTER bibliothèque externe (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

Modifie le contenu existant de la bibliothèque.  

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

**PLATEFORME = WINDOWS**

Spécifie la plateforme pour le contenu de la bibliothèque. Cette valeur est requise lors de la modification d’une bibliothèque existante pour ajouter une autre plateforme. Windows est la seule plateforme prise en charge.

## <a name="remarks"></a>Notes

Pour le langage R, les packages doivent être préparées sous la forme de fichiers d’archive ZIP avec le. Extension ZIP pour Windows. Actuellement, seule la plate-forme Windows est prise en charge.  
La `ALTER EXTERNAL LIBRARY` instruction télécharge uniquement les bits de la bibliothèque à la base de données. La bibliothèque modifiée n’est pas installée jusqu'à ce qu’un utilisateur exécute un script externe par la suite, en exécutant [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

## <a name="permissions"></a>Permissions
Nécessite le `ALTER ANY EXTERNAL LIBRARY` autorisation. Les utilisateurs qui a créé une bibliothèque externe peut modifier cette bibliothèque externe.

## <a name="examples"></a>Exemples

L’exemple suivant modifie une bibliothèque externe appelée customPackage.

```sql  
ALTER EXTERNAL LIBRARY customPackage 
SET 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip')
WITH (LANGUAGE = 'R');
```  
Puis exécutez le `sp_execute_external_script` procédure pour installer la bibliothèque.

```sql   
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'
# load customPackage
library(customPackage)

# call customPackageFunc
OutputDataSet <- customPackageFunc()
'
with result sets (([result] int));    
```


## <a name="see-also"></a>Voir aussi  
[CRÉER la bibliothèque externe (Transact-SQL)](create-external-library-transact-sql.md)
[supprimer la bibliothèque externe (Transact-SQL)](drop-external-library-transact-sql.md)  
[Sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[Sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  


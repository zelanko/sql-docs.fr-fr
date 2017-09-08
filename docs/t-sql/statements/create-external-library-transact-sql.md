---
title: "CRÉER la bibliothèque externe (Transact-SQL) | Documents Microsoft"
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
- CREATE EXTERNAL LIBRARY
- CREATE_EXTERNAL_LIBRARY_TSQL
- EXTERNAL LIBRARY
- EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE EXTERNAL LIBRARY
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0f11a6b7633be392e1f789e12c43f2e5d6e56b47
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-external-library-transact-sql"></a>CRÉER la bibliothèque externe (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ssvnxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]  

Télécharge des packages R sur une base de données à partir du chemin de flux ou un fichier spécifié d’octets.

Cette instruction sert un mécanisme générique de l’administrateur de base de données de téléchargement des artefacts nécessaires pour tout nouveau runtime de langage externe (R, Python, Java, etc.) et les plateformes de système d’exploitation pris en charge par [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)]. Actuellement seules la langue de R et de la plateforme Windows sont pris en charge.

## <a name="syntax"></a>Syntaxe

```
CREATE EXTERNAL LIBRARY library_name  
    [ AUTHORIZATION owner_name ]  
FROM <file_spec> [,…2]  
WITH ( LANGUAGE = 'R' )  
[ ; ]  

<file_spec> ::=  
{  
(CONTENT = { <client_library_specifier> | <library_bits> }  
[, PLATFORM = WINDOWS ])  
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

Bibliothèques sont ajoutées à la base de données d’une étendue à l’utilisateur. Autrement dit, les noms de bibliothèque sont considérés comme étant uniques dans le contexte d’un utilisateur spécifique ou un propriétaire et les noms de bibliothèque doivent être uniques pour chaque utilisateur. Par exemple, deux utilisateurs **RUser1** et **RUser2** peuvent à la fois individuellement et séparément le téléchargement de la bibliothèque R `ggplot2`. 

**owner_name**

Spécifie le nom de l’utilisateur ou le rôle de propriétaire de la bibliothèque externe. En l'absence de spécification, la propriété revient à l'utilisateur actuel.

Les bibliothèques appartenant au propriétaire de la base de données sont considérés comme globales pour la base de données et d’exécution. En d’autres termes, les propriétaires de base de données peuvent créer des bibliothèques qui contiennent un ensemble commun de bibliothèques ou les packages qui sont partagés par de nombreux utilisateurs. Lorsqu’une bibliothèque externe est créée par un utilisateur autre que le `dbo` , la bibliothèque externe est privée pour cet utilisateur uniquement.   

Lorsque l’utilisateur **RUser1** exécute un script R, la valeur de `libPath` peut contenir plusieurs chemins d’accès. Le premier chemin d’accès est toujours le chemin d’accès à la bibliothèque partagée créée par le propriétaire de la base de données. La deuxième partie de `libPath` Spécifie le chemin d’accès contenant les packages téléchargés individuellement par **RUser1**.

**file_spec**

Spécifie le contenu du package pour une plateforme spécifique. Artefact qu’un seul fichier par la plateforme est pris en charge. 

Le fichier peut être spécifié sous la forme d’un chemin d’accès local ou un chemin d’accès réseau.

Si vous le souhaitez, une plateforme de système d’exploitation pour le fichier peut être spécifiée. Les artefacts qu’un seul fichier ou le contenu est autorisé pour chaque plate-forme de système d’exploitation pour une langue spécifique ou d’un runtime.

**PLATEFORME = WINDOWS**

Spécifie la plateforme pour le contenu de la bibliothèque. La valeur par défaut est la plateforme hôte sur lequel SQL Server est en cours d’exécution. Par conséquent, l’utilisateur ne doit spécifier la valeur. Il est obligatoire en cas où plusieurs plateformes sont prises en charge, ou l’utilisateur doit spécifier une autre plateforme. Windows est la seule plateforme prise en charge.

## <a name="remarks"></a>Notes

Pour le langage R, les packages doivent être préparées sous la forme de fichiers d’archive ZIP avec le. Extension ZIP pour Windows. Actuellement, seule la plate-forme Windows est prise en charge.  

La `CREATE EXTERNAL LIBRARY` instruction télécharge uniquement les bits de la bibliothèque à la base de données. La bibliothèque n’est pas installée jusqu'à ce qu’un utilisateur exécute un script externe par la suite, en exécutant [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).  

## <a name="permissions"></a>Permissions  
Nécessite le `CREATE EXTERNAL LIBRARY` autorisation.  

## <a name="examples"></a>Exemples

### <a name="a-add-an-external-library-to-a-database"></a>A. Ajouter une bibliothèque externe à une base de données  
L’exemple suivant ajoute une bibliothèque externe appelée customPackage à une base de données.   
```sql
CREATE EXTERNAL LIBRARY customPackage 
FROM 
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

### <a name="b-installing-packages-with-dependencies"></a>B. Installation de packages avec des dépendances

Si `packageB` a une dépendance sur `packageA`, puis par exemple, le code suit ces entités générales :   
```
CREATE EXTERNAL LIBRARY packageA 
FROM 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\ggplot2.zip') 
WITH (LANGUAGE = 'R'); 

CREATE EXTERNAL LIBRARY packageB FROM 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\ggplot2.zip') 
WITH (LANGUAGE = 'R');
```

`packageA`et `packageB` sont tous deux installés quand `sp_execute_external_script` la première exécution.   
```sql
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'
# load packageB
library(packageB)

# call customPackageBFunc
OutputDataSet <- customPackageBFunc()
'
with result sets (([result] int));    
```

Pour ce faire, le dossier dans lequel les packages sont enregistrés doit être accessible au serveur. 

### <a name="change-an-existing-package-library"></a>Modifier une bibliothèque de package existante

La `ALTER EXTERNAL LIBRARY` instruction DDL peut être utilisée pour ajouter un nouveau contenu de la bibliothèque ou de modifier le contenu existant de la bibliothèque.   

### <a name="delete-a-package-library"></a>Supprimer une bibliothèque de package

Pour supprimer une bibliothèque de package à partir de la base de données, exécutez l’instruction :

```sql
DROP EXTERNAL LIBRARY ggplot2 <user_name>;
```

> [!NOTE]
> Contrairement à d’autres `DROP` instructions dans [!INCLUDE[ssnoversion](../../includes/ssnoversion.md)], cette instruction prend en charge un paramètre facultatif qui spécifie l’autorisation de l’utilisateur. Cette option permet aux utilisateurs avec des rôles de la propriété à supprimer les bibliothèques téléchargés par les utilisateurs normaux. 

## <a name="see-also"></a>Voir aussi  
[ALTER bibliothèque externe (Transact-SQL)](alter-external-library-transact-sql.md)  
[SUPPRIMER la bibliothèque externe (Transact-SQL)](drop-external-library-transact-sql.md)  
[Sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[Sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md)  


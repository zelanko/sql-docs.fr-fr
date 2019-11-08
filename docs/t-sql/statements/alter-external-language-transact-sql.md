---
title: ALTER EXTERNAL LANGUAGE (Transact-SQL) - SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.reviewer: dphansen
ms.technology: language-extensions
ms.topic: language-reference
author: nelgson
ms.author: negust
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1b831047e4c2b8bad166e5ddf5ce3bdc7f8b6165
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532859"
---
# <a name="create-external-language-transact-sql"></a>CREATE EXTERNAL LANGUAGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Modifie le contenu d’une extension de langage externe existante dans la base de données.

## <a name="syntax"></a>Syntaxe

```text
ALTER EXTERNAL LANGUAGE language_name  
[ AUTHORIZATION owner_name ]
{
    SET <file_spec>
    | ADD <file_spec>
    | REMOVE <file_spec>
}
[ ; ]  

<file_spec> ::=  
{
    ( CONTENT = {<external_lang_specifier> | <content_bits>,
    FILE_NAME = <external_lang_file_name>
    [, PLATFORM = <platform> ]
    [, PARAMETERS = <external_lang_parameters> ]
    [, ENVIRONMENT_VARIABLES = <external_lang_env_variables> ] )
}

<external_lang_specifier> :: =  
{
    '[file_path\]os_file_name'  
}

<content_bits> :: =  
{
    varbinary_literal
   | varbinary_expression
}

<external_lang_file_name> :: =  
'extension_file_name'

<platform> :: =
{
   WINDOWS
  | LINUX
}

< external_lang_parameters > :: =  
'extension_specific_parameters'
```

### <a name="arguments"></a>Arguments

**language_name**

Les langages sont des objets dont l’étendue est limitée à la base de données. Les noms de langage doivent être uniques dans la base de données.

**owner_name**

Spécifie le nom de l’utilisateur ou du rôle propriétaire du langage externe. En l'absence de spécification, la propriété revient à l'utilisateur actuel. Suivant les autorisations, il peut s’avérer nécessaire d’accorder à d’autres utilisateurs une autorisation explicite pour exécuter des scripts à l’aide d’un langage spécifique.

**file_spec**

Spécifie le contenu de l’extension de langage. Un seul fichier de spécification est autorisé pour un langage spécifique par plateforme. 

**external_lang_specifier**

Chemin complet du fichier .zip ou tar.gz contenant le code des extensions. Ce contenu peut être le chemin d’un fichier .zip (sur Windows) ou d’un fichier tar.gz (sur Linux).

**content_bits**

Spécifie le contenu du langage en tant que littéral hexadécimal, similaire aux assemblys.
Cette option est utile si vous devez créer un langage ou modifier un langage existant (et que vous disposez des autorisations nécessaires), mais que le système de fichiers sur le serveur est restreint et vous ne pouvez pas copier les fichiers de bibliothèque vers un emplacement accessible au serveur.

**external_lang_file_name**

Nom du fichier d’extension .dll ou .so. Cet argument est nécessaire pour identifier le fichier approprié, au cas où il existerait plusieurs fichiers .dll ou .so dans le fichier .zip ou tar.gz défini par <external_lang_specifier>.

**external_lang_parameters**

Cet argument permet de donner un ensemble de paramètres au runtime de langage externe. Les valeurs de paramètre sont fournies au runtime externe une fois que le processus externe a démarré. Toutefois, les variables d’environnement sont accessibles à l’extension de langage avant le démarrage du processus externe.

**external_lang_env_variables**

Cet argument permet de donner un ensemble de variables d’environnement au runtime de langage externe avant le démarrage du processus externe. Un exemple de variable d’environnement est le répertoire de base du runtime lui-même. Par exemple : JRE_HOME.

**platform**

Ce paramètre est nécessaire pour les scénarios de systèmes d’exploitation hybrides. Dans une architecture hybride, le langage doit être inscrit une fois par plateforme. La plateforme et le nom du langage constituent la clé unique par langage externe. Si aucune plateforme n’est spécifiée, le système d’exploitation actuel est pris en considération.

## <a name="remarks"></a>Notes

Actuellement, **PARAMETERS** et **ENVIRONMENT_VARIABLES** ne sont pas pris en charge.

## <a name="permissions"></a>Autorisations

Nécessite l’autorisation `ALTER ANY EXTERNAL LANGUAGE`. Par défaut, tout utilisateur qui possède **dbo**, membre du rôle **db_owner**, dispose des autorisations nécessaires pour modifier un langage externe. En ce qui concerne les autres utilisateurs, vous devez leur en donner l’autorisation explicitement à l’aide d’une instruction [GRANT](https://docs.microsoft.com/sql/t-sql/statements/grant-database-permissions-transact-sql), en spécifiant le privilège ALTER ANY EXTERNAL LANGUAGE.

## <a name="examples"></a>Exemples

### <a name="alter-an-external-language-in-a-database"></a>Modifier un langage externe dans une base de données  

L’exemple suivant ajoute un langage externe appelé Java à une base de données sur SQL Server sur Windows.

```sql
ALTER EXTERNAL LANGUAGE Java 
SET (CONTENT = N'<path-to-zip>', FILE_NAME = 'javaextension.dll');
GO
```

## <a name="see-also"></a>Voir aussi

[CREATE EXTERNAL LANGUAGE (Transact-SQL)](create-external-language-transact-sql.md)  
[DROP EXTERNAL LANGUAGE (Transact-SQL)](drop-external-language-transact-sql.md)  
[sys.external_languages](../../relational-databases/system-catalog-views/sys-external-languages-transact-sql.md)  
[sys.external_language_files](../../relational-databases/system-catalog-views/sys-external-language-files-transact-sql.md)  

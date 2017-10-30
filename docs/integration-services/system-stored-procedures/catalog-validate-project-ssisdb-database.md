---
title: "Catalog.validate_project (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5270689a-46d4-4847-b41f-3bed1899e955
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 83439015694f4235af4a67e994e916651ec63cc1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogvalidateproject-ssisdb-database"></a>catalog.validate_project (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Valide de façon asynchrone un projet dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql
catalog.validate_project [ @folder_name = ] folder_name  
    , [ @project_name = ] project_name  
    , [ @validate_type = ] validate_type  
    , [ @validation_id = ] validation_id OUTPUT  
 [  , [ @use32bitruntime = ] use32bitruntime ]  
 [  , [ @target_environment = ] target_environment ]  
 [  , [ @reference_id = ] reference_id ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name =] *nom_dossier*  
 Nom d'un dossier qui contient le projet. Le *nom_dossier* est **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Nom du projet. Le *project_name* est **nvarchar (128)**.  
  
 [ @validate_type =] *validate_type*  
 Indique le type de validation à réaliser. Utilisez le caractère `F` pour effectuer une validation complète. Le *validate_type* est **char (1)**.  
  
 [ @validation_id =] *validation_id*  
 Retourne l'identificateur unique (ID) de la validation. Le *validation_id* est **bigint**.  
  
 [ @use32bitruntime =] *use32bitruntime*  
 Indique si l'exécution 32 bits doit être utilisée pour exécuter le package sur un système d'exploitation 64 bits. Utilisez la valeur de `1` pour exécuter le package avec le runtime 32 bits lors de l’exécution sur un système d’exploitation de 64 bits. Utilisez la valeur `0` pour exécuter le package avec l'exécution 64 bits lorsqu'un système d'exploitation 64 bits est exécuté. Ce paramètre est facultatif. Le *use32bitruntime* est **bits**.  
  
 [ @environment_scope =] *environment_scope*  
 Indique les références environnementales considérées par la validation. Lorsque la valeur est `A`, toutes les références environnementales associées au projet sont incluses dans la validation. Lorsque la valeur est `S`, seule une référence environnementale unique est incluse. Lorsque la valeur est `D`, aucune référence environnementale n'est incluse et chaque paramètre doit avoir une valeur par défaut littérale pour passer la validation. Ce paramètre est facultatif, le caractère `D` sera utilisé par défaut. Le *environment_scope* est **char (1)**.  
  
 [ @reference_id =] *reference_id*  
 ID unique de la référence environnementale. Ce paramètre est obligatoire uniquement quand une référence environnementale unique est incluse dans la validation, lors de la *environment_scope* est `S`. Le *reference_id* est **bigint**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 La sortie des étapes de validation est retournée sous la forme de sections différentes du jeu de résultats.  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations de lecture sur le projet et, le cas échéant, les autorisations de lecture sur les environnements référencés  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante fournit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   La validation échoue pour un ou plusieurs packages dans le projet  
  
-   La validation échoue si un ou plusieurs des environnements référencés inclus dans la validation ne contiennent pas de variables référencées  
  
-   Le type validé spécifié n'est pas valide.  
  
-   Le nom du projet ou l'ID de référence d'environnement n'est pas valide  
  
-   L’utilisateur ne dispose pas des autorisations appropriées  
  
## <a name="remarks"></a>Notes  
 La validation aide à identifier les problèmes qui empêchent les packages dans le projet de s'exécuter avec succès. Utilisez le [catalog.validations](../../integration-services/system-views/catalog-validations-ssisdb-database.md) ou [catalog.operations](../../integration-services/system-views/catalog-operations-ssisdb-database.md) vues pour surveiller l’état de validation.  
  
 Seuls les environnements qui sont accessibles par l'utilisateur peuvent être utilisés dans la validation. La sortie de validation est envoyée au client sous forme d'un jeu de résultats.  
  
 Dans cette version, la validation de projet ne prend pas en charge la validation de dépendance.  
  
 La validation complète confirme que toutes les variables d'environnement référencées sont recherchées dans les environnements référencés inclus dans la validation. Les résultats de la validation complète répertorient des références environnementales qui ne sont pas des variables d'environnement valides et référencées et qui sont introuvables dans les environnements référencés inclus dans la validation.  
  
  


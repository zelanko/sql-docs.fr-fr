---
title: "Catalog.validate_package (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- validate_package stored procedure [Integration Services]
- catalog.validate_package stored procedure [Integration Services]
ms.assetid: 0dc03df1-b793-408f-af4c-c11188729abf
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 869b758e3ac922762c293eb8aa9a9537a4397bd6
ms.contentlocale: fr-fr
ms.lasthandoff: 10/20/2017

---
# <a name="catalogvalidatepackage-ssisdb-database"></a>catalog.validate_package (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Valide de façon asynchrone un package dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql
catalog.validate_package [ @folder_name = ] folder_name  
    , [ @project_name = ] project_name  
    , [ @package_name = ] package_name  
    , [ @validation_id = ] validation_id OUTPUT  
 [  , [ @use32bitruntime = ] use32bitruntime ]  
 [  , [ @target_environment = ] target_environment ]  
 [  , [ @reference_id = ] reference_id ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name =] *nom_dossier*  
 Nom du dossier qui contient le package. Le *nom_dossier* est **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Nom du  projet qui contient le package. Le *project_name* est **nvarchar (128)**.  
  
 [ @package_name =] *package_name*  
 Nom du package. Le *package_name* est **nvarchar (260)**.  
  
 [ @validation_id =] *validation_id*  
 Retourne l'identificateur unique (ID) de la validation. Le *validation_id* est **bigint**.  
  
 [ @use32bitruntime =] *use32bitruntime*  
 Indique si l'exécution 32 bits doit être utilisée pour exécuter le package sur un système d'exploitation 64 bits. Utilisez la valeur de `1` pour exécuter le package avec le runtime 32 bits lors de l’exécution sur un système d’exploitation de 64 bits. Utilisez la valeur `0` pour exécuter le package avec l'exécution 64 bits lorsqu'un système d'exploitation 64 bits est exécuté. Ce paramètre est facultatif. Le *use32bitruntime* est **bits**.  
  
 [ @environment_scope =] *environment_scope*  
 Indique les références environnementales considérées par la validation. Lorsque la valeur est `A`, toutes les références environnementales associées au projet sont incluses dans la validation. Lorsque la valeur est `S`, seule une référence environnementale unique est incluse. Lorsque la valeur est `D`, aucune référence environnementale n'est incluse et chaque paramètre doit avoir une valeur par défaut littérale pour passer la validation. Ce paramètre est facultatif. Le caractère `D` est utilisé par défaut. Le *environment_scope* est **char (1)**.  
  
 [ @reference_id =] *reference_id*  
 ID unique de la référence environnementale. Ce paramètre est obligatoire uniquement quand une référence environnementale unique est incluse dans la validation, lors de la *environment_scope* est `S`. Le *reference_id* est **bigint**.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations de lecture sur le projet et, le cas échéant, les autorisations de lecture sur les environnements référencés  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   Le nom du projet ou le nom de package n'est pas valide  
  
-   L’utilisateur ne dispose pas des autorisations appropriées  
  
-   Un ou plusieurs environnements référencés inclus dans la validation ne contiennent pas de variables référencées  
  
-   La validation du package échoue  
  
-   L'environnement référencé n'existe pas  
  
-   Les variables référencées ne peuvent pas être trouvées dans les environnements référencés inclus dans la validation  
  
-   Les variables sont référencées dans les paramètres du package, mais aucun environnement référencé n'a été inclus dans la validation  
  
## <a name="remarks"></a>Notes  
 La validation aide à identifier les problèmes qui peuvent empêcher le package à partir de l’exécution avec succès. Utilisez le [catalog.validations](../../integration-services/system-views/catalog-validations-ssisdb-database.md) ou [catalog.operations](../../integration-services/system-views/catalog-operations-ssisdb-database.md) vues pour surveiller l’état de validation.  
  
  


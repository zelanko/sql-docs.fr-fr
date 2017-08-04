---
title: "Catalog.create_execution (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 45d0c2f6-1f38-445f-ac06-e2a01f6ac600
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 95c07e2550330ff9a2ac1cc70107d11147ae53dd
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="catalogcreateexecution-ssisdb-database"></a>catalog.create_execution (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Crée une instance d'exécution dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Cette procédure stockée utilise le niveau de journalisation par défaut du serveur.  
  
## <a name="syntax"></a>Syntaxe  
  
```tsql  
create_execution [ @folder_name = folder_name  
     , [ @project_name = ] project_name  
     , [ @package_name = ] package_name  
  [  , [ @reference_id = ] reference_id ]  
  [  , [ @use32bitruntime = ] use32bitruntime ] 
  [  , [ @runinscaleout = ] runinscaleout ]
  [  , [ @useanyworker = ] useanyworker ] 
     , [ @execution_id = ] execution_id OUTPUT  
```  
  
## <a name="arguments"></a>Arguments  
 [ @folder_name =] *nom_dossier*  
 Nom du dossier qui contient le package qui sera exécuté. Le *nom_dossier* est **nvarchar (128)**.  
  
 [ @project_name =] *project_name*  
 Le nom du projet qui contient le package doit être exécutée. Le *project_name* est **nvarchar (128)**.  
  
 [ @package_name =] *package_name*  
 Nom du package qui sera exécuté. Le *package_name* est **nvarchar (260)**.  
  
 [ @reference_id =] *reference_id*  
 Identificateur unique d'une référence environnementale. Ce paramètre est facultatif. Le *reference_id* est **bigint**.  
  
 [ @use32bitruntime =] *use32bitruntime*  
 Indique si l'exécution 32 bits doit être utilisée pour exécuter le package sur un système d'exploitation 64 bits. Utilisez la valeur 1 pour exécuter le package avec le runtime 32 bits lors de l’exécution sur un système d’exploitation de 64 bits. Utilisez la valeur 0 pour exécuter le package avec l'exécution 64 bits lorsqu'un système d'exploitation 64 bits est exécuté. Ce paramètre est facultatif. Le *Use32bitruntime* est **bits**.  
 
 [ @runinscaleout =] *runinscaleout*  
 Indique si l’exécution est de monter en charge. Utilisez la valeur 1 pour exécuter le package de monter en charge. Utilisez la valeur 0 pour exécuter le package sans monter en charge. Ce paramètre est facultatif. Il est défini sur DEFAULT_EXECUTION_MODE dans [SSISDB]. [catalogue]. [catalog_properties] si non spécifié. Le *runinscaleout* est **bits**. 
 
 [ @useanyworker =] *useanyworker*  
  Indiquez si tout montée en puissance des processus de travail est autorisée à effectuer l’exécution. Utilisez la valeur 1 pour exécuter le package avec tout montée en puissance des processus de travail. Utilisez la valeur 0 pour indiquer que la mise à l’échelle pas toutes des travailleurs sont autorisés pour exécuter le package. Ce paramètre est facultatif. Il est défini sur 1, si n’est pas spécifié. Le *useanyworker* est **bits**. 
  
 [ @execution_id =] *execution_id*  
 Retourne l'identificateur unique d'une instance d'exécution. Le *execution_id* est **bigint**.  

  
## <a name="remarks"></a>Notes  
 Une exécution est utilisée pour spécifier les valeurs de paramètre qui sont utilisées par un package pendant une instance d'exécution unique du package.  
  
 Si une référence environnementale est spécifiée avec la *reference_id* paramètre, la procédure stockée remplit les paramètres de projet et de package avec des valeurs littérales ou des valeurs référencées à partir de variables d’environnement correspondantes. Si la référence environnementale est spécifiée, les valeurs de paramètre par défaut sont utilisées pendant l'exécution du package. Pour déterminer exactement quelles valeurs sont utilisées pour une instance particulière de l’exécution, utilisez la *execution_id* paramètre de sortie à partir de cette procédure stockée et la requête la [execution_parameter_values](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md) vue.  
  
 Seuls les packages marqués comme packages de point d'entrée peuvent être spécifiés dans une exécution. Si un package qui n'est pas un point d'entrée est spécifié, l'exécution échoue.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant appelle catalog.create_execution pour créer une instance d’exécution pour le package Child1.dtsx, ce qui n’est pas monter en charge. Project1 Integration Services contient le package. L'exemple appelle catalog.set_execution_parameter_value afin de définir des valeurs pour les paramètres Parameter1, Parameter2 et LOGGING_LEVEL. L'exemple appelle catalog.start_execution pour démarrer une instance d'exécution.  
  
```  
Declare @execution_id bigint  
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Child1.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'TestDeply4', @project_name=N'Integration Services Project1', @use32bitruntime=False, @reference_id=Null  
Select @execution_id  
DECLARE @var0 sql_variant = N'Child1.dtsx'  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=20, @parameter_name=N'Parameter1', @parameter_value=@var0  
DECLARE @var1 sql_variant = N'Child2.dtsx'  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=20, @parameter_name=N'Parameter2', @parameter_value=@var1  
DECLARE @var2 smallint = 1  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var2  
EXEC [SSISDB].[catalog].[start_execution] @execution_id  
GO  
  
```  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et EXECUTE sur le projet et, si applicable, autorisations READ sur les environnements référencés  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  

 Si @runinscaleout est 1, la procédure stockée requiert l’une des autorisations suivantes :
 
-   L’appartenance à la **ssis_admin** rôle de base de données

-   L’appartenance à la **ssis_cluster_executor** rôle de base de données

-   L’appartenance à la **sysadmin** rôle de serveur
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   Le package n’existe pas.  
  
-   L’utilisateur n’a pas les autorisations appropriées.  
  
-   La référence environnementale, *reference_id*, n’est pas valide.  
  
-   Le package spécifié n'est pas un package de point d'entrée.  
  
-   Le type de données de la variable d'environnement référencée est différent du type de données du paramètre du projet ou du package.  
  
-   Le projet ou le package contient des paramètres qui requièrent des valeurs, mais aucune valeur n'a été affectée.  
  
-   Les variables d’environnement référencée est introuvable dans l’environnement qui font référence à l’environnement, *reference_id*, spécifie.  
  
## <a name="see-also"></a>Voir aussi  
 [Catalog.start_execution &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md)   
 [catalog.set_execution_parameter_value &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
 [Catalog.add_execution_worker &#40; Base de données SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md)  
  


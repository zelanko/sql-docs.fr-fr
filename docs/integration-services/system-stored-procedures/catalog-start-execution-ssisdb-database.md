---
title: "Catalog.start_execution (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: f8663ff3-aa98-4dd8-b850-b21efada0b87
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 70359d539bc7b4fc6dd70de8bbb7e16be5d71208
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogstartexecution-ssisdb-database"></a>catalog.start_execution (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Démarre une instance d'exécution dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```tsql  
start_execution [ @execution_id = ] execution_id [, [@retry_count = ] retry_count]  
```  
  
## <a name="arguments"></a>Arguments  
 [ @execution_id =] *execution_id*  
 Identificateur unique de l'instance d'exécution. Le *execution_id* est **bigint**.
 
 [ @retry_count =] *tentatives*  
 Le nombre de tentatives en cas de l’exécution. Il prend effet uniquement si l’exécution se fait dans monter en charge. Ce paramètre est facultatif. Elle est définie sur 0, si n’est pas spécifié. Le *tentatives* est **int**.
  
## <a name="remarks"></a>Notes  
 Une exécution est utilisée pour spécifier les valeurs de paramètre qui seront utilisées par un package pendant une instance d'exécution unique du package. Le projet correspondant peut être redéployé une fois une instance d'exécution créée et avant son démarrage. Dans ce cas, l'instance d'exécution référencera un projet obsolète. Cela provoquera l'échec de la procédure stockée.  
  
> [!NOTE]  
>  Les exécutions peuvent être démarrées uniquement une fois. Pour démarrer une instance d’exécution, il doit être dans l’état créé (valeur `1` dans le **état** colonne de la [catalog.operations](../../integration-services/system-views/catalog-operations-ssisdb-database.md) affichage).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant appelle catalog.create_execution pour créer une instance d'exécution pour le package Child1.dtsx. Project1 Integration Services contient le package. L'exemple appelle catalog.set_execution_parameter_value afin de définir des valeurs pour les paramètres Parameter1, Parameter2 et LOGGING_LEVEL. L'exemple appelle catalog.start_execution pour démarrer une instance d'exécution.  
  
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
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur l'instance d'exécution, autorisations READ et EXECUTE sur le projet, et si applicable, autorisations READ sur l'environnement référencé  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   L’utilisateur ne dispose pas des autorisations appropriées  
  
-   L'identificateur d'exécution n'est pas valide.  
  
-   L'exécution a déjà démarré, ou a déjà été effectuée ; les exécutions peuvent être démarrées une seule fois  
  
-   La référence environnementale associée au projet n'est pas valide  
  
-   Les valeurs de paramètre obligatoires n'ont pas été définies  
  
-   La version du projet associée à l'instance d'exécution est obsolète ; seule la version la plus actuelle d'un projet peut être exécutée  
  
  


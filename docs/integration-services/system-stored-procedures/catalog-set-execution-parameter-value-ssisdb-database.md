---
title: "Catalog.set_execution_parameter_value (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 055d86c9-befd-4e63-acb1-6dfe833549d2
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 7b13e7b1c28bad6e573e829183372da4bb62f92d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="catalogsetexecutionparametervalue-ssisdb-database"></a>catalog.set_execution_parameter_value (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Définit la valeur d'un paramètre pour une instance d'exécution dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Une valeur de paramètre ne peut pas être modifiée après qu'une instance d'exécution a commencé.  
  
## <a name="syntax"></a>Syntaxe  
  
```tsql  
set_execution_parameter_value [ @execution_id = execution_id  
    , [ @object_type = ] object_type  
    , [ @parameter_name = ] parameter_name  
    , [ @parameter_value = ] parameter_value  
  
```  
  
## <a name="arguments"></a>Arguments  
 [ @execution_id =] *execution_id*  
 Identificateur unique de l'instance d'exécution. Le *execution_id* est **bigint**.  
  
 [ @object_type =] *object_type*  
 Le type de paramètre.  
  
 Pour les paramètres suivants, définissez *object_type* à 50  
  
-   LOGGING_LEVEL  
  
-   CUSTOMIZED_LOGGING_LEVEL  
  
-   DUMP_ON_ERROR  
  
-   DUMP_ON_EVENT  
  
-   DUMP_EVENT_CODE  
  
-   CALLER_INFO  
  
-   SYNCHRONIZED  
  
 Utilisez la valeur `20` pour indiquer un paramètre du projet ou la valeur `30` pour indiquer un paramètre du package.  
  
 Le *object_type* est **smallint**.  
  
 [ @parameter_name =] *nom_paramètre*  
 Nom du paramètre. Le *nom_paramètre* est **nvarchar (128)**.  
  
 [ @parameter_value =] *parameter_value*  
 Valeur du paramètre. Le *parameter_value* est **sql_variant**.  
  
## <a name="remarks"></a>Notes  
 Pour découvrir les valeurs de paramètre utilisées pour une exécution donnée, interrogez la vue catalog.execution_parameter_values.  
  
 Pour spécifier l’étendue des informations enregistrées lors d’une exécution de package, définissez *nom_paramètre* LOGGING_LEVEL et ensemble *parameter_value* à une des valeurs suivantes.  
  
 Définir le *object_type* paramètre à 50.  
  
|Valeur|Description|  
|-----------|-----------------|  
|0|Aucun<br /><br /> La journalisation est désactivée. Seul l'état d'exécution du package est enregistré.|  
|1|Basic<br /><br /> Tous les événements sont enregistrés, sauf les événements personnalisés et de diagnostic. Ceci est la valeur par défaut.|  
|2|Performance<br /><br /> Seules les statistiques de performances, et les événements OnError et OnWarning, sont enregistrés.|  
|3|Commentaires<br /><br /> Tous les événements sont enregistrés, y compris les événements personnalisés et de diagnostic. <br />Les événements personnalisés sont notamment ces événements consignés par les tâches Integration Services. Pour plus d’informations, consultez [pour la journalisation des Messages personnalisés](../../integration-services/performance/integration-services-ssis-logging.md#custom_messages)|  
|4|Lignage de l’exécution<br /><br /> Collecte les données nécessaires pour effectuer le suivi de lignage dans le flux de données.|  
|100|Niveau de journalisation personnalisés<br /><br /> Spécifiez les paramètres dans le paramètre CUSTOMIZED_LOGGING_LEVEL. Pour plus d’informations sur les valeurs que vous pouvez spécifier, consultez [catalog.create_customized_logging_level](../../integration-services/system-stored-procedures/catalog-create-customized-logging-level.md).<br /><br /> Pour plus d’informations sur les niveaux de journalisation personnalisés, consultez [activer la journalisation pour l’exécution du Package sur le serveur SSIS](../../integration-services/performance/integration-services-ssis-logging.md#server_logging).|  
  
 Pour spécifier que le serveur Integration Services doit générer des fichiers de vidage lorsqu'une erreur se produit pendant une exécution de package, définissez les valeurs de paramètre suivantes pour une instance d'exécution qui n'a pas été exécutée.  
  
|Paramètre|Valeur|  
|---------------|-----------|  
|*execution_id*|Identificateur unique de l'instance d'exécution|  
|*object_type*|50|  
|*nom_paramètre*|‘DUMP_ON_ERROR|  
|*parameter_value*|1|  
  
 Pour spécifier que le serveur Integration Services doit générer des fichiers de vidage lorsque des événements se produisent pendant une exécution de package, définissez les valeurs de paramètre suivantes pour une instance d'exécution qui n'a pas été exécutée.  
  
|Paramètre|Valeur|  
|---------------|-----------|  
|*execution_id*|Identificateur unique de l'instance d'exécution|  
|*object_type*|50|  
|*nom_paramètre*|‘DUMP_ON_EVENT|  
|*parameter_value*|1|  
  
 Pour spécifier les événements lors d'une exécution de package qui provoquent la génération de fichiers de vidage par le serveur Integration Services, définissez les valeurs de paramètre suivantes pour une instance d'exécution qui n'a pas été exécutée. Séparez plusieurs codes d'événement à l'aide d'un point-virgule.  
  
|Paramètre|Valeur|  
|---------------|-----------|  
|*execution_id*|Identificateur unique de l'instance d'exécution|  
|*object_type*|50|  
|*nom_paramètre*|DUMP_EVENT_CODE|  
|*parameter_value*|Un ou plusieurs codes d'événement|  
  
## <a name="example"></a>Exemple  
 L'exemple suivant spécifie que le serveur Integration Services doit générer des fichiers de vidage lorsqu'une erreur se produit pendant une exécution de package.  
  
```  
exec catalog.create_execution  'TR2','Recurring ETL', 'Dim_DCVendor.dtsx',NULL, 0,@execution_id out  
exec catalog.set_execution_parameter_value  @execution_id, 50, 'DUMP_ON_ERROR',1  
  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant spécifie que le serveur Integration Services doit générer des fichiers de vidage lorsque des événements se produisent pendant une exécution de package, et identifie l'événement qui provoque la génération des fichiers par le serveur.  
  
```  
exec catalog.create_execution  'TR2','Recurring ETL', 'Dim_DCVendor.dtsx',NULL, 0,@execution_id out  
exec catalog.set_execution_parameter_value  @execution_id, 50, 'DUMP_ON_EVENT',1  
  
declare @event_code nvarchar(50)  
set @event_code = '0xC020801C'  
exec catalog.set_execution_parameter_value  @execution_id, 50, 'DUMP_EVENT_CODE', @event_code  
```  
  
## <a name="return-code-value"></a>Valeur de Code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur l'instance d'exécution  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   L’utilisateur ne dispose pas des autorisations appropriées  
  
-   L'identificateur d'exécution n'est pas valide.  
  
-   Le nom du paramètre n'est pas valide.  
  
-   Le type de données de la valeur de paramètre ne correspond pas au type du paramètre.  
  
## <a name="see-also"></a>Voir aussi  
 [Catalog.execution_parameter_values &#40; Base de données SSISDB &#41;](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)   
 [Générer de fichiers de vidage pour l'exécution des packages](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  

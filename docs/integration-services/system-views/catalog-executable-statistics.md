---
title: catalog.executable_statistics | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 3dda28d6-10d8-4294-9b5e-a6048c07faf9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 79ef41fb52aa431325578195111ee9e4f451d9cf
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85673002"
---
# <a name="catalogexecutable_statistics"></a>catalog.executable_statistics 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Affiche une ligne pour chaque fichier exécutable exécuté, y compris chaque itération d'un fichier exécutable.  
  
 Un exécutable est une tâche ou un conteneur que vous ajoutez au flux de contrôle d'un package.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|Statistics_id|bigint|ID unique des données.|  
|Execution_id|bigint|ID unique de l'instance de l'exécution.<br /><br /> La vue catalog.executions fournit des informations supplémentaires sur les exécutions. Pour plus d’informations, consultez [catalog.executions &#40;base de données SSISDB&#41;](../../integration-services/system-views/catalog-executions-ssisdb-database.md).|  
|Executable_id|bigint|ID unique du composant de package.<br /><br /> La vue catalog.executables fournit des informations supplémentaires sur les fichiers exécutables. Pour plus d’informations, consultez [catalog.executables](../../integration-services/system-views/catalog-executables.md).|  
|Execution_path|nvarchar(max)|Chemin d'exécution complet du composant de package, y compris chaque itération du composant.|  
|Start_time|datetimeoffset(7)|Heure à laquelle le fichier exécutable entre dans la phase de pré-exécution.|  
|End_time|datetimeoffset(7)|Heure à laquelle le fichier exécutable entre dans la phase de post-exécution.|  
|Execution_duration|int|Durée passée par le fichier exécutable en phase d'exécution. Cette valeur est exprimée en millisecondes.|  
|Execution_result|SMALLINT|Les valeurs possibles sont les suivantes :<br /><br /> 0 (réussite)<br /><br /> 1 (échec)<br /><br /> 2 (achèvement)<br /><br /> 3 (annulé)|  
|Execution_value|sql_variant|Valeur retournée par l'exécution. Il s'agit d'une valeur définie par l'utilisateur.|  
  
## <a name="permissions"></a>Autorisations  
 La vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'instance de l'exécution.  
  
-   Appartenance au rôle de base de données **ssis_admin**.  
  
-   Appartenance au rôle serveur **sysadmin**.  
  
  

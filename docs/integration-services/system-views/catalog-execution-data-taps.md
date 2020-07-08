---
title: catalog.execution_data_taps | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 54226c01-5b8f-4730-8a5f-1da2613f9689
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3e9112883b7a85ed1ced0c3f5a7e061a396cbf31
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85672693"
---
# <a name="catalogexecution_data_taps"></a>catalog.execution_data_taps 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Affiche des informations pour chaque drainage de données défini dans une exécution.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|data_tap_id|**bigint**|Identificateur (ID) unique du drainage de données.|  
|execution_id|**bigint**|Identificateur unique (ID) de l'instance d'exécution.|  
|package_path|**nvarchar(max)**|Chemin d'accès au package pour la tâche de flux de données où les données sont drainées.|  
|dataflow_path_id_string|**nvarchar(4000)**|Chaîne d'identification du chemin d'accès de flux de données.|  
|dataflow_task_guid|**uniqueidentifier**|Identificateur (ID) unique de la tâche de flux de données.|  
|max_rows|**int**|Nombre de lignes à capturer. Si cette valeur n'est spécifiée, toutes les lignes sont capturées.|  
|filename|**nvarchar(4000)**|Nom du fichier de vidage de données. Pour plus d’informations, voir [Generating Dump Files for Package Execution](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md).|  
  
## <a name="permissions"></a>Autorisations  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'instance d'exécution  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
> [!NOTE]  
>  Lorsque vous avez l'autorisation pour effectuer une opération sur le serveur, vous avez également l'autorisation pour consulter les informations de l'opération. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
## <a name="see-also"></a>Voir aussi  
 [Générer de fichiers de vidage pour l’exécution des packages](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  

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
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fe54f3560c0c4584dcf7c9f84864a3552ed23172
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65714783"
---
# <a name="catalogexecutiondatataps"></a>catalog.execution_data_taps 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche des informations pour chaque drainage de données défini dans une exécution.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|data_tap_id|**bigint**|Identificateur (ID) unique du drainage de données.|  
|execution_id|**bigint**|Identificateur unique (ID) de l'instance d'exécution.|  
|package_path|**nvarchar(max)**|Chemin d'accès au package pour la tâche de flux de données où les données sont drainées.|  
|dataflow_path_id_string|**nvarchar(4000)**|Chaîne d'identification du chemin d'accès de flux de données.|  
|dataflow_task_guid|**uniqueidentifier**|Identificateur (ID) unique de la tâche de flux de données.|  
|max_rows|**Int**|Nombre de lignes à capturer. Si cette valeur n'est spécifiée, toutes les lignes sont capturées.|  
|filename|**nvarchar(4000)**|Nom du fichier de vidage de données. Pour plus d’informations, voir [Generating Dump Files for Package Execution](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md).|  
  
## <a name="permissions"></a>Autorisations  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'instance d'exécution  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
> [!NOTE]  
>  Lorsque vous avez l'autorisation pour effectuer une opération sur le serveur, vous avez également l'autorisation pour consulter les informations de l'opération. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
## <a name="see-also"></a> Voir aussi  
 [Générer de fichiers de vidage pour l’exécution des packages](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  

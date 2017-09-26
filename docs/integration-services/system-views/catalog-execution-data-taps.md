---
title: Catalog.execution_data_taps | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 54226c01-5b8f-4730-8a5f-1da2613f9689
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: bc949b9b6111c65d6faa43a118efd03068630fe0
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogexecutiondatataps"></a>catalog.execution_data_taps
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche des informations pour chaque drainage de données défini dans une exécution.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|data_tap_id|**bigint**|Identificateur (ID) unique du drainage de données.|  
|execution_id|**bigint**|Identificateur unique (ID) de l'instance d'exécution.|  
|package_path|**nvarchar(max)**|Chemin d'accès au package pour la tâche de flux de données où les données sont drainées.|  
|dataflow_path_id_string|**nvarchar(4000)**|Chaîne d'identification du chemin d'accès de flux de données.|  
|dataflow_task_guid|**uniqueidentifier**|Identificateur (ID) unique de la tâche de flux de données.|  
|max_rows|**int**|Nombre de lignes à capturer. Si cette valeur n'est spécifiée, toutes les lignes sont capturées.|  
|filename|**nvarchar(4000)**|Nom du fichier de vidage de données. Pour plus d’informations, voir [Generating Dump Files for Package Execution](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md).|  
  
## <a name="permissions"></a>Permissions  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'instance d'exécution  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
> [!NOTE]  
>  Lorsque vous avez l'autorisation pour effectuer une opération sur le serveur, vous avez également l'autorisation pour consulter les informations de l'opération. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
## <a name="see-also"></a>Voir aussi  
 [Générer de fichiers de vidage pour l’exécution des packages](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  

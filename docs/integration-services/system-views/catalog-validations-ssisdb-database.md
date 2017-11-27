---
title: "Catalog.validations (base de données SSISDB) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: dbafe110-b480-48f3-b45f-31d71ca68f62
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 2d799fd23c2adef75e3dcf4543e9e0ee6271c9b5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogvalidations-ssisdb-database"></a>catalog.validations (base de données SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Affiche les détails de toutes les validations du package et du projet dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|validation_id|**bigint**|Identificateur (ID) unique de la validation.|  
|environment_scope|**Char (1)**|Indique les références environnementales considérées par la validation. Lorsque la valeur est `A`, toutes les références environnementales associées au projet sont incluses dans la validation. Lorsque la valeur est `S`, seule une référence environnementale unique est incluse. Lorsque la valeur est `D`, aucune référence environnementale n'est incluse et chaque paramètre doit avoir une valeur par défaut littérale pour passer la validation.|  
|validate_type|**Char (1)**|Le type de validation à effectuer. Les types de validation possibles sont la validation de dépendance (`D`) ou la validation complète (`F`). La validation du package est toujours une validation complète.|  
|nom_dossier|**nvarchar (128)**|Nom du dossier qui contient le projet correspondant.|  
|PROJECT_NAME|**nvarchar (128)**|Nom du projet.|  
|project_lsn|**bigint**|Version du projet validé.|  
|use32bitruntime|**bit**|Indique si l'exécution 32 bits est utilisée pour exécuter le package sur un système d'exploitation 64 bits. Lorsque la valeur est `1`, l’exécution est effectuée avec le runtime 32 bits. Lorsque la valeur est `0`, l'exécution 64 bits est utilisée.|  
|reference_id|**bigint**|ID unique de la référence d'environnement de projet utilisée par le projet pour référencer un environnement.|  
|type_opération|**smallint**|Le type d’opération. Les opérations affichées dans cette vue incluent la validation de projet (`300`) et la validation du package (`301`).|  
|object_name|**nvarhcar(260)**|Nom de l'objet.|  
|object_type|**smallint**|Type de l'objet. L'objet peut être un projet (`20`) ou un package (`30`).|  
|object_id|**bigint**|ID de l'objet affecté par l'opération.|  
|start_time|**DateTimeOffset(7)**|Heure de début de l'opération, si disponible.|  
|end_time|**datetimeoffsset(7)**|Heure à laquelle l'opération s'est terminée.|  
|status|**int**|État de l'opération. Les valeurs possibles sont Créé (`1`), En cours d'exécution (`2`), Annulé (`3`), Échec (`4`), En attente (`5`), Arrêté prématurément (`6`), Opération réussie (`7`), Arrêt en cours (`8`) et Fin (`9`).|  
|caller_sid|**varbinary(85)**|ID de sécurité (SID) de l'utilisateur si l'Authentification Windows a été utilisée pour se connecter.|  
|caller_name|**nvarchar (128)**|Nom du compte qui a effectué l'opération.|  
|process_id|**int**|ID de processus externe, le cas échéant.|  
|stopped_by_sid|**varbinary(85)**|SID de l'utilisateur qui a arrêté l'opération.|  
|stopped_by_name|**nvarchar (128)**|Nom de l'utilisateur qui a arrêté l'opération.|  
|server_name|**nvarchar (128)**|Informations relatives à l'instance et au serveur Windows pour une instance spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|machine_name|**nvarchar (128)**|Nom de l'ordinateur sur lequel s'exécute l'instance du serveur.|  
|dump_id|**uniqueidentifier**|ID du vidage d'exécution.|  
  
## <a name="remarks"></a>Notes  
 Cette vue affiche une ligne pour chaque validation dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="permissions"></a>Permissions  
 Cette vue requiert l'une des autorisations suivantes :  
  
-   Autorisation READ sur l'opération correspondante  
  
-   L’appartenance à la **ssis_admin** rôle de base de données  
  
-   L’appartenance à la **sysadmin** rôle de serveur  
  
> [!NOTE]  
>  Lorsque vous avez l'autorisation pour effectuer une opération sur le serveur, vous avez également l'autorisation pour consulter les informations de l'opération. La sécurité au niveau de la ligne est imposée ; uniquement les lignes que vous avez l'autorisation d'afficher s'affichent.  
  
  


---
title: Sys.dm_external_script_requests | Microsoft Docs
ms.custom: ''
ms.date: 10/28/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_external_script_requests
- sys.dm_external_script_requests_TSQL
- dm_external_script_requests
- dm_external_script_requests_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_external_script_requests dynamic management view
ms.assetid: e7e7c50f-b8b2-403c-b8c8-1955da5636c3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 54c572acac645146e3db18195a0dbe5b794effdc
ms.sourcegitcommit: c2322c1a1dca33b47601eb06c4b2331b603829f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50743187"
---
# <a name="sysdmexternalscriptrequests"></a>Sys.dm_external_script_requests
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

Renvoie une ligne pour chaque compte de travail actif qui exécute un script externe.
  
> [!NOTE] 
>  
> Cette vue de gestion dynamique (DMV) est disponible uniquement si vous avez installé et activé la fonctionnalité qui prend en charge l’exécution du script externe. Pour plus d’informations, consultez [R Services dans SQL Server 2016](../../advanced-analytics/r/sql-server-r-services.md) et [Machine Learning Services (R, Python) dans SQL Server 2017](../../advanced-analytics/what-is-sql-server-machine-learning.md).  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|external_script_request_id|**Identificateur unique**|ID du processus qui a envoyé la demande de script externe. Cela correspond à l’ID de processus, comme reçu par [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]|  
|langue|**nvarchar**|Mot clé qui représente un langage de script pris en charge. |  
|degree_of_parallelism|**Int**|Nombre indiquant le nombre de traitements parallèles qui ont été créés. Cette valeur peut être différente du nombre de traitements parallèles qui ont été demandés.|  
|external_user_name|**nvarchar**|Le compte de travail Windows sous lequel le script a été exécuté.|  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation VIEW SERVER STATE sur le serveur.  
  
> [!NOTE]
>   
>  Les utilisateurs qui exécutent des scripts externes doivent avoir l’autorisation supplémentaire EXECUTE ANY EXTERNAL SCRIPT, toutefois, cette vue de gestion dynamique peut être utilisée par les administrateurs sans cette autorisation. 
  
## <a name="remarks"></a>Notes  

Cette vue peut être filtrée à l’aide de l’identificateur de langage de script.

La vue renvoie également le compte de travail sous lequel le script est en cours d’exécution. Pour plus d’informations sur les comptes de travail utilisés par les scripts externes, consultez les identités utilisées dans le traitement de la section (SQLRUserGroup) dans [vue d’ensemble de la sécurité pour l’infrastructure d’extensibilité dans SQL Server Machine Learning Services](../../advanced-analytics/concepts/security.md#sqlrusergroup).

Le GUID renvoyé dans le champ **external_script_request_id** représente également le nom de fichier du répertoire sécurisé où sont stockés les fichiers temporaires. Chaque compte de travail, tel que MSSQLSERVER01 représente une connexion SQL unique ou un utilisateur Windows et peut être utilisé pour exécuter plusieurs demandes de script. Par défaut, ces fichiers temporaires sont nettoyés après l’achèvement du script demandé.
 
Cette vue de gestion dynamique surveille uniquement les processus actifs et ne peut pas générer de rapports sur des scripts déjà effectués. Si vous avez besoin de suivre la durée des scripts, nous vous recommandons d’ajouter des informations de durée à votre script et de les capturer dans le cadre de l’exécution du script.

## <a name="examples"></a>Exemples  
  
### <a name="viewing-the-currently-active-r-scripts-for-a-particular-process"></a>Afficher les scripts R actuellement actifs pour un processus particulier 
 L’exemple suivant affiche le nombre d’exécutions de scripts externes en cours d’exécution sur l’instance actuelle.  
  
```  
SELECT external_script_request_id 
  , [language]
  , degree_of_parallelism
  , external_user_name
FROM sys.dm_external_script_requests; 
```  

Résultats  


external_script_request_id  |langue  |degree_of_parallelism  |external_user_name  
---------|---------|---------|---------
183EE6FC-7399-4318-AA2E-7A6C68E435A8     |     R    |      1   |  MSSQLSERVER01       


  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Fonctions et vues de gestion dynamique relatives aux exécutions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
[sys.dm_external_script_execution_stats](../../relational-databases/system-dynamic-management-views/sys-dm-external-script-execution-stats.md)
[sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)  
  


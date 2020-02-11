---
title: syscollector_execution_log_full (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syscollector_execution_log_full
- syscollector_execution_log_full_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector view
- syscollector_execution_log_full view
ms.assetid: 6c8db22d-2e4c-4b7c-ac5a-8762ef1b175b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4bcbbf3d4e0e0b77156b7adceedbdc5aad97afdc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68060366"
---
# <a name="syscollector_execution_log_full-transact-sql"></a>syscollector_execution_log_full (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit des informations sur un jeu d'éléments de collecte ou package lorsque le journal des exécutions est saturé.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|log_id|**bigint**|Identifie chaque exécution de jeu d'éléments de collecte. Utilisé pour joindre cette vue à d'autres journaux détaillés. Autorise la valeur NULL.|  
|parent_log_id|**bigint**|Identifie le package parent ou jeu d'éléments de collecte. N'accepte pas la valeur NULL. Les ID sont chaînés dans la relation parent-enfant, ce qui vous permet de déterminer quel package a été démarré par quel jeu d'éléments de collecte. Cette vue regroupe les entrées de journal par leur liaison parent-enfant et met en retrait les noms des packages afin que la chaîne d’appel soit clairement visible.|  
|name|**nvarchar(4000)**|Nom du jeu d'éléments de collecte ou du package que cette entrée de journal représente. Autorise la valeur NULL.|  
|status|**smallint**|Indique l'état actuel du jeu d'éléments de collecte ou package. Autorise la valeur NULL.<br /><br /> Les valeurs sont les suivantes :<br /><br /> 0 = En cours d'exécution<br /><br /> 1 = Terminé<br /><br /> 2 = échec|  
|runtime_execution_mode|**smallint**|Indique si l'activité du jeu d'éléments de collecte consistait à collecter ou à télécharger des données. Autorise la valeur NULL.|  
|start_time|**DATETIME**|Heure de démarrage du jeu d'éléments de collecte ou package. Autorise la valeur NULL.|  
|last_iteration_time|**DATETIME**|Pour des packages exécutés en permanence, dernière fois où le package a effectué un instantané. Autorise la valeur NULL.|  
|finish_time|**DATETIME**|Heure de fin de l'exécution pour les packages et jeux d'éléments de collecte terminés. Autorise la valeur NULL.|  
|duration|**int**|Durée d'exécution, en secondes, du package ou jeu d'éléments de collecte. Autorise la valeur NULL.|  
|failure_message|**nvarchar (2048)**|En cas d'échec du jeu d'éléments de collecte ou du package, message d'erreur le plus récent pour ce composant. Autorise la valeur NULL. Pour obtenir des informations d’erreur plus détaillées, utilisez la fonction [Transact-SQL&#41;fn_syscollector_get_execution_details &#40;](../../relational-databases/system-functions/fn-syscollector-get-execution-details-transact-sql.md) .|  
|operator|**nvarchar(128)**|Identifie la personne qui a démarré le jeu d'éléments de collecte ou package. Autorise la valeur NULL.|  
|package_execution_id|**uniqueidentifier**|Fournit un lien vers la table de journal [!INCLUDE[ssIS](../../includes/ssis-md.md)]. Autorise la valeur NULL.|  
|collection_set_id|**int**|Fournit un lien vers la table de configuration de collecte de données dans msdb. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 Requiert SELECT pour **dc_operator**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [Vues du collecteur de données &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)   
 [Collecte de données](../../relational-databases/data-collection/data-collection.md)  
  
  

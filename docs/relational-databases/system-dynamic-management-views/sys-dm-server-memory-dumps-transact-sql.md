---
title: Sys.dm_server_memory_dumps (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_server_memory_dumps_TSQL
- dm_server_memory_dumps_TSQL
- dm_server_memory_dumps
- sys.dm_server_memory_dumps
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_memory_dumps dynamic management view
ms.assetid: 41782719-f54d-4e11-941a-c050c7576e23
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0b1ec6c19344939db7c97870c024f08751cc90c0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sysdmservermemorydumps-transact-sql"></a>sys.dm_server_memory_dumps (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie une ligne pour chaque fichier de vidage de mémoire généré par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Utilisez cette vue de gestion dynamique pour résoudre les problèmes potentiels.  
 
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**filename**|**nvarchar (256)**|Chemin d'accès et nom du fichier de vidage de mémoire. Ne peut pas avoir la valeur null.|  
|**creation_time**|**datetimeoffset(7)**|Date et heure de création du fichier. Ne peut pas avoir la valeur null.|  
|**size_in_bytes**|**bigint**|Taille (en octets) du fichier. Autorise la valeur NULL.|  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Le type de vidage peut être un minidump, un vidage de tous les threads ou un vidage complet. Les fichiers portent l'extension .mdmp.  
  
## <a name="security"></a>Sécurité  
 Les fichiers de vidage peuvent contenir des informations sensibles. Pour protéger les informations sensibles, vous pouvez utiliser une liste de contrôle d'accès (ACL) afin de restreindre l'accès aux fichiers ou copier les fichiers dans un dossier avec accès limité. Par exemple, avant d’envoyer que vos fichiers de débogage à Microsoft les services de support technique, nous vous recommandons de supprimer toutes les informations sensibles ou confidentielles.  
  
### <a name="permissions"></a>Autorisations  
 Requiert l'autorisation VIEW SERVER STATE.  
  
  

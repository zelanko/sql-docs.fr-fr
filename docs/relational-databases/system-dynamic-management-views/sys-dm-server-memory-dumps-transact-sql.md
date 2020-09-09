---
description: sys.dm_server_memory_dumps (Transact-SQL)
title: sys. dm_server_memory_dumps (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: cec8575270fd7068290cb24f88405453415b3020
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543825"
---
# <a name="sysdm_server_memory_dumps-transact-sql"></a>sys.dm_server_memory_dumps (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Renvoie une ligne pour chaque fichier de vidage de mémoire généré par le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Utilisez cette vue de gestion dynamique pour résoudre les problèmes potentiels.  
 
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**extension**|**nvarchar (256)**|Chemin d'accès et nom du fichier de vidage de mémoire. Ne peut pas être null.|  
|**creation_time**|**datetimeoffset(7)**|Date et heure de création du fichier. Ne peut pas être null.|  
|**size_in_bytes**|**bigint**|Taille (en octets) du fichier. Autorise la valeur NULL.|  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Le type de vidage peut être un minidump, un vidage de tous les threads ou un vidage complet. Les fichiers portent l'extension .mdmp.  
  
## <a name="security"></a>Sécurité  
 Les fichiers de vidage peuvent contenir des informations sensibles. Pour protéger les informations sensibles, vous pouvez utiliser une liste de contrôle d'accès (ACL) afin de restreindre l'accès aux fichiers ou copier les fichiers dans un dossier avec accès limité. Par exemple, avant d’envoyer vos fichiers de débogage aux services de support technique Microsoft, nous vous recommandons de supprimer toutes les informations sensibles ou confidentielles.  
  
### <a name="permissions"></a>Autorisations  
 Requiert l'autorisation VIEW SERVER STATE.  
  
  

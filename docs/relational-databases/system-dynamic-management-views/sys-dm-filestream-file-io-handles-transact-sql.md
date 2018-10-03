---
title: Sys.dm_filestream_file_io_handles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_filestream_file_io_handles
- sys.dm_filestream_file_io_handles
- dm_filestream_file_io_handles_TSQL
- sys.dm_filestream_file_io_handles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_filestream_file_io_handle catalog view
ms.assetid: e59632f4-3292-419f-9217-ca375749f1a5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cde19779c178b8064e6b20a3ae39bbfb7f5b96f6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47847157"
---
# <a name="sysdmfilestreamfileiohandles-transact-sql"></a>sys.dm_filestream_file_io_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche les descripteurs de fichiers connus par le propriétaire de l'espace de noms (NSO, Namespace Owner). Handles de FileStream un client obtient à l’aide **OpenSqlFilestream** sont affichés par cette vue.  
  
|colonne|Type|Description|  
|------------|----------|-----------------|  
|**handle_context_address**|**varbinary(8)**|Affiche l'adresse de la structure NSO interne associée au handle du client. Autorise la valeur NULL.|  
|**creation_request_id**|**Int**|Affiche un champ de la requête d'E/S REQ_PRE_CREATE utilisé pour créer ce handle. N'accepte pas la valeur NULL.|  
|**creation_irp_id**|**Int**|Affiche un champ de la requête d'E/S REQ_PRE_CREATE utilisé pour créer ce handle. N'accepte pas la valeur NULL|  
|**handle_id**|**Int**|Affiche l'ID unique de ce handle qui est attribué par le pilote. N'accepte pas la valeur NULL.|  
|**creation_client_thread_id**|**varbinary(8)**|Affiche un champ de la requête d'E/S REQ_PRE_CREATE utilisé pour créer ce handle. Autorise la valeur NULL.|  
|**creation_client_process_id**|**varbinary(8)**|Affiche un champ de la requête d'E/S REQ_PRE_CREATE utilisé pour créer ce handle. Autorise la valeur NULL.|  
|**filestream_transaction_id**|**varbinary(128)**|Affiche l'ID de la transaction associée au handle donné. C’est la valeur retournée par la **get_filestream_transaction_context** (fonction). Ce champ permet de joindre à la **sys.dm_filestream_file_io_requests** vue. Autorise la valeur NULL.|  
|**access_type**|**nvarchar(60)**|N'accepte pas la valeur NULL.|  
|**logical_path**|**nvarchar (256)**|Affiche le nom de chemin d'accès logique du fichier ouvert par ce handle. Il s’agit du même chemin d’accès qui est retourné par la **. Chemin d’accès** méthode de **varbinary**(**max**) filestream. Autorise la valeur NULL.|  
|**chemin physique**|**nvarchar (256)**|Affiche le nom de chemin d'accès NTFS réel du fichier. Il s’agit du même chemin d’accès retourné par la **. PhysicalPathName** méthode de la **varbinary**(**max**) filestream. Il est activé par l'indicateur de suivi 5556. Autorise la valeur NULL.|  
  
## <a name="permissions"></a>Permissions  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [FileStream et des vues de gestion dynamique FileTable &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)  
  
  

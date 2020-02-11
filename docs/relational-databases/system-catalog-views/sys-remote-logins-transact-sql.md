---
title: sys. remote_logins (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.remote_logins_TSQL
- remote_logins
- remote_logins_TSQL
- sys.remote_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_logins catalog view
ms.assetid: 38477e91-d084-4df7-b1de-b930c5580189
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 371f8e2bf9a5d67d68e9c1d48502bf3fa2f81db6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67904575"
---
# <a name="sysremote_logins-transact-sql"></a>sys.remote_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne par mappage de connexions à distance. Cette vue de catalogue est utilisée pour mapper les connexions locales entrantes issues d'un serveur correspondant et accédant à une connexion locale.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|ID du serveur dans **sys.** Servers. Le nom est fourni par la connexion à partir du serveur « distant ».|  
|**remote_name**|**sysname**|Nom de connexion fourni pour un mappage. Si la valeur est NULL, le nom de connexion spécifié dans la connexion est utilisé.|  
|**local_principal_id**|**int**|ID du principal de serveur auquel la connexion est mappée. Si la valeur est 0, la connexion distante est mappée à la connexion portant le même nom.|  
|**modify_date**|**DATETIME**|Date de la dernière modification de la connexion liée.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue des serveurs liés &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)   
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  

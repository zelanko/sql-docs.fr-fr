---
title: Sys.linked_logins (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.linked_logins
- sys.linked_logins_TSQL
- linked_logins_TSQL
- linked_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.linked_logins catalog view
ms.assetid: af57bf0c-a265-410f-9bab-63b78569b4a6
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 712d5286036aa8fbf375d16abfbe3a3c2257ab91
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47683348"
---
# <a name="syslinkedlogins-transact-sql"></a>sys.linked_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne une ligne par mappage de connexion de serveur lié dans le but d'utiliser ce mappage dans les requêtes RPC et les requêtes distribuées en provenance du serveur local et à destination du serveur lié correspondant.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**Int**|ID du serveur dans **sys.servers**.|  
|**local_principal_id**|**Int**|Serveur principal auquel s'applique le mappage.<br /><br /> 0 = générique ou public.|  
|**uses_self_credential**|**bit**|Si la valeur de la colonne est égale à 1, le mappage indique que la session doit utiliser ses propres informations d'identification ; la valeur 0 indique que la session utilise les nom et mot de passe fournis.|  
|**nom_distant**|**sysname**|Nom utilisateur distant servant à la connexion. Le mot de passe est également stocké mais n'est pas exposé dans les interfaces des vues de catalogue.|  
|**modify_date**|**datetime**|Date de la dernière modification de la connexion liée.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue de serveurs liés &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)  
  
  

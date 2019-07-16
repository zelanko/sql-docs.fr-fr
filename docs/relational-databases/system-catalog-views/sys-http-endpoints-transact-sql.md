---
title: Sys.http_endpoints (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.http_endpoints
- http_endpoints
- sys.http_endpoints_TSQL
- http_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.http_endpoints catalog view
ms.assetid: 16f59695-ecd9-457e-8874-055af63f8ea7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 41ca717399a3cd86f2137de6ae474d89e3eb819e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122730"
---
# <a name="syshttpendpoints-transact-sql"></a>sys.http_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient une ligne pour chaque point de terminaison créé sur le serveur qui utilise le protocole HTTP.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**< colonnes héritées >**||Hérite des colonnes de [sys.endpoints &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**site**|**nvarchar(128)**|Nom de l'ordinateur hôte du site, tel qu'il est spécifié dans l'option SITE =.|  
|**url_path**|**nvarchar(4000)**|Portion du chemin d'accès uniquement de ce point de terminaison HTTP, comme le spécifie l'option PATH=.|  
|**is_clear_port_enabled**|**bit**|1 = Activation du port en clair à l'aide de l'option PORT = CLEAR.|  
|**clear_port**|**int**|Numéro de port spécifié dans l'option CLEAR PORT =.<br /><br /> NULL = Non spécifié.|  
|**is_ssl_port_enabled**|**bit**|1 = Activation du port SSL à l'aide de l'option PORT = SSL.|  
|**ssl_port**|**int**|Numéro de port spécifié dans l'option SSL PORT =.<br /><br /> NULL = Non spécifié.|  
|**is_anonymous_enabled**|**bit**|1 = Activation de l'accès anonyme à l'aide de l'option AUTHENTICATION = ANONYMOUS.|  
|**is_basic_auth_enabled**|**bit**|1 = Activation de l'authentification de base à l'aide de l'option AUTHENTICATION = BASIC.|  
|**is_digest_auth_enabled**|**bit**|1 = Activation de l'authentification de type Digest à l'aide de l'option AUTHENTICATION = DIGEST.|  
|**is_kerberos_auth_enabled**|**bit**|1 = Activation de l'authentification intégrée à l'aide de l'option AUTHENTICATION = KERBEROS.|  
|**is_ntlm_auth_enabled**|**bit**|1 = Activation de l'authentification intégrée à l'aide de l'option AUTHENTICATION = NTLM.|  
|**is_integrated_auth_enabled**|**bit**|1 = Activation de l'authentification intégrée à l'aide de l'option AUTHENTICATION = INTEGRATED.|  
|**authorization_realm**|**nvarchar(128)**|Indicateur retourné au client dans le cadre de la vérification de l'authentification DIGEST HTTP. Valeur de l'option AUTH REALM.<br /><br /> NULL si non spécifié ou si l'authentification DIGEST n'est pas activée.|  
|**default_logon_domain**|**nvarchar(128)**|Domaine de connexion par défaut si vous activez l'authentification de base. Valeur de l'option DEFAULT LOGON DOMAIN.<br /><br /> NULL si non spécifié ou si l'authentification de base n'est pas activée.|  
|**is_compression_enabled**|**bit**|1 = L'option COMPRESSION = ENABLED est définie.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Affichages catalogue de points de terminaison &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  

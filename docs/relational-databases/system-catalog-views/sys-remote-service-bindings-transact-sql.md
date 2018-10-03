---
title: Sys.remote_service_bindings (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.remote_service_bindings_TSQL
- remote_service_bindings_TSQL
- remote_service_bindings
- sys.remote_service_bindings
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_service_bindings catalog view
ms.assetid: 4e1a885d-eed1-4993-9c87-e6fd781f437d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 2a0b326eef888ebf36fded7ae4ab95fe9f1b6bc0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47785197"
---
# <a name="sysremoteservicebindings-transact-sql"></a>sys.remote_service_bindings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cet affichage catalogue contient une ligne pour chaque liaison de service distant. 
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom de la liaison de service distant. Cette colonne n'accepte pas la valeur NULL.|  
|**remote_service_binding_id**|**Int**|Identificateur de la liaison de service distant. Cette colonne n'accepte pas la valeur NULL.|  
|**principal_id**|**Int**|Identificateur du principal de base de données qui est propriétaire de la liaison de service distant. Accepte la valeur NULL.|  
|**remote_service_name**|**nvarchar (256)**|Nom du service distant auquel cette liaison s'applique. Accepte la valeur NULL.|  
|**service_contract_id**|**Int**|Identificateur du contrat auquel cette liaison s'applique. La valeur 0 est un caractère générique signifiant que la liaison s'applique à tous les contrats associés au service. Cette colonne n'accepte pas la valeur NULL.|  
|**remote_principal_id**|**Int**|Identificateur de l'utilisateur spécifié dans la liaison de service distant. Service Broker utilise un certificat appartenant à cet utilisateur pour communiquer avec le service spécifié sur les contrats concernés. Accepte la valeur NULL.|  
|**is_anonymous_on**|**bit**|Cette liaison de service distant utilise la sécurité ANONYMOUS. L'identité de l'utilisateur qui commence la conversation n'est pas fournie au service cible. Cette colonne n'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  

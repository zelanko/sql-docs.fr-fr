---
title: sys. services (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.services
- services
- services_TSQL
- sys.services_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.services catalog view
ms.assetid: 16d0b0c5-5cce-469b-aa3d-4b9248e0c085
author: stevestein
ms.author: sstein
ms.openlocfilehash: c19e65117a03de6b473eced3c7c1379943c851a7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68078659"
---
# <a name="sysservices-transact-sql"></a>sys.services (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cet affichage catalogue contient une ligne pour chaque service de la base de données.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nom du service qui respecte la casse, unique au sein de la base de données. Cette colonne n'accepte pas la valeur NULL.|  
|**service_id**|**int**|ID du service. Cette colonne n'accepte pas la valeur NULL.|  
|**principal_id**|**int**|Identificateur du principal de base de données qui est propriétaire du service. Accepte la valeur NULL.|  
|**service_queue_id**|**int**|Identificateur d'objet associé à la file d'attente utilisée par le service. Cette colonne n'accepte pas la valeur NULL.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  

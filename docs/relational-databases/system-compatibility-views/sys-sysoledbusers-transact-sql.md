---
title: sys. sysoledbusers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sysoledbusers
- sys.sysoledbusers_TSQL
- sysoledbusers
- sysoledbusers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysoledbusers system table
- sys.sysoledbusers compatibility view
ms.assetid: fe924c17-9cad-4b2b-8124-1e0fd82931e3
author: rothja
ms.author: jroth
ms.openlocfilehash: d7c8b97a04e8b9898a9d49a412c5c6e5a2aa910c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076533"
---
# <a name="syssysoledbusers-transact-sql"></a>sys.sysoledbusers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  Cette table système [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] est incluse dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en tant que vue seulement pour des raisons de compatibilité descendante. Nous vous recommandons d’utiliser à la place des [affichages catalogue](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md) .  
  
 Contient une ligne pour chaque mappage d'utilisateur et de mot de passe pour le serveur lié spécifié. **sysoledbusers** est stocké dans la base de données **Master** .  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**rmtsrvid**|**smallint**|Numéro d'identification de sécurité (SID) du serveur.|  
|**rmtloginame**|**nvarchar (** 128 **)**|Nom de la connexion distante avec laquelle **LoginSid** mappe pour **rmtservid**lié.|  
|**rmtpassword**|**nvarchar (** 128 **)**|Renvoie NULL.|  
|**LoginSid**|**varbinary (** 85 **)**|SID de la connexion locale à mapper.|  
|**statu**|**smallint**|Si la valeur est 1, le mappage doit utiliser les informations d'identification de l'utilisateur.|  
|**ChangeDate**|**DATETIME**|Date de la dernière modification des informations de mappage.|  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Vues de compatibilité &#40;&#41;Transact-SQL](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  

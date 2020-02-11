---
title: sys. server_triggers (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_triggers
- sys.server_triggers_TSQL
- server_triggers_TSQL
- sys.server_triggers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_triggers catalog view
ms.assetid: 25926ff4-9271-45bf-bc32-d5d3344bd47a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 995a9b5fe4786e1e188a8bbdc612cce743e77a18
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68133011"
---
# <a name="sysserver_triggers-transact-sql"></a>sys.server_triggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Contient l'ensemble de tous les déclencheurs DDL de niveau serveur avec un type object_type de valeur TR ou TA. Dans le cas des déclencheurs CLR, l’assembly doit être chargé dans la base de données **Master** . Tous les noms de déclencheurs DDL au niveau du serveur existent dans une étendue unique et globale.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nomme**|**sysname**|Nom du déclencheur.|  
|**object_id**|**int**|ID de l'objet.|  
|**parent_class**|**tinyint**|Classe du parent. Est toujours :<br /><br /> 100 = serveur|  
|**parent_class_desc**|**nvarchar (60)**|Description d'une classe de parent. Est toujours :<br /><br /> SERVER.|  
|**parent_id**|**int**|Toujours 0 pour les déclencheurs sur SERVER.|  
|**entrer**|**Char (2)**|Type d’objet :<br /><br /> TA = Déclencheur assembly (CLR)<br /><br /> TR = Déclencheur SQL|  
|**type_desc**|**nvarchar (60)**|Description de la classe du type d'objet.<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**create_date**|**DATETIME**|Date de création du déclencheur.|  
|**modify_date**|**DATETIME**|Date de la dernière modification du déclencheur à l'aide de l'instruction ALTER.|  
|**is_ms_shipped**|**bit**|Déclencheur créé pour l'utilisateur par un composant [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interne.|  
|**is_disabled**|**bit**|1 = Déclencheur désactivé.|  
  
## <a name="permissions"></a>Autorisations  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Pour plus d'informations, consultez [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Affichages catalogue &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  

---
title: sp_getmergedeletetype (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_getmergedeletetype
- sp_getmergedeletetype_TSQL
helpviewer_keywords:
- sp_getmergedeletetype
ms.assetid: 64450e4d-844d-4176-874e-f3845536f7d2
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 96258cb01e49c3d0b3fc2b83960e7d4aff6b64a1
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43027756"
---
# <a name="spgetmergedeletetype-transact-sql"></a>sp_getmergedeletetype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie le type de suppression de fusion. Cette procédure stockée est exécutée sur le serveur de publication sur la base de données de publication ou sur l’abonné sur la base de données d’abonnement.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_getmergedeletetype [ @source_object = ] 'source_object', [ @rowguid =] 'rowguid', [ @delete_type=] delete_type OUTPUT  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@source_object =**] **'***source_object***'**  
 Est le nom de l’objet source. *source_object* est **nvarchar (386)**, sans valeur par défaut.  
  
 [  **@rowguid=**] **'***rowguid***'**  
 Identificateur de ligne pour le type de suppression. *ROWGUID* est **uniqueidentifier**, sans valeur par défaut.  
  
 [  **@delete_type=**] *type_de_suppression* **sortie**  
 Code indiquant le type de suppression. *type_de_suppression* est **int**, sans valeur par défaut. *type_de_suppression* est également un paramètre de sortie, et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**1**|Suppression par l'utilisateur|  
|**5**|Suppression partielle|  
|**6**|Suppression par le système|  
  
## <a name="remarks"></a>Notes  
 **sp_getmergedeletetype** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **db_owner** rôle de base de données fixe peuvent exécuter **sp_getmergedeletetype**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

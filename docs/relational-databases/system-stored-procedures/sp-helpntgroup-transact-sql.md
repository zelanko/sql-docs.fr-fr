---
title: sp_helpntgroup (Transact-SQL) | Documents Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpntgroup
- sp_helpntgroup_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpntgroup
ms.assetid: 02b4f7c1-480a-436c-8bae-7a2488be45d2
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 5c2128c95c4729d087a0e9bb9c8553d71600af14
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="sphelpntgroup-transact-sql"></a>sp_helpntgroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit des informations sur les groupes Windows ayant un compte dans la base de données active.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpntgroup [ [ @ntname= ] 'name' ]   
```  
  
## <a name="arguments"></a>Arguments  
 [  **@ntname =** ] **'***nom***'**  
 Est le nom du groupe Windows. *nom* est **sysname**, avec NULL comme valeur par défaut. *nom* doit être un groupe Windows valid ayant accès à la base de données actuelle. Si *nom* n’est pas spécifié, tous les groupes Windows ayant accès à la base de données active sont inclus dans la sortie.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**NTGroupName**|**sysname**|Nom du groupe Windows.|  
|**NTGroupId**|**smallint**|Identificateur du groupe.|  
|**SID**|**varbinary(85)**|Identificateur de sécurité (SID) de **NTGroupName**.|  
|**HasDbAccess**|**int**|1 = le groupe Windows a une autorisation d'accès à la base de données.|  
  
## <a name="remarks"></a>Notes  
 Pour afficher la liste de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rôles dans la base de données actuelle, utilisez **sp_helprole**.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 L'exemple de code suivant affiche la liste des groupes Windows ayant accès à la base de données active.  
  
```  
EXEC sp_helpntgroup;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_helprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprole-transact-sql.md)   
 [sp_revokedbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokedbaccess-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

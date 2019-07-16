---
title: sp_vupgrade_replication (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_vupgrade_replication_TSQL
- sp_vupgrade_replication
helpviewer_keywords:
- sp_vupgrade_replication
ms.assetid: d2c0ed66-07d1-4adc-82e5-a654376879bc
author: stevestein
ms.author: sstein
ms.openlocfilehash: 66ee4819e8830fd718334d4a094ec22c01bf069d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67927805"
---
# <a name="spvupgradereplication-transact-sql"></a>sp_vupgrade_replication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Activé par le programme d'installation lors de la mise à niveau d'un serveur de réplication. Met à niveau le schéma et les données système afin que la réplication soit prise en charge par la version actuelle du produit. Crée de nouveaux objets système de réplication dans les bases de données système et utilisateur. Cette procédure stockée est exécutée sur la machine sur laquelle la mise à niveau de la réplication doit intervenir.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_vupgrade_replication [ [@login=] 'login' ]  
    [ , [ @password= ] 'password' ]  
    [ , [ @ver_old= ] 'old_version' ]  
    [ , [ @force_remove= ] 'force_removal' ]  
    [ , [ @security_mode= ] security_mode ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @login = ] 'login'` Est la connexion d’administrateur système à utiliser lors de la création d’objets système dans la base de données de Distribution. *login* est de type **sysname**, avec NULL comme valeur par défaut. Ce paramètre n’est pas obligatoire si *security_mode* a la valeur **1**, qui est l’authentification Windows.  
  
> [!NOTE]  
>  Ce paramètre est ignoré lorsque vous effectuez une mise à niveau vers [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures.  
  
`[ @password = ] 'password'` Est le mot de passe administrateur système à utiliser lors de la création d’objets système dans la base de données de Distribution. *mot de passe* est **sysname**, avec une valeur par défaut **''** (chaîne vide). Ce paramètre n’est pas obligatoire si *security_mode* a la valeur **1**, qui est l’authentification Windows.  
  
> [!NOTE]  
>  Ce paramètre est ignoré lorsque vous mettez à niveau vers SQL [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures.  
  
`[ @ver_old = ] 'old_version'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 Cette procédure stockée est déconseillée et sera supprimée dans les prochaines versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
`[ @force_remove = ] 'force_removal'` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @security_mode = ] 'security_mode'` Est le mode de sécurité de connexion à utiliser lors de la création de nouveaux objets système dans la base de données de Distribution. *security_mode* est **bits** avec une valeur par défaut **0**. Si **0**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification est utilisée. Si **1**, l’authentification Windows est utilisée.  
  
> [!NOTE]  
>  Ce paramètre est ignoré lorsque vous effectuez une mise à niveau vers [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_vupgrade_replication** est utilisé lors de la mise à niveau de tous les types de réplication.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_vupgrade_replication**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Valider des données répliquées](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  

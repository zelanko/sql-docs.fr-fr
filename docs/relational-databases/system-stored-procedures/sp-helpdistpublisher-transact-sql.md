---
title: sp_helpdistpublisher (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistpublisher_TSQL
- sp_helpdistpublisher
helpviewer_keywords:
- sp_helpdistpublisher
ms.assetid: f207c22d-8fb2-4756-8a9d-6c51d6cd3470
author: stevestein
ms.author: sstein
ms.openlocfilehash: a47a81b2b19ceccf76a031e298ab60cf4a6f8c9a
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770949"
---
# <a name="sphelpdistpublisher-transact-sql"></a>sp_helpdistpublisher (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Renvoie les propriétés des serveurs de publication qui utilisent un serveur de distribution. Cette procédure stockée est exécutée sur n’importe quelle base de données du serveur de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpdistpublisher [ [ @publisher=] 'publisher']   
    [ , [ @check_user = ] check_user  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'`Est le serveur de publication pour lequel les propriétés sont retournées. *Publisher* est de **%** **type sysname**, avec la valeur par défaut.  
  
`[ @check_user = ] check_user` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nom du serveur de publication.|  
|**distribution_db**|**sysname**|Base de données de distribution pour le serveur de publication spécifié.|  
|**security_mode**|**int**|Mode de sécurité utilisé par les Agents de réplication pour se connecter au serveur de publication des abonnements avec mise à jour en attente ou à un serveur de publication non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **0**  =  authentification[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> **1** = authentification Windows|  
|**login**|**sysname**|Nom de connexion utilisé par les Agents de réplication pour se connecter au serveur de publication des abonnements avec mise à jour en attente ou à un serveur de publication non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**nvarchar(524)**|Mot de passe renvoyé (sous forme chiffrée simple). Le mot de passe est NULL pour les utilisateurs autres que **sysadmin**.|  
|**active**|**bit**|Indique si un serveur de publication distant utilise le serveur local comme serveur de distribution.<br /><br /> **0** = Non<br /><br /> **1** = Oui|  
|**working_directory**|**nvarchar(255)**|Nom du répertoire de travail.|  
|**TPM**|**bit**|si le mot de passe est requis lorsqu'un serveur de publication se connecte au serveur de distribution. Pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] et[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] les versions ultérieures, cette valeur doit toujours retourner **0**, ce qui signifie que le mot de passe est requis.|  
|**thirdparty_flag**|**bit**|Indique si la publication est activée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou par une application tierce :<br /><br /> **0, Oracle ou** = serveur de publication Oracle Gateway.[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> **1** = le serveur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] publication a été intégré à l’aide d’une application tierce.|  
|**publisher_type**|**sysname**|Type de serveur de publication ; il peut s'agir d'une des valeurs suivantes :<br /><br /> **MSSQLSERVER**<br /><br /> **SOLUTION**<br /><br /> **PASSERELLE ORACLE**|  
|**publisher_data_source**|**nvarchar(4000)**|Nom de la source de données OLE DB sur le serveur de publication.|  
|**storage_connection_string**|**nvarchar(4000)**|Clé d’accès de stockage pour le répertoire de travail lorsque le serveur de distribution ou le serveur de publication Azure SQL Database.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpdistpublisher** est utilisé dans tous les types de réplications.  
  
 **sp_helpdistpublisher** n’affiche pas la connexion ou le mot de passe du serveur de publication dans le jeu de résultats pour les connexions non-**sysadmin** .  
  
## <a name="permissions"></a>Autorisations  
 Les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_helpdistpublisher** pour n’importe quel serveur de publication utilisant le serveur local en tant que serveur de distribution. Les membres du rôle de base de données fixe **db_owner** ou du rôle **replmonitor** dans une base de données de distribution peuvent exécuter **Sp_helpdistpublisher** pour tout serveur de publication qui utilise cette base de données de distribution. Les utilisateurs de la liste d’accès à la publication pour une publication sur le serveur de publication spécifié peuvent exécuter **sp_helpdistpublisher**. Si le serveur de *publication* n’est pas spécifié, des informations sont retournées pour tous les serveurs de publication auxquels l’utilisateur a le droit d’accéder.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  

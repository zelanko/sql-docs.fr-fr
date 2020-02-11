---
title: sp_MSchange_logreader_agent_properties (T-SQL)
description: Décrit la procédure stockée sp_MSchange_logreader_agent_properties utilisée pour modifier les propriétés de l’agent de lecture du journal pour une topologie de Réplication SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_MSchange_logreader_agent_properties_TSQL
- sp_MSchange_logreader_agent_properties
helpviewer_keywords:
- sp_MSchange_logreader_agent_properties
ms.assetid: 925df9d3-a041-4046-8e17-c47f40edb86d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 37a36218b4e9e93a761c776e76a6596f40a6c0eb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75322275"
---
# <a name="sp_mschange_logreader_agent_properties-transact-sql"></a>sp_MSchange_logreader_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés d’un travail de l’agent de lecture du journal [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] qui s’exécute sur un serveur de distribution ou version ultérieure. Cette procédure stockée est utilisée pour modifier des propriétés lorsque le serveur de publication s'exécute sur une instance de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Cette procédure stockée est exécutée au niveau du serveur de distribution sur la base de données de distribution.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_MSchange_logreader_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publisher_security_mode = ] publisher_security_mode  
        , [ @publisher_login = ] 'publisher_login'  
        , [ @publisher_password = ] 'publisher_password'   
        , [ @job_login = ] 'job_login'  
        , [ @job_password = ] 'job_password'  
        , [ @publisher_type = ] 'publisher_type'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'`Nom du serveur de publication. *Publisher* est de **type sysname**, sans valeur par défaut.  
  
`[ @publisher_db = ] 'publisher_db'`Nom de la base de données de publication. *publisher_db* est de **type sysname**, sans valeur par défaut.  
  
`[ @publisher_security_mode = ] publisher_security_mode`Mode de sécurité utilisé par l’agent lors de la connexion au serveur de publication. *publisher_security_mode* est de type **smallint**, sans valeur par défaut.  
  
 **0** spécifie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.  
  
 **1** spécifie l’authentification Windows.  
  
`[ @publisher_login = ] 'publisher_login'`Nom de connexion utilisé lors de la connexion au serveur de publication. *publisher_login* est de **type sysname**, sans valeur par défaut. *publisher_login* doit être spécifié lorsque *publisher_security_mode* a la **valeur 0**. Si *publisher_login* a la valeur null et que *publisher_security_mode* a la valeur **1**, le compte Windows spécifié dans *job_login* sera utilisé lors de la connexion au serveur de publication.  
  
`[ @publisher_password = ] 'publisher_password'`Mot de passe utilisé lors de la connexion au serveur de publication. *publisher_password* est de **type sysname**, sans valeur par défaut.  
  
`[ @job_login = ] 'job_login'`Nom de connexion du compte Windows sous lequel l’agent s’exécute. *job_login* est de type **nvarchar (257)**, sans valeur par défaut. *Cela ne peut pas être modifié pour un serveur de publication non-* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *.*  
  
`[ @job_password = ] 'job_password'`Mot de passe du compte Windows sous lequel l’agent s’exécute. *job_password* est de **type sysname**, sans valeur par défaut.  
  
`[ @publisher_type = ] 'publisher_type'`Spécifie le type de serveur de publication lorsque le serveur de publication n' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]est pas en cours d’exécution dans une instance de. *publisher_type* est de **type sysname**et peut prendre l’une des valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**|Spécifie un serveur de publication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**SOLUTION**|Spécifie un serveur de publication Oracle standard.|  
|**ORACLE GATEWAY**|Spécifie un serveur de publication Oracle Gateway.|  
  
 Pour plus d’informations sur les différences entre un serveur de publication Oracle et un serveur de publication Oracle Gateway, consultez [vue d’ensemble de la publication Oracle](../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
## <a name="remarks"></a>Notes  
 **sp_MSchange_logreader_agent_properties** est utilisé dans la réplication transactionnelle.  
  
 Vous devez spécifier tous les paramètres lors de l’exécution de **sp_MSchange_logreader_agent_properties**. Exécutez [sp_helplogreader_agent &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) pour retourner les propriétés actuelles du travail de l’agent de lecture du journal.  
  
 Après avoir modifié le nom de connexion ou le mot de passe d'un Agent, vous devez arrêter et redémarrer celui-ci avant que la modification prenne effet.  
  
 Quand le serveur de publication s’exécute sur [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] une instance de ou version ultérieure, vous devez utiliser [sp_changelogreader_agent](../../relational-databases/system-stored-procedures/sp-changelogreader-agent-transact-sql.md) pour modifier les propriétés de l’agent de lecture du journal.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** sur le serveur de distribution peuvent exécuter **sp_MSchange_logreader_agent_properties**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addlogreader_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)  
  
  

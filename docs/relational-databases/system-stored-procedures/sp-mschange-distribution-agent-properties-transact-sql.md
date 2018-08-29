---
title: sp_MSchange_distribution_agent_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
- sp_MSchange_distribution_agent_properties
- sp_MSchange_distribution_agent_properties_TSQL
helpviewer_keywords:
- sp_MSchange_distribution_agent_properties
ms.assetid: 7dac5e68-bf84-433a-a531-66921f35126f
caps.latest.revision: 17
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 75b89dab3a8e8e1aaaf967101ffaac566ec34d06
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022868"
---
# <a name="spmschangedistributionagentproperties-transact-sql"></a>sp_MSchange_distribution_agent_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés d’un travail d’Agent de Distribution s’exécute sur un [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure du serveur de distribution. Cette procédure stockée est utilisée pour modifier des propriétés lorsque le serveur de publication s'exécute sur une instance de [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Cette procédure stockée est exécutée au niveau du serveur de distribution sur la base de données de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_MSchange_distribution_agent_properties [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'   
        , [ @subscriber = ] 'subscriber'   
        , [ @subscriber_db = ] 'subscriber_db'   
        , [ @property = ] 'property'   
        , [ @value = ] 'value' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@publisher** =] **'***publisher***'**  
 Nom du serveur de publication. *serveur de publication* est **sysname**, sans valeur par défaut.  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 Nom de la base de données de publication. *publisher_db* est **sysname**, sans valeur par défaut.  
  
 [  **@publication =** ] **'***publication***'**  
 Nom de la publication. *publication* est **sysname**, sans valeur par défaut.  
  
 [  **@subscriber=** ] **'***abonné***'**  
 Nom de l'Abonné. *abonné* est **sysname**, sans valeur par défaut.  
  
 [  **@subscriber_db=** ] **'***bd_abonné***'**  
 Est le nom de la base de données d’abonnement. *bd_abonné* est **sysname**, sans valeur par défaut.  
  
 [  **@property =** ] **'***propriété***'**  
 Propriété de publication à modifier. *propriété* est **sysname**, sans valeur par défaut.  
  
 [  **@value =** ] **'***valeur***'**  
 Nouvelle valeur de la propriété. *valeur* est **nvarchar (524)**, avec NULL comme valeur par défaut.  
  
 Le tableau ci-dessous décrit les propriétés modifiables du travail de l'Agent de distribution et les limites liées aux valeurs de ces propriétés.  
  
|Propriété|Valeur|Description|  
|--------------|-----------|-----------------|  
|**distrib_job_login**||Nom de connexion du compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent s'exécute.|  
|**distrib_job_password**||Mot de passe du compte Windows sous lequel le travail de l'Agent s'exécute.|  
|**subscriber_catalog**||Catalogue à utiliser lors d’une connexion au fournisseur OLE DB. *Cette propriété est uniquement valide pour les non -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *abonnés.*|  
|**subscriber_datasource**||Nom de la source de données tel qu'il est interprété par le fournisseur OLE DB. *Cette propriété est uniquement valide pour les non -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *abonnés.*|  
|**subscriber_location**||Emplacement de la base de données interprété par le fournisseur OLE DB. *Cette propriété est uniquement valide pour les non -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *abonnés.*|  
|**subscriber_login**||Nom de connexion à utiliser lors de la connexion à un Abonné pour synchroniser l'abonnement.|  
|**subscriber_password**||Mot de passe abonné.<br /><br /> [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]|  
|**subscriber_provider**||Identificateur de programme unique (PROGID) avec lequel le fournisseur OLE DB de la source de données non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est inscrit. *Cette propriété est uniquement valide pour les non -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *abonnés.*|  
|**subscriber_providerstring**||Chaîne de connexion propre au fournisseur OLE DB qui identifie la source de données. *Cette propriété est uniquement valide pour les abonnés non SQL Server.*|  
|**subscriber_security_mode**|**1**|Authentification Windows.<br /><br /> [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]|  
||**0**|Authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**subscriber_type**|**0**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonné|  
||**1**|Serveur de la source de données ODBC.|  
||**3**|Fournisseur OLE DB|  
|**flux d’abonnements**||Indique le nombre de connexions autorisées par Agent de distribution pour appliquer en parallèle des traitements de modifications à un Abonné. *Non pris en charge pour les non -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *les abonnés, les serveurs de publication Oracle ou les abonnements d’égal à égal.*|  
  
> [!NOTE]  
>  Après avoir modifié le nom de connexion ou le mot de passe d'un Agent, vous devez arrêter et redémarrer celui-ci avant que la modification prenne effet.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_MSchange_distribution_agent_properties** est utilisé dans la réplication d’instantané ou transactionnelle.  
  
 Lorsque le serveur de publication s’exécute sur une instance de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure, vous devez utiliser [sp_changesubscription](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md) pour modifier les propriétés d’un travail d’Agent de fusion qui synchronise un abonnement envoyé qui s’exécute sur le serveur de distribution.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** du rôle serveur fixe sur le serveur de distribution peuvent exécuter **sp_MSchange_distribution_agent_properties**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)   
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)  
  
  

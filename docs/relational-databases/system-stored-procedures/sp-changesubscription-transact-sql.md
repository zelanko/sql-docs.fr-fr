---
title: sp_changesubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/28/2015
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
- changesubscription
- sp_changesubscription
- changesubscription_TSQL
- sp_changesubscription_TSQL
helpviewer_keywords:
- sp_changesubscription
ms.assetid: f9d91fe3-47cf-4915-b6bf-14c9c3d8a029
caps.latest.revision: 40
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 64a34ed640dc9efac57d948475071690ed266d2e
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43023330"
---
# <a name="spchangesubscription-transact-sql"></a>sp_changesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés d'un abonnement par envoi de données (push) ou par extraction de données (pull) d'instantané ou transactionnel, qui participe à une réplication transactionnelle de mise à jour en attente. Pour modifier les propriétés de tous les autres types d’abonnements par extraction, utilisez [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md). **sp_changesubscription** est exécutée sur le serveur de publication sur la base de données de publication.  
  
> [!IMPORTANT]  
>  Lors de la configuration d'un serveur de publication avec un serveur de distribution distant, les valeurs fournies pour tous les paramètres, y compris *job_login* et *job_password*, sont envoyées en texte brut au serveur de distribution. Vous devez chiffrer la connexion entre le serveur de publication et son serveur de distribution distant avant d'exécuter cette procédure stockée. Pour plus d’informations, consultez [Activer des connexions chiffrées dans le moteur de base de données &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changesubscription [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
        , [ @subscriber = ] 'subscriber'  
        , [ @destination_db = ] 'destination_db'  
        , [ @property = ] 'property'  
        , [ @value = ] 'value'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@publication**=] **'***publication***'**  
 Nom de la publication à modifier. *publication*est **sysname**, sans valeur par défaut  
  
 [ **@article** =] **'***article***'**  
 Nom de l'article à modifier. *article* est **sysname**, sans valeur par défaut.  
  
 [ **@subscriber** =] **'***abonné***'**  
 Nom de l'Abonné. *abonné* est **sysname**, sans valeur par défaut.  
  
 [ **@destination_db** =] **'***destination_db***'**  
 Est le nom de la base de données d’abonnement. *destination_db* est **sysname**, sans valeur par défaut.  
  
 [  **@property=**] **'***propriété***'**  
 Propriété à modifier pour l'abonnement donné. *propriété* est **nvarchar (30)**, et peut prendre l’une des valeurs dans la table.  
  
 [  **@value=**] **'***valeur***'**  
 Nouvelle valeur pour le texte spécifié *propriété*. *valeur* est **nvarchar (4000)**, et peut prendre l’une des valeurs dans la table.  
  
|Propriété|Valeur|Description|  
|--------------|-----------|-----------------|  
|**distrib_job_login**||Nom de connexion du compte [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows sous lequel l'Agent s'exécute.|  
|**distrib_job_password**||Mot de passe pour le compte Windows sous lequel l’agent s’exécute.|  
|**subscriber_catalog**||Catalogue à utiliser lors d’une connexion au fournisseur OLE DB. Cette propriété est uniquement valide pour les non -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonnés.|  
|**subscriber_datasource**||Nom de la source de données tel qu'il est interprété par le fournisseur OLE DB. *Cette propriété est uniquement valide pour les non -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *abonnés.*|  
|**subscriber_location**||Emplacement de la base de données interprété par le fournisseur OLE DB. *Cette propriété est uniquement valide pour les non -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *abonnés.*|  
|**subscriber_login**||Nom de la connexion du côté Abonné.|  
|**subscriber_password**||Mot de passe fort pour le nom de connexion fourni.|  
|**subscriber_security_mode**|**1**|Utilise l'authentification Windows pour la connexion à l'Abonné.|  
||**0**|Utiliser l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la connexion à l'Abonné.|  
|**subscriber_provider**||Identificateur de programme unique (PROGID) avec lequel le fournisseur OLE DB de la source de données non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est inscrit. *Cette propriété est uniquement valide pour les non -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *abonnés.*|  
|**subscriber_providerstring**||Chaîne de connexion propre au fournisseur OLE DB qui identifie la source de données. *Cette propriété est uniquement valide pour les non -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *abonnés.*|  
|**flux d’abonnements**||Nombre de connexions autorisées par Agent de distribution pour appliquer en parallèle des traitements de modifications à un Abonné. Une plage de valeurs à partir de **1** à **64** est pris en charge pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les serveurs de publication. Cette propriété doit être **0** pour non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les abonnés, les serveurs de publication Oracle ou les abonnements d’égal à égal.|  
|**subscriber_type**|**1**|Serveur de la source de données ODBC.|  
||**3**|Fournisseur OLE DB|  
|**memory_optimized**|**bit**|Indique que l’abonnement prend en charge les tables optimisées en mémoire. *memory_optimized* est **bits**, où 1 est égale à true (l’abonnement prend en charge les tables optimisées en mémoire).|  
  
 [  **@publisher =** ] **'***publisher***'**  
 Spécifie un serveur de publication non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  *serveur de publication* ne doit pas être spécifié pour un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_changesubscription** est utilisé dans la réplication transactionnelle et d’instantané.  
  
 **sp_changesubscription** peut uniquement être utilisé pour modifier les propriétés d’abonnements par envoi ou d’abonnements par extraction impliqués dans la mise à jour de la réplication transactionnelle en file d’attente. Pour modifier les propriétés de tous les autres types d’abonnements par extraction, utilisez [sp_change_subscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md).  
  
 Après avoir modifié le nom de connexion ou le mot de passe d'un Agent, vous devez arrêter et redémarrer celui-ci avant que la modification prenne effet.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_changesubscription**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)  
  
  

---
title: sp_changemergepullsubscription (Transact-SQL) | Microsoft Docs
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
- sp_changemergepullsubscription
- sp_changemergepullsubscription_TSQL
helpviewer_keywords:
- sp_changemergepullsubscription
ms.assetid: 5e0d04f2-6175-44a2-ad96-a8e2986ce4c9
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 81b03ee49bb3184490d8ba8182b70557e5b0d8a8
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43018274"
---
# <a name="spchangemergepullsubscription-transact-sql"></a>sp_changemergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés de l'abonnement de fusion extrait. Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changemergepullsubscription [ [ @publication= ] 'publication' ]  
    [ , [ @publisher= ] 'publisher' ]  
    [ , [ @publisher_db= ] 'publisher_db' ]  
    [ , [ @property= ] 'property' ]  
    [ , [ @value= ] 'value' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication=**] **'***publication***'**  
 Nom de la publication. *publication* est **sysname**, avec % comme valeur par défaut.  
  
 [  **@publisher=**] **'***publisher***'**  
 Nom du serveur de publication. *serveur de publication*est **sysname**, avec % comme valeur par défaut.  
  
 [  **@publisher_db=**] **'***publisher_db***'**  
 Nom de la base de données du serveur de publication. *publisher_db*est **sysname**, avec % comme valeur par défaut.  
  
 [  **@property=**] **'***propriété***'**  
 Est le nom de la propriété à modifier. *propriété* est **sysname**, et peut prendre l’une des valeurs dans la table.  
  
 [  **@value=**] **'***valeur***'**  
 Est la nouvelle valeur pour la propriété spécifiée. *valeur*est **nvarchar (255)**, et peut prendre l’une des valeurs dans la table.  
  
|Propriété|Valeur|Description|  
|--------------|-----------|-----------------|  
|**alt_snapshot_folder**||Emplacement de stockage du dossier d'instantanés, si cet emplacement est différent ou en complément de l'emplacement par défaut.|  
|**description**||Description de cet abonnement extrait.|  
|**serveur de distribution**||Nom du serveur de distribution.|  
|**distributor_login**||ID de connexion utilisé sur le serveur de distribution pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**distributor_password**||Mot de passe (chiffré) sur le serveur de distribution pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.|  
|**distributor_security_mode**|**1**|Utilise l'authentification Windows pour la connexion au serveur de distribution.|  
||**0**|Utilise l'authentification  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la connexion au serveur de distribution.|  
|**dynamic_snapshot_location**||Chemin d'accès au dossier dans lequel les fichiers d'instantané sont enregistrés.|  
|**ftp_address**||Disponible pour compatibilité descendante uniquement. Est l’adresse réseau du service de transfert de protocole FTP (File) pour le serveur de distribution.|  
|**ftp_login**||Disponible pour compatibilité descendante uniquement. Le nom d’utilisateur est utilisé pour se connecter au service FTP.|  
|**ftp_password**||Disponible pour compatibilité descendante uniquement. Mot de passe de l'utilisateur utilisé pour la connexion au service FTP.|  
|**ftp_port**||Disponible pour compatibilité descendante uniquement. Numéro de port du service FTP du serveur de distribution.|  
|**Nom d’hôte**||Spécifie la valeur de la fonction HOST_NAME() lorsqu'elle est utilisée dans la clause WHERE d'un filtre de jointure ou d'une relation logique.|  
|**internet_login**||Connexion que l'Agent de fusion utilise pour se connecter, à l'aide de l'authentification de base, au serveur Web qui héberge la synchronisation Web.|  
|**internet_password**||Mot de passe de la connexion que l'Agent de fusion utilise pour se connecter, à l'aide de l'authentification de base, au serveur Web qui héberge la synchronisation Web.|  
|**internet_security_mode**|**1**|Utilise l'authentification Windows pour se connecter au serveur Web qui héberge la synchronisation Web.|  
||**0**|Utilise l'authentification de base pour se connecter au serveur Web qui héberge la synchronisation Web.|  
|**internet_timeout**||Délai en secondes avant l'expiration d'une demande de synchronisation Web.|  
|**internet_url**||URL qui représente l'emplacement de l'écouteur de réplication pour la synchronisation Web.|  
|**merge_job_login**||Nom de connexion pour le compte Windows sous lequel l’agent s’exécute.|  
|**merge_job_password**||Mot de passe pour le compte Windows sous lequel l’agent s’exécute.|  
|**priority**||Disponible pour compatibilité descendante uniquement. Exécutez [sp_changemergesubscription](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md) sur le serveur de publication à la place pour modifier la priorité d’un abonnement.|  
|**publisher_login**||ID de connexion utilisé côté serveur de publication pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**publisher_password**||Mot de passe (chiffré) utilisé côté serveur de publication pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**publisher_security_mode**|**0**|Utiliser l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la connexion au serveur de publication.|  
||**1**|Utiliser l'authentification Windows pour la connexion au serveur de publication.|  
||**2**|Déclencheurs de synchronisation utilisent statique **sysservers** entrée pour l’appel de procédure distante (RPC) et le serveur de publication doit être définie dans le **sysservers** table en tant que serveur distant ou serveur lié.|  
|**sync_type**|**Automatique**|Le schéma et les données initiales des tables publiées sont transférés en premier lieu vers l'Abonné.|  
||**None**|L'Abonné dispose déjà du schéma et des données initiales pour les tables publiées ; les données et les tables système sont toujours transférées.|  
|**use_ftp**|**true**|Utilise FTP au lieu du protocole usuel pour extraire les instantanés.|  
||**false**|Utilise le protocole usuel pour extraire les instantanés.|  
|**use_web_sync**|**true**|L'abonnement peut être synchronisé sur HTTP.|  
||**false**|L'abonnement ne peut pas être synchronisé sur HTTP.|  
|**use_interactive_resolver**|**true**|Le résolveur interactif est utilisé lors de la résolution des conflits.|  
||**false**|Le résolveur interactif n'est pas utilisé.|  
|**working_directory**||Chemin complet du répertoire dans lequel les fichiers d'instantané sont transférés via FTP lorsque cette option est spécifiée.|  
|NULL (par défaut)||Retourne la liste des valeurs prises en charge pour *propriété*.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_changemergepullsubscription** est utilisé dans la réplication de fusion.  
  
 Le serveur courant et la base de données courantes sont supposés être l'abonné et la base de données de l'abonné.  
  
 Après avoir modifié le nom de connexion ou le mot de passe d'un Agent, vous devez arrêter et redémarrer celui-ci avant que la modification prenne effet.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_changemergepullsubscription**.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’un abonnement par extraction](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [sp_addmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

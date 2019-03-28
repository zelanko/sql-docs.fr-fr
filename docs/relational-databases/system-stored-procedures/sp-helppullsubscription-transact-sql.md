---
title: sp_helppullsubscription (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppullsubscription_TSQL
- sp_helppullsubscription
helpviewer_keywords:
- sp_helppullsubscription
ms.assetid: a0d9c3f1-1fe9-497c-8e2f-5b74f47a7346
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 10a8184fdad0c25c2377c5ed9df0a318aba736a2
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58527771"
---
# <a name="sphelppullsubscription-transact-sql"></a>sp_helppullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche des informations relatives à un ou plusieurs abonnements de l'Abonné. Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helppullsubscription [ [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @publication = ] 'publication' ]  
    [ , [ @show_push = ] 'show_push' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'` Est le nom du serveur distant. *serveur de publication* est **sysname**, avec une valeur par défaut **%**, qui retourne des informations pour tous les serveurs de publication.  
  
`[ @publisher_db = ] 'publisher_db'` Est le nom de la base de données du serveur de publication. *publisher_db* est **sysname**, avec une valeur par défaut **%**, qui retourne toutes les bases de données de serveur de publication.  
  
`[ @publication = ] 'publication'` Est le nom de la publication. *publication* est **sysname**, avec une valeur par défaut **%**, qui renvoie toutes les publications. Si ce paramètre est égal à ALL, seuls les abonnements par extraction avec independent_agent = **0** sont retournés.  
  
`[ @show_push = ] 'show_push'` Est si tous les abonnements envoyés doivent être retournées. *afficher_envoi*est **nvarchar (5)**, avec une valeur FALSE par défaut, ne retourne pas les abonnements envoyés.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**publisher** (serveur de publication)|**sysname**|Nom du serveur de publication.|  
|**base de données du serveur de publication**|**sysname**|Nom de la base de données du serveur de publication.|  
|**publication**|**sysname**|Nom de la publication.|  
|**independent_agent**|**bit**|Indique s'il existe un Agent de distribution autonome pour cette publication.|  
|**type d’abonnement**|**Int**|Type d'abonnement à la publication.|  
|**agent de distribution**|**nvarchar(100)**|Agent de distribution traitant l'abonnement.|  
|**description de la publication**|**nvarchar(255)**|Description de la publication.|  
|**heure de la dernière mise à jour**|**date**|Heure à laquelle les informations d'abonnement ont été mises à jour. Il s'agit d'une chaîne UNICODE de date ISO (114) et d'heure ODBC (121). Le format est aaaammjj hh:mi:sss.mmm où aaaa représente l'année, mm le mois, jj le jour, hh l'heure, mi les minutes, sss les secondes et mmm les millisecondes.|  
|**nom de l’abonnement**|**varchar(386)**|Nom de l'abonnement.|  
|**horodatage de la dernière transaction**|**varbinary(16)**|Horodateur de la dernière transaction dupliquée.|  
|**mode de mise à jour**|**tinyint**|Types de mise à jour autorisés|  
|**job_id de l’agent de distribution**|**Int**|ID du travail de l'Agent de distribution.|  
|**enabled_for_synmgr**|**Int**|Indique si l'abonnement peut être synchronisé à l'aide du gestionnaire de synchronisation de [!INCLUDE[msCoName](../../includes/msconame-md.md)].|  
|**guid d’abonnement**|**binary(16)**|Identificateur global de la version d'abonnement associée à une publication|  
|**subid**|**binary(16)**|Identificateur global d'un abonnement anonyme|  
|**immediate_sync**|**bit**|Indique si les fichiers de synchronisation sont créés ou recréés à chaque exécution de l’Agent d'instantané.|  
|**connexion du serveur de publication**|**sysname**|ID de connexion utilisé côté serveur de publication pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**mot de passe de serveur de publication**|**nvarchar(524)**|Mot de passe (chiffré) utilisé côté serveur de publication pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**security_mode du serveur de publication**|**Int**|Mode de sécurité implémenté sur le serveur de publication :<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification<br /><br /> **1** = l’authentification Windows<br /><br /> **2** = les déclencheurs de synchronisation utilisent statique **sysservers** entrée pour effectuer l’appel de procédure distante (RPC), et *publisher* doit être défini dans le **sysservers**table en tant que serveur distant ou serveur lié.|  
|**distributor**|**sysname**|Nom du serveur de distribution.|  
|**distributor_login**|**sysname**|ID de connexion utilisé côté serveur de distribution pour l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**distributor_password**|**nvarchar(524)**|Mot de passe (chiffré) sur le serveur de distribution pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification.|  
|**distributor_security_mode**|**Int**|Mode de sécurité implémenté sur le serveur de distribution :<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification<br /><br /> **1** = l’authentification Windows|  
|**ftp_address**|**sysname**|Pour compatibilité descendante uniquement.|  
|**ftp_port**|**Int**|Pour compatibilité descendante uniquement.|  
|**ftp_login**|**sysname**|Pour compatibilité descendante uniquement.|  
|**ftp_password**|**nvarchar(524)**|Pour compatibilité descendante uniquement.|  
|**alt_snapshot_folder**|**nvarchar(255)**|Emplacement de stockage du dossier d'instantané si cet emplacement est différent ou en complément de l'emplacement par défaut.|  
|**working_directory**|**nvarchar(255)**|Chemin complet du répertoire dans lequel les fichiers d'instantané sont transférés via FTP (File Transfer Protocol) lorsque cette option est spécifiée.|  
|**use_ftp**|**bit**|L'abonnement souscrit à la publication via Internet et les propriétés d'adressage FTP sont configurées. Si **0**, abonnement n’utilise pas FTP. Si **1**, l’abonnement utilise FTP.|  
|**publication_type**|**Int**|Indique le type de réplication de la publication :<br /><br /> **0** = réplication transactionnelle<br /><br /> **1** = réplication d’instantané<br /><br /> **2** = la réplication de fusion|  
|**dts_package_name**|**sysname**|Spécifie le nom du package DTS (Data Transformation Services).|  
|**dts_package_location**|**Int**|Emplacement auquel le package DTS est enregistré :<br /><br /> **0** = serveur de distribution<br /><br /> **1** = abonné|  
|**offload_agent**|**bit**|Indique si l'agent peut être activé à distance. Si **0**, l’agent ne peut pas être activé à distance.|  
|**offload_server**|**sysname**|Indique le nom de réseau du serveur utilisé pour l'activation à distance.|  
|**last_sync_status**|**Int**|État de l'abonnement :<br /><br /> **0** = tous les travaux sont en attente de démarrage<br /><br /> **1** = une ou plusieurs travaux commencent<br /><br /> **2** = tous les travaux ont été correctement exécutées.<br /><br /> **3** = au moins un travail s’exécute.<br /><br /> **4** = tous les travaux sont planifiés et inactifs<br /><br /> **5** = au moins un travail est relancée après un échec<br /><br /> **6** = au moins un travail n’a pas pu s’exécuter avec succès|  
|**last_sync_summary**|**sysname**|Description des résultats de la dernière synchronisation.|  
|**last_sync_time**|**datetime**|Heure à laquelle les informations d'abonnement ont été mises à jour. Il s'agit d'une chaîne UNICODE de date ISO (114) et d'heure ODBC (121). Le format est aaaammjj hh:mi:sss.mmm où aaaa représente l'année, mm le mois, jj le jour, hh l'heure, mi les minutes, sss les secondes et mmm les millisecondes.|  
|**job_login**|**nvarchar(512)**|Est le compte Windows sous lequel l’agent de Distribution s’exécute, ce qui est retourné sous la forme *domaine*\\*nom d’utilisateur*.|  
|**job_password**|**sysname**|Pour des raisons de sécurité, une valeur de «**\*\*\*\*\*\*\*\*\*\***» est toujours retourné.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helppullsubscription** est utilisé dans la réplication transactionnelle et d’instantané.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **db_owner** rôle de base de données fixe peuvent exécuter **sp_helppullsubscription** .  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addpullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_droppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppullsubscription-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

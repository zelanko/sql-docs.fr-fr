---
title: sp_helpdistpublisher (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistpublisher_TSQL
- sp_helpdistpublisher
helpviewer_keywords:
- sp_helpdistpublisher
ms.assetid: f207c22d-8fb2-4756-8a9d-6c51d6cd3470
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a909154d1d8f8c5d4a260199b3738d7526338350
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47601243"
---
# <a name="sphelpdistpublisher-transact-sql"></a>sp_helpdistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie les propriétés des serveurs de publication qui utilisent un serveur de distribution. Cette procédure stockée est exécutée sur le serveur de distribution sur une base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpdistpublisher [ [ @publisher=] 'publisher']   
    [ , [ @check_user = ] check_user  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publisher=** ] **'***publisher***'**  
 Nom du serveur de publication dont les propriétés sont renvoyées. *serveur de publication* est **sysname**, avec une valeur par défaut **%**.  
  
 [  **@check_user=** ] *check_user*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**nom**|**sysname**|Nom du serveur de publication.|  
|**distribution_db**|**sysname**|Base de données de distribution pour le serveur de publication spécifié.|  
|**security_mode**|**Int**|Mode de sécurité utilisé par les Agents de réplication pour se connecter au serveur de publication des abonnements avec mise à jour en attente ou à un serveur de publication non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification<br /><br /> **1** = l’authentification Windows|  
|**connexion**|**sysname**|Nom de connexion utilisé par les Agents de réplication pour se connecter au serveur de publication des abonnements avec mise à jour en attente ou à un serveur de publication non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**nvarchar (524)**|Mot de passe renvoyé (sous forme chiffrée simple). Mot de passe est NULL pour les utilisateurs autres que **sysadmin**.|  
|**Active**|**bit**|Indique si un serveur de publication distant utilise le serveur local comme serveur de distribution.<br /><br /> **0** = Non<br /><br /> **1** = Oui|  
|**working_directory**|**nvarchar(255)**|Nom du répertoire de travail.|  
|**approuvé**|**bit**|si le mot de passe est requis lorsqu'un serveur de publication se connecte au serveur de distribution. Pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures, doit toujours renvoyer **0**, ce qui signifie que le mot de passe est requis.|  
|**thirdparty_flag**|**bit**|Indique si la publication est activée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou par une application tierce :<br /><br /> **0** = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], oracle ou Oracle Gateway Publisher.<br /><br /> **1** = serveur de publication a été intégré à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’une application tierce.|  
|**publisher_type**|**sysname**|Type de serveur de publication ; il peut s'agir d'une des valeurs suivantes :<br /><br /> **MSSQLSERVER**<br /><br /> **ORACLE**<br /><br /> **ORACLE GATEWAY**|  
|**publisher_data_source**|**nvarchar(4000)**|Nom de la source de données OLE DB sur le serveur de publication.|  
|**storage_connection_string**|**nvarchar(4000)**|Clé d’accès de stockage pour le répertoire de travail lors de serveur de distribution ou le serveur de publication dans la base de données SQL Azure.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpdistpublisher** est utilisée dans tous les types de réplication.  
  
 **sp_helpdistpublisher** n’affichera pas la connexion de serveur de publication ou de mot de passe dans le résultat défini pour non -**sysadmin** connexions.  
  
## <a name="permissions"></a>Permissions  
 Membres de la **sysadmin** du rôle serveur fixe peut-être exécuter **sp_helpdistpublisher** pour n’importe quel serveur de publication utilise le serveur local comme serveur de distribution. Membres de la **db_owner** rôle de base de données fixe ou le **replmonitor** du rôle dans une base de données de distribution peut-être exécuter **sp_helpdistpublisher** pour n’importe quel serveur de publication à l’aide qui base de données de distribution. Liste des utilisateurs de l’accès à une publication pour une publication à l’emplacement spécifié *publisher* peut s’exécuter **sp_helpdistpublisher**. Si *publisher* n’est pas spécifié, les informations sont retournées pour tous les serveurs de publication que l’utilisateur dispose des droits d’accès.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)  
  
  

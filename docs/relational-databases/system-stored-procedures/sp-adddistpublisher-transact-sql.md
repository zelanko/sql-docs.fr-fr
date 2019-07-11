---
title: sp_adddistpublisher (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adddistpublisher
- sp_adddistpublisher_TSQL
helpviewer_keywords:
- sp_adddistpublisher
ms.assetid: 04e15011-a902-4074-b38c-3ec2fc73b838
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b7f55d89054ff7d950921e0c6762770c6e714500
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716746"
---
# <a name="spadddistpublisher-transact-sql"></a>sp_adddistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Configure un serveur de publication pour qu'il utilise une base de données de distribution spécifique. Cette procédure stockée est exécutée sur le serveur de distribution sur une base de données. Notez que les procédures stockées [sp_adddistributor &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md) et [sp_adddistributiondb &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md) doit avoir été exécutées préalablement à l’aide de cette procédure procédure.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_adddistpublisher [ @publisher= ] 'publisher'   
        , [ @distribution_db= ] 'distribution_db'   
    [ , [ @security_mode= ] security_mode ]   
    [ , [ @login= ] 'login' ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @working_directory= ] 'working_directory' ]   
    [ , [ @storage_connection_string= ] 'storage_connection_string']
    [ , [ @trusted= ] 'trusted' ]   
    [ , [ @encrypted_password= ] encrypted_password ]   
    [ , [ @thirdparty_flag = ] thirdparty_flag ]  
    [ , [ @publisher_type = ] 'publisher_type' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'` Est le nom du serveur de publication. *serveur de publication* est **sysname**, sans valeur par défaut.  
  
`[ @distribution_db = ] 'distribution_db'` Est le nom de la base de données de distribution. *distributor_db* est **sysname**, sans valeur par défaut. Il est utilisé par les agents de réplication pour se connecter au serveur de publication.  
  
`[ @security_mode = ] security_mode` Est le mode de sécurité implémenté. Ce paramètre est utilisé uniquement par les agents de réplication pour se connecter au serveur de publication pour les abonnements mis à jour en file d’attente ou à un non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication. *security_mode* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**0**|Les Agents de réplication situés sur le serveur de distribution utilisent l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour se connecter au serveur de publication.|  
|**1** (par défaut)|Les agents de réplication situés sur le serveur de distribution utilisent l'authentification Windows pour se connecter au serveur de publication.|  
  
`[ @login = ] 'login'` Est le nom de connexion. Ce paramètre est obligatoire si *security_mode* est **0**. *login* est de type **sysname**, avec NULL comme valeur par défaut. Il est utilisé par les agents de réplication pour se connecter au serveur de publication.  
  
`[ @password = ] 'password']` Est le mot de passe. *mot de passe* est **sysname**, avec NULL comme valeur par défaut. Il est utilisé par les agents de réplication pour se connecter au serveur de publication.  
  
> [!IMPORTANT]  
>  N'utilisez pas de mot de passe vide. Utilisez un mot de passe fort.  
  
`[ @working_directory = ] 'working_directory'` Est le nom du répertoire de travail utilisé pour stocker les fichiers de données et le schéma de la publication. *working_directory* est **nvarchar (255)** et les valeurs par défaut pour le dossier ReplData pour cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], par exemple `C:\Program Files\Microsoft SQL Server\MSSQL\MSSQ.1\ReplData`. Le nom doit être indiqué au format UNC.  

 Pour la base de données SQL Azure, utilisez `\\<storage_account>.file.core.windows.net\<share>`.

`[ @storage_connection_string = ] 'storage_connection_string'` Est requis pour la base de données SQL. Utilisez la clé d’accès à partir du portail Azure sous stockage > Paramètres.

 > [!INCLUDE[Azure SQL Database link](../../includes/azure-sql-db-repl-for-more-information.md)]

`[ @trusted = ] 'trusted'` Ce paramètre a été déconseillé et est fourni pour la compatibilité descendante uniquement. *approuvé* est **nvarchar (5)** et la valeur n’est pas **false** entraîne une erreur.  
  
`[ @encrypted_password = ] encrypted_password` Paramètre *encrypted_password* n’est plus pris en charge. Tentez de définir cela **bits** paramètre **1** entraîne une erreur.  
  
`[ @thirdparty_flag = ] thirdparty_flag` Est lorsque le serveur de publication est [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *thirdparty_flag* est **bits**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**0** (valeur par défaut)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données.|  
|**1**|Base de données autre que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
  
`[ @publisher_type = ] 'publisher_type'` Spécifie le type de serveur de publication lorsque le serveur de publication n’est pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *publisher_type* est de type sysname et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**MSSQLSERVER**<br /><br /> (par défaut)|Spécifie un serveur de publication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**ORACLE**|Spécifie un serveur de publication Oracle standard.|  
|**ORACLE GATEWAY**|Spécifie un serveur de publication Oracle Gateway.|  
  
 Pour plus d’informations sur les différences entre un serveur de publication Oracle et un serveur de publication Oracle Gateway, consultez [configurer un serveur de publication Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_adddistpublisher** est utilisé par la réplication d’instantané, la réplication transactionnelle et la réplication de fusion.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#AddDistPub](../../relational-databases/replication/codesnippet/tsql/sp-adddistpublisher-tran_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_adddistpublisher**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer la publication et la distribution](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Configurer la distribution](../../relational-databases/replication/configure-distribution.md)  
  
  

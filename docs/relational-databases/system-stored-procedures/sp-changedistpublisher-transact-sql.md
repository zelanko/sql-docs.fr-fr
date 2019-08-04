---
title: sp_changedistpublisher (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changedistpublisher_TSQL
- sp_changedistpublisher
helpviewer_keywords:
- sp_changedistpublisher
ms.assetid: 7ef5c89d-faaa-4f8e-aef7-00649ebc8bc9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 80eb30fc6b6b2cea9fc058780831af3915fd9007
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771364"
---
# <a name="spchangedistpublisher-transact-sql"></a>sp_changedistpublisher (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Modifie les propriétés du serveur de publication de distribution. Cette procédure stockée est exécutée sur n’importe quelle base de données du serveur de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changedistpublisher [ @publisher = ] 'publisher'  
    [ , [ @property = ] 'property' ]  
    [ , [ @value = ] 'value' ]  
    [ , [ @storage_connection_string = ] 'storage_connection_string']
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'`Nom du serveur de publication. *Publisher* est de **type sysname**, sans valeur par défaut.  
  
`[ @property = ] 'property'`Propriété à modifier pour le serveur de publication donné. *Property* est de **type sysname** et peut prendre l’une des valeurs suivantes.  
  
`[ @value = ] 'value'`Valeur de la propriété donnée. la *valeur* est de type **nvarchar (255)** , avec NULL comme valeur par défaut.  
  
`[ @storage_connection_string = ] 'storage_connection_string'`Est requis pour SQL Database Managed instance, doit correspondre à la clé d’accès du volume de stockage Azure SQL Database. 


 > [!INCLUDE[Azure SQL Database link](../../includes/azure-sql-db-repl-for-more-information.md)]
 
 Le tableau ci-dessous décrit les propriétés des serveurs de publication et les valeurs de ces propriétés.  
  
|Propriété|Valeurs|Description|  
|--------------|------------|-----------------|  
|**active**|**true**|Active le serveur de publication.|  
||**false**|Désactive le serveur de publication.|  
|**distribution_db**||Nom de la base de données de distribution.|  
|**login**||Nom de connexion.|  
|**password**||Mot de passe fort pour le nom de connexion fourni.|  
|**security_mode**|**1**|Utiliser l'authentification Windows pour la connexion au serveur de publication. *Cela ne peut pas être modifié pour un* [!INCLUDE[msCoName](../../includes/msconame-md.md)] serveur de publication non- *.* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
||**0**|Utiliser l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la connexion au serveur de publication. *Cela ne peut pas être modifié pour un* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication non- *.*|  
|**working_directory**||Répertoire de travail utilisé pour stocker les fichiers de données et de schéma de la publication.|  
|NULL (par défaut)||Toutes les options de *propriété* disponibles sont imprimées.| 
|**storage_connection_string**| Clé d’accès | La clé d’accès pour le répertoire de travail lorsque la base de données est Azure SQL Database Managed Instance. 
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_changedistpublisher** est utilisé dans tous les types de réplications.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_changedistpublisher**.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

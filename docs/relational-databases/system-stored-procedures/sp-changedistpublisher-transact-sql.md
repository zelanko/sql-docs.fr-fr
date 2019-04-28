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
manager: craigg
ms.openlocfilehash: 06a0e5e2edb793a94e8d8542ca17734f23824121
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997816"
---
# <a name="spchangedistpublisher-transact-sql"></a>sp_changedistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés du serveur de publication de distribution. Cette procédure stockée est exécutée sur le serveur de distribution sur une base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changedistpublisher [ @publisher = ] 'publisher'  
    [ , [ @property = ] 'property' ]  
    [ , [ @value = ] 'value' ]  
    [ , [ @storage_connection_string = ] 'storage_connection_string']
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'` Est le nom du serveur de publication. *serveur de publication* est **sysname**, sans valeur par défaut.  
  
`[ @property = ] 'property'` Est une propriété à modifier pour le serveur de publication donné. *propriété* est **sysname** et peut prendre l’une des valeurs suivantes.  
  
`[ @value = ] 'value'` Est la valeur pour la propriété donnée. *valeur* est **nvarchar (255)**, avec NULL comme valeur par défaut.  
  
`[ @storage_connection_string = ] 'storage_connection_string'` Est requis pour l’instance managée de base de données SQL, doit correspondre à la clé d’accès pour le volume de stockage de base de données SQL Azure. 


 > [!INCLUDE[Azure SQL Database link](../../includes/azure-sql-db-repl-for-more-information.md)]
 
 Le tableau ci-dessous décrit les propriétés des serveurs de publication et les valeurs de ces propriétés.  
  
|Propriété|Valeurs|Description|  
|--------------|------------|-----------------|  
|**active**|**true**|Active le serveur de publication.|  
||**false**|Désactive le serveur de publication.|  
|**distribution_db**||Nom de la base de données de distribution.|  
|**login**||Nom de connexion.|  
|**password**||Mot de passe fort pour le nom de connexion fourni.|  
|**security_mode**|**1**|Utiliser l'authentification Windows pour la connexion au serveur de publication. *Cela ne peut pas être modifié pour non -* [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *serveur de publication.*|  
||**0**|Utiliser l'authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour la connexion au serveur de publication. *Cela ne peut pas être modifié pour non -* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *serveur de publication.*|  
|**working_directory**||Répertoire de travail utilisé pour stocker les fichiers de données et de schéma de la publication.|  
|NULL (par défaut)||Tous disponibles *propriété* options sont imprimées.| 
|**storage_connection_string**| Clé d’accès | La clé d’accès pour le répertoire de travail lors de la base de données est Azure SQL Database Managed Instance. 
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_changedistpublisher** est utilisée dans tous les types de réplication.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_changedistpublisher**.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les propriétés d’un serveur de distribution et d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

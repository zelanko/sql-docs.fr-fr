---
title: sp_help_targetserver (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_targetserver_TSQL
- sp_help_targetserver
dev_langs: TSQL
helpviewer_keywords: sp_help_targetserver
ms.assetid: f841d3bd-901a-4980-ad0b-1c6eeba3f717
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1542bc54c6c40b44f0738e249b4f609ac36b3b67
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sphelptargetserver-transact-sql"></a>sp_help_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Répertorie tous les serveurs cibles.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_targetserver   
     [ [ @server_name = ] 'server_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@server_name=** ] **'***nom_serveur***'**  
 Nom du serveur pour lequel renvoyer des informations. *nom_serveur* est **nvarchar (30)**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Si *nom_serveur* n’est pas spécifié, **sp_help_targetserver** retourne ce jeu de résultats.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Numéro d’identification du serveur.|  
|**nom_serveur**|**nvarchar (30)**|Nom du serveur.|  
|**emplacement**|**nvarchar(200)**|Emplacement du serveur spécifié.|  
|**TIME_ZONE_ADJUSTMENT**|**int**|Définition du fuseau horaire, en heures, par rapport à l'heure de Greenwich (GMT).|  
|**enlist_date**|**datetime**|Date d'inscription du serveur spécifié.|  
|**last_poll_date**|**datetime**|Date à laquelle le serveur a été interrogé pour la dernière fois pour des travaux.|  
|**status**|**int**|État du serveur spécifié.|  
|**unread_instructions**|**int**|Indique si le serveur a des instructions non lues. Si toutes les lignes ont été téléchargées, cette colonne est **0**.|  
|**local_time**|**datetime**|Heure et date locales sur le serveur cible, qui sont fonction de l'heure locale du serveur cible lors de la dernière interrogation du serveur maître.|  
|**enlisted_by_nt_user**|**nvarchar (100)**|Utilisateur Microsoft Windows ayant inscrit le serveur cible.|  
|**poll_interval**|**int**|Fréquence (en secondes) à laquelle le serveur cible interroge le service SQLServerAgent principal afin de télécharger des travaux et charger des états de travaux.|  
  
## <a name="permissions"></a>Permissions  
 Pour exécuter cette procédure stockée, l'utilisateur doit être membre du rôle de serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-listing-information-for-all-registered-target-servers"></a>A. Affichage d'informations pour tous les serveurs cibles enregistrés  
 L'exemple suivant produit une liste d'informations pour tous les serveurs cibles enregistrés.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetserver ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-target-server"></a>B. Affichage d'informations pour un serveur cible spécifique  
 L'exemple suivant produit une liste d'informations pour le serveur cible `SEATTLE2`.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_targetserver N'SEATTLE2' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_targetservergroup &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-add-targetservergroup-transact-sql.md)   
 [sp_delete_targetserver &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-targetserver-transact-sql.md)   
 [sp_delete_targetservergroup &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-delete-targetservergroup-transact-sql.md)   
 [sp_update_targetservergroup &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-update-targetservergroup-transact-sql.md)   
 [dbo.sysdownloadlist &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysdownloadlist-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

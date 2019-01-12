---
title: sp_changereplicationserverpasswords (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changereplicationserverpasswords_TSQL
- sp_changereplicationserverpasswords
helpviewer_keywords:
- sp_changereplicationserverpasswords
ms.assetid: 9333da96-3a1c-4adb-9a74-5dac9ce596df
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: bfe5d9f7bc5c95055af06b0582f2ddcf88ae7cdf
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54125709"
---
# <a name="spchangereplicationserverpasswords-transact-sql"></a>sp_changereplicationserverpasswords (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les mots de passe stockés pour le [!INCLUDE[msCoName](../../includes/msconame-md.md)] compte de Windows ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion utilisée par les agents de réplication lors de la connexion aux serveurs dans une topologie de réplication. En temps normal, vous devriez modifier un mot de passe pour chacun des Agents en cours d'exécution sur un serveur, même s'ils utilisent tous la même connexion ou le même compte. Cette procédure stockée vous permet de modifier le mot de passe pour toutes les instances d'une connexion ou d'un compte [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] donnés utilisés par tous les Agents de réplication exécutés sur un serveur. Cette procédure stockée est exécutée sur la base de données master de n'importe quel serveur de la topologie de réplication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changereplicationserverpasswords [ @login_type = ] login_type  
        , [ @login = ] 'login'   
        , [ @password = ] 'password'  
    [ , [ @server = ] 'server' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@login_type** =] *login_type*  
 Type d'authentification des informations d'identification fournies. *LOGIN_TYPE* est **tinyint**, sans valeur par défaut.  
  
 **1** = authentification intégrée de Windows  
  
 **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification  
  
 [ **@login** =] **'**_connexion_**'**  
 Nom du compte Windows ou de la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cours de modification. *connexion* est **nvarchar (257)**, sans valeur par défaut  
  
 [ **@password** =] **'**_mot de passe_**'**  
 Nouveau mot de passe à stocker pour spécifié *connexion*. *mot de passe* est **sysname**, sans valeur par défaut.  
  
> [!NOTE]  
>  Après avoir modifié un mot de passe de réplication, vous devez arrêter puis redémarrer chaque Agent qui utilise ce mot de passe afin que les modifications apportées prennent effet.  
  
 [ **@server** =] **'**_server_**'**  
 Connexion serveur pour laquelle le mot de passe stocké est en cours de changement. *serveur* est **sysname**, et peut prendre l’une des valeurs suivantes :  
  
|Value|Description|  
|-----------|-----------------|  
|**serveur de distribution**|Toutes les connexions d'Agent au serveur de distribution.|  
|**publisher** (serveur de publication)|Toutes les connexions d'Agent au serveur de publication.|  
|**subscriber** (Abonné)|Toutes les connexions d'Agent à l'Abonné.|  
|**%** (valeur par défaut)|Toutes les connexions d'Agent à tous les serveurs d'une topologie de réplication.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_changereplicationserverpasswords** est utilisé avec tous les types de réplication.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_changereplicationserverpasswords**.  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher et modifier les paramètres de sécurité de la réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)  
  
  

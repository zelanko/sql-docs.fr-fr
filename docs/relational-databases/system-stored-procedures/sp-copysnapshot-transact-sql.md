---
title: sp_copysnapshot (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_copysnapshot
- sp_copysnapshot_TSQL
helpviewer_keywords:
- sp_copysnapshot
ms.assetid: a012a32f-6f26-45bf-8046-b51cd7fec455
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7e857539c26f7806712c3c8e0fd4222064eac8c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68108704"
---
# <a name="spcopysnapshot-transact-sql"></a>sp_copysnapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Copie le dossier de capture instantanée de la publication spécifiée vers le dossier indiqué dans le **@destination_folder** . Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication. Elle permet de copier un instantané sur un support amovible, tel qu'un CD-ROM.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_copysnapshot [ @publication = ] 'publication', [ @destination_folder = ] 'destination_folder' ]  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @subscriber_db = ] 'subscriber_db' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication dont le contenu instantané doivent être copiés. *publication* est **sysname**, sans valeur par défaut.  
  
`[ @destination_folder = ] 'destination_folder'` Est le nom du dossier dans lequel le contenu de l’instantané de publication doivent être copiés. *destination_folder*est **nvarchar (255)** , sans valeur par défaut. Le *destination_folder* peut être un autre emplacement comme sur un autre serveur, sur un lecteur réseau ou sur un support amovible (CD-ROM ou disque).  
  
`[ @subscriber = ] 'subscriber'` Est le nom de l’abonné. *abonné* est de type sysname, avec NULL comme valeur par défaut.  
  
`[ @subscriber_db = ] 'subscriber_db'` Est le nom de la base de données d’abonnement. *bd_abonné* est de type sysname, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_copysnapshot** est utilisée dans tous les types de réplication. Les abonnés exécutant [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 et antérieure ne peut pas utiliser l’emplacement d’instantanés de remplacement.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_copysnapshot**.  
  
## <a name="see-also"></a>Voir aussi  
 [Autres emplacements du dossier d’instantanés](../../relational-databases/replication/snapshot-options.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

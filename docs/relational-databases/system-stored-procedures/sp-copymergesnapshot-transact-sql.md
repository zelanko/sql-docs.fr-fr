---
title: sp_copymergesnapshot (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_copymergesnapshot
- sp_copymergesnapshot_TSQL
helpviewer_keywords: sp_copymergesnapshot
ms.assetid: eaecd6e0-8486-4e5d-ace7-8ae75768c0a8
caps.latest.revision: "26"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ff82ac5788461d396ba64279d073d8eda62d0c1e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spcopymergesnapshot-transact-sql"></a>sp_copymergesnapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Copie le dossier de capture instantanée de la publication spécifiée vers le dossier indiqué dans le  **@destination_folde**  *r*. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_copymergesnapshot [ @publication = ] 'publication', [ @destination_folder = ] 'destination_folder'  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@publication=**] **'***publication***'**  
 Nom de la publication dont le contenu de l'instantané doit être copié. *publication* est **sysname**, sans valeur par défaut.  
  
 [  **@destination_folder=**] **'***destination_folder***'**  
 Nom du dossier dans lequel le contenu d'instantané de la publication doit être copié. *destination_folder*est **nvarchar (255)**, sans valeur par défaut. Le *destination_folder* peut être un autre emplacement comme sur un autre serveur, sur un lecteur réseau ou sur un support amovible (CD-ROM ou des disques amovibles).  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_copymergesnapshot** est utilisé dans la réplication de fusion. Les abonnés exécutant [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0 et antérieure ne peut pas utiliser cet emplacement.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** du rôle de base de données fixe peut exécuter **sp_copymergesnapshot**.  
  
## <a name="see-also"></a>Voir aussi  
 [Autres emplacements du dossier d’instantanés](../../relational-databases/replication/alternate-snapshot-folder-locations.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

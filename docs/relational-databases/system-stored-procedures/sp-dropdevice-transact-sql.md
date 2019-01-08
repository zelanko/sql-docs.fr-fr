---
title: sp_dropdevice (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropdevice_TSQL
- sp_dropdevice
dev_langs:
- TSQL
helpviewer_keywords:
- backup devices [SQL Server], deleting
- sp_dropdevice
ms.assetid: c8b07189-7c35-414b-acc1-45bd6e7e17c3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ee0703a0dca2c6ba958f52dee0f8850ea2c8244e
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52536392"
---
# <a name="spdropdevice-transact-sql"></a>sp_dropdevice (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un périphérique de base de données ou d’une unité de sauvegarde à partir d’une instance de la [!INCLUDE[ssDEversion2005](../../includes/ssdeversion2005-md.md)], suppression de l’entrée à partir de **master.dbo.sysdevices**.  
   
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dropdevice [ @logicalname = ] 'device'   
    [ , [ @delfile = ] 'delfile' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@logicalname=** ] **'**_appareil_**'**  
 Est le nom de l’unité de base de données ou d’une unité de sauvegarde logique comme indiqué dans **master.dbo.sysdevices.name**. *APPAREIL* est **sysname**, sans valeur par défaut.  
  
 [  **@delfile=** ] **'**_delfile_**'**  
 Spécifie si le fichier de l'unité de sauvegarde physique doit être supprimé. *delfile* est **varchar(7)**. S’il est spécifié en tant que **DELFILE**, le fichier de disque d’unité de sauvegarde physique est supprimé.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 **sp_dropdevice** ne peut pas être utilisé dans une transaction.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle serveur fixe **diskadmin** .  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant supprime le `tapedump1` unité de sauvegarde sur bande à partir de la [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
```  
EXEC sp_dropdevice 'tapedump1';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Unités de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [Supprimer une unité de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/delete-a-backup-device-sql-server.md)   
 [sp_addumpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql.md)   
 [sp_helpdb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdb-transact-sql.md)   
 [sp_helpdevice &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdevice-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

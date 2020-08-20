---
description: sp_restoredbreplication (Transact-SQL)
title: sp_restoredbreplication (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_restoredbreplication
- sp_restoredbreplication_TSQL
helpviewer_keywords:
- sp_restoredbreplication
ms.assetid: a2c5ee32-e6d9-46e9-8031-8ff13c20acf7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b75fb66ba210f8981ab5a61e635030d2d7c941a8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473828"
---
# <a name="sp_restoredbreplication-transact-sql"></a>sp_restoredbreplication (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Supprime les paramètres de réplication si une base de données est restaurée vers un serveur, une base de données ou un système non source, normalement incapables d'exécuter des processus de réplication. Lorsque vous restaurez une base de données répliquée vers un serveur ou une base de données autres que ceux à partir desquels la sauvegarde a été créée, les paramètres de réplication ne peuvent pas être préservés. Lors de la restauration, le serveur appelle **sp_restoredbreplication** directement pour supprimer automatiquement les métadonnées de réplication de la base de données restaurée.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_restoredbreplication [ @srv_orig = ] 'original_server_name'  
        , [ @db_orig = ] 'original_database_name'  
    [ , [ @keep_replication = ] keep_replication ]  
    [ , [ @perform_upgrade = ] perform_upgrade ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @srv_orig = ] 'original_server_name'`  
 Nom du serveur sur lequel la sauvegarde a été créée. *original_server_name* est de **type sysname**, sans valeur par défaut.  
  
`[ @db_orig = ] 'original_database_name'`  
 Le nom de la base de données qui a été sauvegardée. *original_database_name* est de **type sysname**, sans valeur par défaut.  
  
`[ @keep_replication = ] keep_replication`  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
`[ @perform_upgrade = ] perform_upgrade`  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_restoredbreplication** est utilisé dans tous les types de réplications.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou **dbcreator** ou du schéma de base de données **dbo** peuvent exécuter **sp_restoredbreplication**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  

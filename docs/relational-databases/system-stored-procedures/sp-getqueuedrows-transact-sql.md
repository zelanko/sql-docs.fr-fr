---
description: sp_getqueuedrows (Transact-SQL)
title: sp_getqueuedrows (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getqueuedrows_TSQL
- sp_getqueuedrows
helpviewer_keywords:
- sp_getqueuedrows
ms.assetid: 139e834f-1988-4b4d-ac81-db1f89ea90e8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6948964a224d0dfe1d36324971608e649ec45d4e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481255"
---
# <a name="sp_getqueuedrows-transact-sql"></a>sp_getqueuedrows (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Extrait, de l'Abonné, les lignes pour lesquelles il existe des mises à jour dans la file d'attente. Cette procédure stockée est exécutée sur la base de données d'abonnement de l'Abonné.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_getqueuedrows [ @tablename = ] 'tablename'  
    [ , [ @owner = ] 'owner'  
    [ , [ @tranid = ] 'transaction_id' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @tablename = ] 'tablename'` Nom de la table. *TableName* est de **type sysname**, sans valeur par défaut. La table doit faire partie d'un abonnement en file d'attente.  
  
`[ @owner = ] 'owner'` Est le propriétaire de l’abonnement. *owner* est de **type sysname**, avec NULL comme valeur par défaut.  
  
`[ @tranid = ] 'transaction_id'` Autorise le filtrage de la sortie par l’ID de transaction. *transaction_id* est de type **nvarchar (70)**, avec NULL comme valeur par défaut. Si cet argument est défini, l'identificateur de transaction associé à la commande placée en file d'attente est affiché. Si la valeur est NULL, toutes les commandes figurant dans la file d'attente sont affichées.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Affiche toutes les lignes détenant actuellement au moins une transaction en attente pour la table d'abonnement.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**Action**|**nvarchar(10**|Type d'action à appliquer au moment de la synchronisation.<br /><br /> INS= insertion <br /><br /> DEL = suppression<br /><br /> UPD = mise à jour|  
|**Tranid**|**nvarchar (70)**|Identificateur de transaction sous lequel la commande a été exécutée.|  
|**table column1...n**||Valeur de chaque colonne de la table spécifiée dans *TableName*.|  
|**msrepl_tran_version**|**uniqueidentifier**|Cette colonne permet d'assurer le suivi des modifications apportées aux données répliquées et de détecter les conflits sur le serveur de publication. Cette colonne est automatiquement ajoutée à la table.|  
  
## <a name="remarks"></a>Notes  
 **sp_getqueuedrows** est utilisé sur les abonnés participant à la mise à jour en attente.  
  
 **sp_getqueuedrows** recherche les lignes d’une table donnée sur une base de données d’abonnement qui ont participé à une mise à jour en file d’attente, mais qui n’ont pas encore été résolues par l’agent de lecture de la file d’attente.  
  
## <a name="permissions"></a>Autorisations  
 **sp_getqueuedrows** nécessite des autorisations SELECT sur la table spécifiée dans *TableName*.  
  
## <a name="see-also"></a>Voir aussi  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Détection et résolution des conflits de mise à jour en attente](../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

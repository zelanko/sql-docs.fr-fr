---
description: sp_repltrans (Transact-SQL)
title: sp_repltrans (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repltrans_TSQL
- sp_repltrans
helpviewer_keywords:
- sp_repltrans
ms.assetid: 738e2322-335b-44fa-820e-f31c02743978
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c6a80364b3df96bb454cf9d43f1de2ee217a796f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481090"
---
# <a name="sp_repltrans-transact-sql"></a>sp_repltrans (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Renvoie un jeu de résultats pour toutes les transactions du journal des transactions de la base de données de publication qui sont marquées pour la réplication mais qui n'ont pas été signalées comme distribuées. Cette procédure stockée est exécutée sur une base de données de publication du serveur de publication.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_repltrans  
```  
  
## <a name="result-sets"></a>Jeux de résultats  
 **sp_repltrans** retourne des informations sur la base de données de publication à partir de laquelle elle est exécutée, ce qui vous permet d’afficher les transactions non distribuées actuellement (les transactions restantes dans le journal des transactions qui n’ont pas été envoyées au serveur de distribution). L'ensemble de résultats affiche les numéros séquentiels dans le journal du premier et du dernier enregistrement de chaque transaction. **sp_repltrans** est semblable à [sp_replcmds &#40;Transact-SQL&#41;, ](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) mais ne retourne pas les commandes pour les transactions.  
  
## <a name="remarks"></a>Notes  
 **sp_repltrans** est utilisé dans la réplication transactionnelle.  
  
 **sp_repltrans** n’est pas pris en charge pour les serveurs de publication non- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_repltrans**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

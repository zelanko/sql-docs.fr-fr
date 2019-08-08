---
title: sp_repldone (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repldone
- sp_repldone_TSQL
helpviewer_keywords:
- sp_repldone
ms.assetid: 045d3cd1-712b-44b7-a56a-c9438d4077b9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 35cd38269fabba59d257e41141141764b6d4919d
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771113"
---
# <a name="sp_repldone-transact-sql"></a>sp_repldone (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Met à jour l'enregistrement identifiant la dernière transaction distribuée du serveur. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
> [!CAUTION]  
>  Si vous exécutez **sp_repldone** manuellement, vous pouvez invalider l’ordre et la cohérence des transactions remises. **sp_repldone** doit uniquement être utilisé pour résoudre les problèmes de réplication, comme indiqué par un professionnel expérimenté du support de la réplication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_repldone [ @xactid= ] xactid   
        , [ @xact_seqno= ] xact_seqno   
    [ , [ @numtrans= ] numtrans ]   
    [ , [ @time= ] time   
    [ , [ @reset= ] reset ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @xactid = ] xactid`Numéro séquentiel dans le journal (LSN) du premier enregistrement de la dernière transaction distribuée du serveur. *xactid* est de **type Binary (10)** , sans valeur par défaut.  
  
`[ @xact_seqno = ] xact_seqno`LSN du dernier enregistrement de la dernière transaction distribuée du serveur. *xact_seqno* est de **type Binary (10)** , sans valeur par défaut.  
  
`[ @numtrans = ] numtrans`Nombre de transactions distribuées. *numtrans* est de **type int**, sans valeur par défaut.  
  
`[ @time = ] time`Nombre de millisecondes, s’il est fourni, nécessaires pour distribuer le dernier lot de transactions. l' *heure* est de **type int**, sans valeur par défaut.  
  
`[ @reset = ] reset`Est l’état de réinitialisation. *Reset* est de **type int**, sans valeur par défaut. Si la **1**est définie, toutes les transactions répliquées dans le journal sont marquées comme distribuées. Si la **valeur est 0**, le journal des transactions est réinitialisé à la première transaction répliquée et aucune transaction répliquée n’est marquée comme distribuée. la réinitialisation est valide uniquement lorsque *xactid* et *xact_seqno* sont null.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_repldone** est utilisé dans la réplication transactionnelle.  
  
 **sp_repldone** est utilisé par le processus de lecture du journal pour effectuer le suivi des transactions qui ont été distribuées.  
  
 Avec **sp_repldone**, vous pouvez indiquer manuellement au serveur qu’une transaction a été répliquée (envoyée au serveur de distribution). Elle vous permet également de modifier la transaction marquée comme étant la prochaine en attente de réplication. Il est possible d'avancer et de reculer dans la liste des transactions répliquées. (Toutes les transactions antérieures ou simultanées à cette transaction seront signalées comme distribuées).  
  
 Les paramètres requis *xactid* et *xact_seqno* peuvent être obtenus à l’aide de **sp_repltrans** ou de **sp_replcmds**.  
  
## <a name="permissions"></a>Autorisations  
 Les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_repldone**.  
  
## <a name="examples"></a>Exemples  
 Quand *xactid* a la valeur null, *xact_seqno* a la valeur null, et *Reset* a la valeur **1**, toutes les transactions répliquées dans le journal sont marquées comme distribuées. Cette fonction est utile lorsque il y a des transactions répliquées situées dans le journal des transactions qui ne sont plus valides et que vous désirez tronquer le journal, par exemple :  
  
```  
EXEC sp_repldone @xactid = NULL, @xact_segno = NULL, @numtrans = 0,     @time = 0, @reset = 1  
```  
  
> [!CAUTION]  
>  Cette procédure peut être utilisée dans les situations d'urgence pour permettre la troncature du journal des transactions lorsque des transactions en attente de réplication sont présentes.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

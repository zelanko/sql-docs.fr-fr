---
title: Interrogation des procédures stockées étendues
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: 875d4f252058d442c91915eb69784507c39b2e94
ms.sourcegitcommit: 15fe0bbba963d011472cfbbc06d954d9dbf2d655
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74095946"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>Interrogation des procédures stockées étendues installées dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez l’intégration CLR à la place.  
  
 Un utilisateur authentifié [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut afficher les procédures stockées étendues actuellement définies et le nom de la DLL à laquelle chaque appartient en exécutant la procédure système **sp_helpextendedproc** . Par exemple, l’exemple suivant retourne la DLL à laquelle **xp_hello** appartient :  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 Si **sp_helpextendedproc** est exécutée sans spécifier de procédure stockée étendue, toutes les procédures stockées étendues et leurs dll sont affichées.  
  
> [!IMPORTANT]  
>  Des informations sont retournées uniquement pour les procédures stockées étendues qui appartiennent à l'utilisateur connecté ou sur lesquelles il possède des autorisations. Seuls les membres du rôle serveur fixe **sysadmin** et des rôles de base de données fixe **db_owner**, **db_securityadmin**et **db_ddladmin** peuvent afficher des informations pour toutes les procédures stockées étendues.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [sp_addextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  

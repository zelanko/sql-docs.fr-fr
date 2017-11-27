---
title: "Interrogation des procédures stockées étendues installées dans SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5d17f27bf2d9822886c022103fae5834d8b4fddc
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>Interrogation des procédures stockées étendues installées dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Utilisez l’intégration du CLR à la place.  
  
 A [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisateur authentifié peut afficher actuellement défini des procédures stockées étendues et le nom de la DLL dans laquelle chacune appartient en exécutant la **sp_helpextendedproc** procédure système. Par exemple, l’exemple suivant retourne la DLL à laquelle **xp_hello** appartient :  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 Si **sp_helpextendedproc** est exécutée sans spécifier une procédure stockée étendue, toutes les procédures stockées étendues et leurs DLL est affichés.  
  
> [!IMPORTANT]  
>  Des informations sont retournées uniquement pour les procédures stockées étendues qui appartiennent à l'utilisateur connecté ou sur lesquelles il possède des autorisations. Seuls les membres de la **sysadmin** rôle serveur fixe et le **db_owner**, **db_securityadmin**et le **db_ddladmin** des rôles de base de données fixe peuvent afficher des informations pour toutes les procédures stockées étendues.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_helpextendedproc &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [sp_addextendedproc &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  

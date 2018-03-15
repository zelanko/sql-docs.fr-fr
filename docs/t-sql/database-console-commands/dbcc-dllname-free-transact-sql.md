---
title: DBCC dllname (FREE) (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|database-console-commands
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbcc_dllname_(FREE)_TSQL
- dllname
- dbcc dllname (FREE)
- FREE
- dbcc_dllname(FREE)_TSQL
- FREE_TSQL
- dllname_TSQL
- dbcc dllname(FREE)
dev_langs:
- TSQL
helpviewer_keywords:
- DLL unloading [SQL Server]
- DBCC dllname (FREE)
- freeing DLLs
- unloading DLLs
ms.assetid: 1eb71c17-fe15-430b-8916-e4e312dcf9c0
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0ad6b900d45ef1c87c0aca0d961685c68a72a33d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="dbcc-dllname-free-transact-sql"></a>DBCC dllname (FREE) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)] Décharge la DLL de procédure stockée étendue spécifiée de la mémoire.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
```sql
DBCC <dllname> ( FREE ) [ WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Arguments  
 \<*dllname*>  
 Nom de la DLL à libérer de la mémoire.  
  
 WITH NO_INFOMSGS  
 Supprime tous les messages d'information.  
  
## <a name="remarks"></a>Notes 
Lorsqu'une procédure stockée étendue est exécutée, la DLL reste chargée par l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jusqu'à l'arrêt du serveur. Cette instruction permet de décharger une DLL de la mémoire sans arrêter [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour afficher les fichiers DLL actuellement chargés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], exécutez **sp_helpextendedproc**
  
## <a name="result-sets"></a>Jeux de résultats  
Quand une DLL valide est spécifiée, DBCC *dllname* (FREE) retourne :
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Autorisations  
Nécessite l’appartenance au rôle de serveur fixe **sysadmin** ou au rôle de base de données fixe **db_owner** .
  
## <a name="examples"></a>Exemples  
L’exemple suivant suppose que `xp_sample` est implémenté en tant que fichier xp_sample.dll et a été exécuté. DBCC \<*dllname*> (FREE) décharge le fichier xp_sample.dll associé à la procédure étendue `xp_sample`.
  
```sql  
DBCC xp_sample (FREE);  
```  
  
## <a name="see-also"></a> Voir aussi  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Caractéristiques d'exécution des procédures stockées étendues](../../relational-databases/extended-stored-procedures-programming/execution-characteristics-of-extended-stored-procedures.md)  
[sp_addextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)  
[sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
[sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)  
[Déchargement d’une DLL de procédure stockée étendue](../../relational-databases/extended-stored-procedures-programming/unloading-an-extended-stored-procedure-dll.md)
  
  

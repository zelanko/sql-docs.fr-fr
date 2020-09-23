---
description: DBCC dllname (FREE) (Transact-SQL)
title: DBCC dllname (FREE) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: pmasl
ms.author: umajay
ms.openlocfilehash: 0fd6d497ed6738d6ef290645df9bcad18ca6df32
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91116935"
---
# <a name="dbcc-dllname-free-transact-sql"></a>DBCC dllname (FREE) (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
Décharge les DLL de procédure stockée étendue spécifiées de la mémoire.
  
![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
```syntaxsql
DBCC <dllname> ( FREE ) [ WITH NO_INFOMSGS ]  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

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
L’exemple suivant suppose que `xp_sample` est implémenté en tant que fichier xp_sample.dll et a été exécuté. L'instruction DBCC \<*dllname*> (FREE) décharge le fichier xp_sample.dll associé à la procédure étendue `xp_sample`.
  
```sql  
DBCC xp_sample (FREE);  
```  
  
## <a name="see-also"></a>Voir aussi  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Caractéristiques d'exécution des procédures stockées étendues](../../relational-databases/extended-stored-procedures-programming/execution-characteristics-of-extended-stored-procedures.md)  
[sp_addextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)  
[sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
[sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)  
[Déchargement d’une DLL de procédure stockée étendue](../../relational-databases/extended-stored-procedures-programming/unloading-an-extended-stored-procedure-dll.md)
  
  

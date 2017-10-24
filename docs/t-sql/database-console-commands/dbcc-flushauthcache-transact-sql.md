---
title: DBCC FLUSHAUTHCACHE (Transact-SQL) | Documents Microsoft
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC FLUSHAUTHCACHE
- FLUSHAUTHCACHE
- DBCC_FLUSHAUTHCACHE_TSQL
- FLUSHAUTHCACHE_TSQL
helpviewer_keywords:
- DBCC FLUSHAUTHCACHE
ms.assetid: 681ef31d-ceb9-4da5-86bf-bf1240df950f
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3ba6a519ebcdbbc70bf19ec491539a3b07fb6c85
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-flushauthcache-transact-sql"></a>DBCC FLUSHAUTHCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Vide le cache de l’authentification de base de données contenant des informations sur les connexions et les règles de pare-feu, pour la base de données de l’utilisateur actuel dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Cette instruction ne s’applique pas à la base de données master logique, car la base de données master contient le stockage physique pour obtenir les informations sur les connexions et les règles de pare-feu. L’utilisateur qui exécute l’instruction et les autres utilisateurs actuellement connectés restent connectés. (DBCC FLUSHAUTHCACHE n’est pas pris en charge actuellement pour [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)].)
 
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
DBCC FLUSHAUTHCACHE [ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
Aucun.
  
## <a name="remarks"></a>Notes  
Le cache d’authentification effectue une copie des connexions et des règles de pare-feu de serveur qui sont stockés dans le master et les place en mémoire dans la base de données utilisateur.  Étant donné que les informations sur les utilisateurs de base de données sont déjà stockés dans la base de données utilisateur, les utilisateurs de base de données ne font pas partie du cache d’authentification.
Connexions actives en permanence à [!INCLUDE[ssSDS](../../includes/sssds-md.md)] nécessitent une nouvelle autorisation (effectuées par le [!INCLUDE[ssDE](../../includes/ssde-md.md)]) au moins toutes les 10 heures. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] une nouvelle autorisation de tentatives en utilisant le mot de passe à l’origine envoyé et aucun utilisateur d’entrée est requis. Pour des raisons de performances, lorsqu’un mot de passe est réinitialisé dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)], la connexion ne sera pas authentifiée de nouveau, même si la connexion est réinitialisée suite à un regroupement de connexion. Cela est différent du comportement de local [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si le mot de passe a été modifié, car la connexion a été initialement autorisée, la connexion doit se terminer et établir une nouvelle connexion à l’aide du nouveau mot de passe. Un utilisateur avec l’autorisation de supprimer la connexion de base de données peut terminer explicitement une connexion à [!INCLUDE[ssSDS](../../includes/sssds-md.md)] à l’aide de la [KILL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/kill-transact-sql.md) commande.
  
## <a name="permissions"></a>Permissions  
Nécessite le [!INCLUDE[ssSDS](../../includes/sssds-md.md)] compte d’administrateur.
  
## <a name="example"></a>Exemple  
L’instruction suivante supprime le cache d’authentification pour la base de données actuelle.
  
```sql
DBCC FLUSHAUTHCACHE;  
```  
  
## <a name="see-also"></a>Voir aussi  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  
  


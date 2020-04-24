---
title: DBCC FLUSHAUTHCACHE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC FLUSHAUTHCACHE
- FLUSHAUTHCACHE
- DBCC_FLUSHAUTHCACHE_TSQL
- FLUSHAUTHCACHE_TSQL
helpviewer_keywords:
- DBCC FLUSHAUTHCACHE
ms.assetid: 681ef31d-ceb9-4da5-86bf-bf1240df950f
author: VanMSFT
ms.author: vanto
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 15b8116b0677ebfccece9c13a49480d6702c6c54
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81631321"
---
# <a name="dbcc-flushauthcache-transact-sql"></a>DBCC FLUSHAUTHCACHE (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

Vide le cache d’authentification de la base de données contenant des informations sur les connexions et les règles de pare-feu, pour la base de données utilisateur actuelle dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)]. Cette instruction ne s’applique pas à la base de données MASTER logique, car la base de données MASTER contient le stockage physique des informations sur les connexions et les règles de pare-feu. L’utilisateur qui exécute l’instruction et les autres utilisateurs actuellement connectés restent connectés. (DBCC FLUSHAUTHCACHE n’est à l’heure actuelle pas pris en charge pour [!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)].)
 
![Icône Lien d’article](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien d’article") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```syntaxsql
DBCC FLUSHAUTHCACHE [ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
Aucun.
  
## <a name="remarks"></a>Notes  
Le cache d’authentification effectue une copie des connexions et des règles de pare-feu de serveur stockées dans la base de données MASTER, puis les place en mémoire dans la base de données utilisateur.  Comme les informations sur les utilisateurs de la base de données autonome sont déjà stockées dans la base de données utilisateur, ces utilisateurs ne font pas partie du cache d’authentification.
Des connexions actives en permanence à [!INCLUDE[ssSDS](../../includes/sssds-md.md)] nécessitent une réautorisation (effectuée par le [!INCLUDE[ssDE](../../includes/ssde-md.md)]) au moins toutes les 10 heures. Le [!INCLUDE[ssDE](../../includes/ssde-md.md)] tente une réautorisation en utilisant le mot de passe envoyé à l’origine et aucune entrée utilisateur n’est nécessaire. Pour des raisons de performances, à la réinitialisation d’un mot de passe dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)], la connexion n’est pas authentifiée de nouveau, même si elle est réinitialisée en raison d’un regroupement de connexions. Ce comportement est différent de celui de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en local. Si le mot de passe a été modifié depuis que la connexion a été initialement autorisée, celle-ci doit être interrompue et une nouvelle connexion établie avec le nouveau mot de passe. Un utilisateur avec l’autorisation KILL DATABASE CONNECTION peut mettre fin explicitement à une connexion à [!INCLUDE[ssSDS](../../includes/sssds-md.md)] à l’aide de la commande [KILL &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-transact-sql.md).
  
## <a name="permissions"></a>Autorisations  
Nécessite le compte administrateur [!INCLUDE[ssSDS](../../includes/sssds-md.md)].
  
## <a name="example"></a>Exemple  
L’instruction suivante efface le cache d’authentification pour la base de données actuelle.
  
```sql
DBCC FLUSHAUTHCACHE;  
```  
  
## <a name="see-also"></a>Voir aussi  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)
  

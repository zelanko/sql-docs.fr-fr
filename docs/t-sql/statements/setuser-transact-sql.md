---
title: SETUSER (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SETUSER_TSQL
- SETUSER
dev_langs: TSQL
helpviewer_keywords:
- delegation [SQL Server]
- impersonation [SQL Server]
- SETUSER statement
- user impersonation [SQL Server]
ms.assetid: 7acfac5c-9ad6-4226-b874-7add36c4ea43
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a511e0337201c9b4501b5274fa8270fbebf7da50
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="setuser-transact-sql"></a>SETUSER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Permet à un membre de la **sysadmin** rôle serveur fixe ou le propriétaire d’une base de données d’emprunter l’identité d’un autre utilisateur.  
  
> [!IMPORTANT]  
>  L'instruction SETUSER est incluse pour des raisons de compatibilité descendante uniquement. Elle ne sera peut-être plus prise en charge dans une version future de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Nous vous recommandons d’utiliser [EXECUTE AS](../../t-sql/statements/execute-as-transact-sql.md) à la place.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SETUSER [ 'username' [ WITH NORESET ] ]   
```  
  
## <a name="arguments"></a>Arguments  
 **'** *nom d’utilisateur* **'**  
 Nom d'un utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou Windows dans la base de données active dont l'identité est empruntée. Lorsque *nom d’utilisateur* n’est pas spécifié, l’identité d’origine de l’administrateur système ou le propriétaire de la base de données empruntant l’identité de l’utilisateur est réinitialisée.  
  
 WITH NORESET  
 Spécifie qu’ultérieures instructions SETUSER (sans aucune spécifié *nom d’utilisateur*) ne doivent pas réaffecter l’identité de l’utilisateur à l’administrateur système ou propriétaire de la base de données.  
  
## <a name="remarks"></a>Notes  
 SETUSER peut être utilisée par un membre de la **sysadmin** rôle serveur fixe ou le propriétaire d’une base de données pour prendre l’identité d’un autre utilisateur pour tester les autorisations de l’autre utilisateur. L’appartenance au rôle de base de données fixé db_owner n’est pas suffisant.  
  
 Utilisez SETUSER uniquement avec des utilisateurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. SETUSER n'est pas prise en charge avec les utilisateurs Windows. Lorsque l'instruction SETUSER est exécutée pour représenter un autre utilisateur, tout objet créé par l'utilisateur qui emprunte l'identité est la propriété de l'utilisateur représenté. Par exemple, si le propriétaire de la base de données utilise l’identité d’utilisateur **Margaret** et crée une table appelée **commandes**, le **commandes** table est détenue par **Margaret**, pas l’administrateur système.  
  
 L'instruction SETUSER reste active jusqu'à ce qu'une autre instruction SETUSER soit exécutée ou jusqu'à ce que l'on change de base de données active à l'aide de l'instruction USE.  
  
> [!NOTE]  
>  Si l'instruction SETUSER WITH NORESET est exécutée, le propriétaire de la base de données ou l'administrateur système doit rétablir ses propres droits en se déconnectant, puis en se connectant de nouveau.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’appartenance dans le **sysadmin** rôle serveur fixe ou doit être le propriétaire de la base de données. L’appartenance à la **db_owner** ne suffit pas de rôle de base de données fixe  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant montre comment le propriétaire d'une base de données peut prendre l'identité d'un autre utilisateur. L'utilisateur `mary` a créé une table appelée `computer_types`. À l'aide de l'instruction SETUSER, le propriétaire de la base de données représente `mary` pour autoriser l'utilisateur `joe` à accéder à la table `computer_types`, puis rétablit sa propre identité.  
  
```  
SETUSER 'mary';  
GO  
GRANT SELECT ON computer_types TO joe;  
GO  
--To revert to the original user  
SETUSER;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [USE &#40;Transact-SQL&#41;](../../t-sql/language-elements/use-transact-sql.md)  
  
  

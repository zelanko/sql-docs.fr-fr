---
title: IS_MEMBER (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS_MEMBER
- IS_MEMBER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database roles [SQL Server], members
- current member status
- roles [SQL Server], members
- testing member status
- members [SQL Server]
- checking member status
- IS_MEMBER function
- verifying member status
- groups [SQL Server], members
- members [SQL Server], verifying
ms.assetid: 77cb68a0-19b7-4fe1-ab17-e5587699631b
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 472d8f1cc258fdc57ef454fbb35f51e3f83b288d
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="ismember-transact-sql"></a>IS_MEMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Indique si l'utilisateur actuel est membre du groupe [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ou du rôle de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifié.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IS_MEMBER ( { 'group' | 'role' } )  
```  
  
## <a name="arguments"></a>Arguments  
 **'** *groupe* **'**  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Est le nom du groupe Windows qui est en cours de vérification ; doit être au format *domaine*\\*groupe*. *groupe* est **sysname**.  
  
 **'** *rôle* **'**  
 Nom de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rôle en cours de vérification. *rôle* est **sysname** et peuvent inclure la base de données fixé de rôles ou les rôles définis par l’utilisateur, mais pas les rôles de serveur.  
  
## <a name="return-types"></a>Types de retour  
 **int**  
  
## <a name="remarks"></a>Notes  
 IS_MEMBER retourne les valeurs suivantes.  
  
|Valeur retournée| Description|  
|------------------|-----------------|  
|0|L’utilisateur actuel n’est pas un membre de *groupe* ou *rôle*.|  
|1|L’utilisateur actuel est membre du *groupe* ou *rôle*.|  
|NULL|Soit *groupe* ou *rôle* n’est pas valide. En cas d'interrogation par une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou une connexion utilisant un rôle d'application, retourne NULL pour un groupe Windows.|  
  
 IS_MEMBER détermine l'appartenance au groupe Windows en examinant un jeton d'accès créé par Windows. Le jeton d'accès ne reflète pas les modifications apportées à l'appartenance au groupe après la connexion d'un utilisateur à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Appartenance au groupe Windows ne peut pas être interrogée par une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion ou un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rôle d’application.  
  
 Pour ajouter et supprimer des membres d’un rôle de base de données, utilisez [ALTER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-role-transact-sql.md). Pour ajouter et supprimer des membres d’un rôle de serveur, utilisez [ALTER SERVER ROLE &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
 Cette fonction évalue l'appartenance au rôle, et non l'autorisation sous-jacente. Par exemple, le **db_owner** a du rôle de base de données fixe le **base de données contrôle** autorisation. Si l’utilisateur a le **base de données de contrôle** autorisation mais n’est pas un membre du rôle, cette fonction signale correctement que l’utilisateur n’est pas un membre de la **db_owner** rôle, même si l’utilisateur dispose des mêmes autorisations.  
  
 Membres de la **sysadmin** rôle serveur fixe Entrez chaque base de données en tant que le **dbo** utilisateur. Vérification de l’autorisation pour le membre de la **sysadmin** rôle serveur fixe, vérifie les autorisations pour **dbo**, pas le compte de connexion d’origine. Étant donné que **dbo** ne peut pas être ajouté à un rôle de base de données et n’existe pas dans les groupes Windows, **dbo** retourne toujours 0 (ou NULL si le rôle n’existe pas).  
  
## <a name="related-functions"></a>Fonctions connexes  
 Pour déterminer si un autre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion est membre d’un rôle de base de données, utilisez [IS_ROLEMEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-rolemember-transact-sql.md). Pour déterminer si un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion est membre d’un rôle de serveur, utilisez [IS_SRVROLEMEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-srvrolemember-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant vérifie si l'utilisateur actuel est membre d'un rôle de base de données ou d'un groupe de domaines Windows.  
  
```  
-- Test membership in db_owner and print appropriate message.  
IF IS_MEMBER ('db_owner') = 1  
   PRINT 'Current user is a member of the db_owner role'  
ELSE IF IS_MEMBER ('db_owner') = 0  
   PRINT 'Current user is NOT a member of the db_owner role'  
ELSE IF IS_MEMBER ('db_owner') IS NULL  
   PRINT 'ERROR: Invalid group / role specified';  
GO  
  
-- Execute SELECT if user is a member of ADVWORKS\Shipping.  
IF IS_MEMBER ('ADVWORKS\Shipping') = 1  
   SELECT 'User ' + USER + ' is a member of ADVWORKS\Shipping.';   
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [IS_SRVROLEMEMBER &#40; Transact-SQL &#41;](../../t-sql/functions/is-srvrolemember-transact-sql.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Affichages catalogue de sécurité &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  


---
title: sp_helpsrvrole (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpsrvrole_TSQL
- sp_helpsrvrole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpsrvrole
ms.assetid: 5c7f39f3-c261-4f70-8beb-08242d4ac242
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 204668e8983ed3503e1a5697c47a4abde92d26cc
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750512"
---
# <a name="sp_helpsrvrole-transact-sql"></a>sp_helpsrvrole (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Retourne la liste des rôles serveur fixes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpsrvrole [ [ @srvrolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @srvrolename = ] 'role'`Nom du rôle serveur fixe. *role* est de **type sysname**, avec NULL comme valeur par défaut. le *rôle* peut prendre l’une des valeurs suivantes.  
  
|Rôle serveur fixe|Description|  
|-----------------------|-----------------|  
|administrateur système|Administrateurs système|  
|securityadmin|Administrateurs de la sécurité|  
|serveradmin|Administrateurs du serveur|  
|setupadmin|Administrateurs de l'installation et de la configuration|  
|processadmin|Administrateurs de processus|  
|diskadmin|Administrateurs de disques|  
|dbcreator|Créateurs de bases de données|  
|bulkadmin|Exécute les instructions BULK INSERT.|  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|ServerRole|**sysname**|Nom du rôle de serveur|  
|Description|**sysname**|Description de ServerRole|  
  
## <a name="remarks"></a>Remarques  
 Les rôles serveur fixes sont définis au niveau du serveur et possèdent les autorisations d'effectuer des opérations administratives spécifiques au niveau du serveur. Il est impossible d'ajouter, de supprimer ou de modifier des rôles serveur fixes.  
  
 Pour ajouter ou supprimer des membres dans des rôles de serveur, consultez [ALTER Server role &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
 Toutes les connexions sont membres du public. sp_helpsrvrole ne reconnaît pas le rôle public car, en interne, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’implémente pas public en tant que rôle.  
  
 sp_helpsrvrole ne prend pas un rôle de serveur défini par l’utilisateur comme argument. Pour répertorier les rôles de serveur définis par l’utilisateur, consultez les exemples dans [ALTER Server role &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle public.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-listing-the-fixed-server-roles"></a>R. Liste des rôles serveur fixes  
 La requête suivante retourne la liste des rôles serveur fixes.  
  
```  
EXEC sp_helpsrvrole ;  
```  
  
### <a name="b-listing-fixed-and-user-defined-server-roles"></a>B. Liste des rôles de serveur définis par l'utilisateur et fixes  
 La requête suivante retourne une liste de rôles serveur fixes et définis par l'utilisateur.  
  
```  
SELECT * FROM sys.server_principals WHERE type = 'R' ;  
```  
  
### <a name="c-returning-a-description-of-a-fixed-server-role"></a>C. Retour d'une description d'un rôle serveur fixe  
 La requête suivante retourne le nom et la description des rôles serveur fixes `diskadmin`.  
  
```  
sp_helpsrvrole 'diskadmin' ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de sécurité &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [Rôles au niveau du serveur](../../relational-databases/security/authentication-access/server-level-roles.md)   
 [sp_addsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsrvrolemember-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

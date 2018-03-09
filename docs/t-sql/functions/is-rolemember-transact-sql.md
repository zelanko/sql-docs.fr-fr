---
title: IS_ROLEMEMBER (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IS_ROLEMEMBER
- IS_ROLEMEMBER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- roles [SQL Server], members
- IS_ROLEMEMBER function
- members [SQL Server], verifying
ms.assetid: 73efa688-ae91-4014-98bc-1cabe47321f7
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: fd8574c27bea00127096dc1f0040c8c3f93e96cb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isrolemember-transact-sql"></a>IS_ROLEMEMBER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  Indique si un principal de base de données spécifié est membre du rôle de base de données spécifié.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
IS_ROLEMEMBER ( 'role' [ , 'database_principal' ] )  
```  
  
## <a name="arguments"></a>Arguments  
 **'** *rôle* **'**  
 Nom du rôle de base de données vérifié. *rôle* est **sysname**.  
  
 **'** *principal_base_de_données* **'**  
 Nom de l'utilisateur de base de données, du rôle de base de données ou du rôle d'application à vérifier. *principal_base_de_données* est **sysname**, avec NULL comme valeur par défaut. Si aucune valeur n'est spécifiée, le résultat est basé sur le contexte d'exécution actuel. Si le paramètre contient le mot NULL, retourne NULL.  
  
## <a name="return-types"></a>Types de retour  
 **int**  
  
|Valeur retournée| Description|  
|------------------|-----------------|  
|0|*principal_base_de_données* n’est pas un membre de *rôle*.|  
|1|*principal_base_de_données* est un membre de *rôle*.|  
|NULL|*principal_base_de_données* ou *rôle* n’est pas valide, ou vous n’êtes pas autorisé à consulter l’appartenance au rôle.|  
  
## <a name="remarks"></a>Notes  
 Utilisez IS_ROLEMEMBER pour déterminer si l'utilisateur actuel peut réaliser une action nécessitant les autorisations du rôle de base de données.  
  
 Si *principal_base_de_données* est basée sur une connexion Windows, telle que Contoso\Mary5, IS_ROLEMEMBER retourne NULL, sauf si le *principal_base_de_données* a été accordé ou refusé l’accès direct aux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Si le paramètre facultatif *principal_base_de_données* paramètre n’est pas fourni et si le *principal_base_de_données* est basée sur une connexion de domaine Windows, il peut être un membre d’un rôle de base de données via l’appartenance à un groupe Windows. Pour résoudre de telles appartenances indirectes, IS_ROLEMEMBER demande des informations sur l'appartenance au groupe Windows à partir du contrôleur du domaine. Si le contrôleur du domaine est inaccessible ou ne répond pas, IS_ROLEMEMBER retourne des informations sur l'appartenance au rôle, en prenant uniquement en considération l'utilisateur et ses groupes locaux. Si l'utilisateur spécifié n'est pas l'utilisateur actuel, la valeur retournée par IS_ROLEMEMBER peut différer de la dernière mise à jour de données de l'authentificateur (par exemple Active Directory) sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Si le paramètre facultatif *principal_base_de_données* paramètre est fourni, le principal de base de données qui est interrogé doit être présent dans sys.database_principals ou IS_ROLEMEMBER retourne NULL. Cela indique que le *principal_base_de_données* n’est pas valide dans cette base de données.  
  
 Lorsque le *principal_base_de_données* paramètre est basé sur une connexion à un domaine ou basé sur un groupe Windows et le contrôleur de domaine n’est pas accessible, les appels à IS_ROLEMEMBER échouent et peuvent retourner des données incorrectes ou incomplètes.  
  
 Si le contrôleur de domaine n'est pas accessible, l'appel à IS_ROLEMEMBER retourne des informations exactes lorsque le principal Windows peut être authentifié localement, par exemple un compte Windows local ou un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **IS_ROLEMEMBER** retourne toujours 0 lorsqu’un groupe Windows est utilisée comme argument de base de données principal, et ce groupe Windows est un membre d’un autre groupe Windows qui, à son tour, un membre du rôle de base de données spécifiée.  
  
 Le contrôle de compte d’utilisateur (UAC) trouvé dans [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] et Windows Server 2008 peut également retourner des résultats différents. Cela varie selon que l'utilisateur a accédé au serveur en tant que membre de groupe Windows ou en tant qu'utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] spécifique.  
  
 Cette fonction évalue l'appartenance au rôle, et non l'autorisation sous-jacente. Par exemple, le **db_owner** a du rôle de base de données fixe le **base de données contrôle** autorisation. Si l’utilisateur a le **base de données de contrôle** autorisation mais n’est pas un membre du rôle, cette fonction signale correctement que l’utilisateur n’est pas un membre de la **db_owner** rôle, même si l’utilisateur dispose des mêmes autorisations.  
  
## <a name="related-functions"></a>Fonctions connexes  
 Pour déterminer si l’utilisateur actuel est membre du groupe Windows spécifié ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rôle de base de données, utilisez [IS_MEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-member-transact-sql.md). Pour déterminer si un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion est membre d’un rôle de serveur, utilisez [IS_SRVROLEMEMBER &#40; Transact-SQL &#41; ](../../t-sql/functions/is-srvrolemember-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation VIEW DEFINITION sur le rôle de base de données.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant indique si l'utilisateur actuel est membre du rôle de base de données fixe `db_datareader`.  
  
```  
IF IS_ROLEMEMBER ('db_datareader') = 1  
   print 'Current user is a member of the db_datareader role'  
ELSE IF IS_ROLEMEMBER ('db_datareader') = 0  
   print 'Current user is NOT a member of the db_datareader role'  
ELSE IF IS_ROLEMEMBER ('db_datareader') IS NULL  
   print 'ERROR: The database role specified is not valid.';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER un rôle &#40; Transact-SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [ALTER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-role-transact-sql.md)   
 [DROP ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-role-transact-sql.md)   
 [CRÉER le rôle de serveur &#40; Transact-SQL &#41;](../../t-sql/statements/create-server-role-transact-sql.md)   
 [ALTER SERVER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-server-role-transact-sql.md)   
 [DROP SERVER ROLE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-server-role-transact-sql.md)   
 [IS_MEMBER &#40; Transact-SQL &#41;](../../t-sql/functions/is-member-transact-sql.md)   
 [IS_SRVROLEMEMBER &#40; Transact-SQL &#41;](../../t-sql/functions/is-srvrolemember-transact-sql.md)   
 [Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)  
  
  

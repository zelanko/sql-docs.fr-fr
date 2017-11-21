---
title: MODIFIER les liaisons de SERVICE distant (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER REMOTE SERVICE BINDING
- ALTER_REMOTE_SERVICE_BINDING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- remote service bindings [Service Broker], modifying
- ALTER REMOTE SERVICE BINDING statement
- modifying remote service bindings
ms.assetid: ee620b4a-9375-4eaa-a016-69916c9e1e68
caps.latest.revision: 37
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5352750b43775b53a508b42de17d33a792a40b1b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-remote-service-binding-transact-sql"></a>ALTER REMOTE SERVICE BINDING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie l'utilisateur associé à des liaisons de service distant ou modifie le paramètre d'authentification anonyme pour ces liaisons.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER REMOTE SERVICE BINDING binding_name   
   WITH [ USER = <user_name> ] [ , ANONYMOUS = { ON | OFF } ]   
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *binding_name*  
 Nom des liaisons de service distant à modifier. Les noms du serveur, de la base de données et du schéma ne peuvent pas être spécifiés.  
  
 AVEC utilisateur = \< *nom_utilisateur >*  
 Spécifie l'utilisateur de base de données qui détient le certificat associé au service distant pour ces liaisons. La clé publique de ce certificat est utilisée pour le chiffrement et l'authentification des messages échangés avec le service distant.  
  
 ANONYMOUS  
 Spécifie si l'authentification anonyme est utilisée lors des communications avec le service distant. Si ANONYMOUS = ON, l'authentification anonyme est utilisée et les informations d'identification de l'utilisateur local ne sont pas transférées au service distant. Si ANONYMOUS = OFF (désactivé), les informations d'identification de l'utilisateur sont transférées. Lorsque cette clause est omise, la valeur par défaut est OFF.  
  
## <a name="remarks"></a>Notes  
 La clé publique dans le certificat associé *nom_utilisateur* est utilisé pour authentifier les messages envoyés au service distant et pour chiffrer une clé de session qui est ensuite utilisée pour chiffrer la conversation. Le certificat pour *nom_utilisateur* doit correspondre au certificat d’une connexion dans la base de données qui héberge le service distant.  
  
## <a name="permissions"></a>Permissions  
 L’autorisation de modification d’une liaison de service distant par défaut au propriétaire de la liaison, les membres du service distant le **db_owner** fixe du rôle de base de données et les membres de la **sysadmin** rôle serveur fixe.  
  
 L'utilisateur qui exécute l'instruction ALTER REMOTE SERVICE BINDING doit disposer de l'autorisation d'emprunt d'identité pour l'utilisateur spécifié dans l'instruction.  
  
 Si vous voulez modifier l'option AUTHORIZATION pour des liaisons de service distant, utilisez l'instruction ALTER AUTHORIZATION.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant modifie les liaisons de service distant `APBinding` de façon à chiffrer les messages à l'aide des certificats du compte `SecurityAccount`.  
  
```  
ALTER REMOTE SERVICE BINDING APBinding  
    WITH USER = SecurityAccount ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE REMOTE SERVICE BINDING &#40;Transact-SQL&#41;](../../t-sql/statements/create-remote-service-binding-transact-sql.md)   
 [SUPPRIMER les liaisons de SERVICE distant &#40; Transact-SQL &#41;](../../t-sql/statements/drop-remote-service-binding-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  


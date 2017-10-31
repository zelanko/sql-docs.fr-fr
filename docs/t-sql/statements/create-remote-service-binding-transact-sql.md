---
title: "CRÉER des liaisons de SERVICE distant (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE REMOTE SERVICE BINDING
- SERVICE_BINDING_TSQL
- CREATE REMOTE SERVICE
- REMOTE_TSQL
- CREATE_REMOTE_SERVICE_BINDING_TSQL
- CREATE_REMOTE_SERVICE_TSQL
- BINDING
- SERVICE BINDING
- BINDING_TSQL
- CREATE_REMOTE_TSQL
- REMOTE_SERVICE_TSQL
- CREATE REMOTE
- REMOTE SERVICE
- REMOTE_SERVICE_BINDING_TSQL
- REMOTE
- REMOTE SERVICE BINDING
dev_langs:
- TSQL
helpviewer_keywords:
- binding remote service [Service Broker]
- dialog security [Service Broker]
- end-to-end security [Service Broker]
- security [Service Broker], remote service bindings
- CREATE REMOTE SERVICE BINDING statement
- conversation security [Service Broker]
- remote service bindings [Service Broker], creating
ms.assetid: 4165c404-4d50-4063-9a6e-6e267d309376
caps.latest.revision: 46
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a4083cb617d76084719450a6abc49fd76345cc7a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-remote-service-binding-transact-sql"></a>CREATE REMOTE SERVICE BINDING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée une liaison qui définit les informations d'identification de sécurité à utiliser pour démarrer une conversation avec un service distant.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE REMOTE SERVICE BINDING binding_name   
   [ AUTHORIZATION owner_name ]   
   TO SERVICE 'service_name'   
   WITH  USER = user_name [ , ANONYMOUS = { ON | OFF } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *binding_name*  
 Nom de la liaison de service distant à créer. Les noms du serveur, de la base de données et du schéma ne peuvent pas être spécifiés. Le *binding_name* doit être un **sysname**.  
  
 AUTORISATION *owner_name*  
 Affecte au propriétaire de la liaison le rôle ou l'utilisateur de base de données spécifié. Lorsque l’utilisateur actuel est **dbo** ou **sa**, *owner_name* peut être le nom de n’importe quel utilisateur ou rôle valide. Dans le cas contraire, *owner_name* doit être le nom de l’utilisateur actuel, le nom d’un utilisateur qui l’utilisateur actuel possède des autorisations IMPERSONATE ou le nom d’un rôle auquel appartient l’utilisateur actuel.  
  
 POUR le SERVICE '*service_name*'  
 Spécifie le service distant à lier à l'utilisateur identifié dans la clause WITH USER.  
  
 UTILISATEUR = *nom_utilisateur*  
 Spécifie le principal de la base de données qui possède le certificat associé au service distant identifié par la clause TO SERVICE. Ce certificat est utilisé pour le chiffrement et l'authentification des messages échangés avec le service distant.  
  
 ANONYMOUS  
 Spécifie si l'authentification anonyme est utilisée lors des communications avec le service distant. Si ANONYMOUS = ON, l’authentification anonyme est utilisée et dans la base de données à distance se produisent en tant que membre de la **public** rôle de base de données fixe. Si ANONYMOUS = OFF, les opérations de la base de données distante sont exécutées en tant qu'utilisateur spécifique dans cette base de données. Lorsque cette clause est omise, la valeur par défaut est OFF.  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[ssSB](../../includes/sssb-md.md)] utilise une liaison de service distant afin de localiser le certificat à utiliser pour une nouvelle conversation. La clé publique dans le certificat associé *nom_utilisateur* est utilisé pour authentifier les messages envoyés au service distant et pour chiffrer une clé de session qui est ensuite utilisée pour chiffrer la conversation. Le certificat pour *nom_utilisateur* doit correspondre au certificat d’un utilisateur dans la base de données qui héberge le service distant.  
  
 Une liaison de service distant n'est nécessaire que pour démarrer des services qui communiquent avec des services cibles en dehors de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Une base de données qui héberge un service d'initialisation doit contenir des liaisons de service distant pour tous les services cibles en dehors de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Une base de données qui héberge un service cible n'a pas besoin de contenir des liaisons de service distant pour les services d'initialisation qui communiquent avec le service cible. Lorsque les services initiateur et cible sont dans la même instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], aucune liaison de service distant n'est nécessaire. Toutefois, si une liaison de service distant est présent où le *service_name* spécifié pour TO SERVICE correspond au nom du service local, [!INCLUDE[ssSB](../../includes/sssb-md.md)] utilisera la liaison.  
  
 Si ANONYMOUS = ON, le service initiateur se connecte au service cible en tant que membre de la **public** rôle de base de données fixe. Par défaut, les membres de ce rôle n'ont pas l'autorisation de se connecter à une base de données. Pour envoyer un message, la base de données cible doit accorder la **public** rôle autorisation CONNECT pour la base de données et l’autorisation SEND pour le service cible.  
  
 Lorsqu'un utilisateur possède plusieurs certificats actuellement valides et marqués comme étant AVAILABLE FOR BEGIN_DIALOG, [!INCLUDE[ssSB](../../includes/sssb-md.md)] sélectionne celui qui est doté de la date d'expiration la plus lointaine.  
  
## <a name="permissions"></a>Permissions  
 Autorisations pour la création d’un ordinateur de service de liaison par défaut à l’utilisateur nommé dans la clause USER, membres de la **db_owner** , les membres du rôle de base de données fixe le **db_ddladmin** fixe du rôle de base de données et les membres du **sysadmin** rôle serveur fixe.  
  
 L'utilisateur qui exécute l'instruction CREATE REMOTE SERVICE BINDING doit avoir l'autorisation d'emprunt d'identité pour le principal spécifié dans l'instruction.  
  
 Une liaison de service distant ne peut pas être un objet temporaire. Noms de liaison de service distant commençant par  **#**  sont autorisées, mais sont des objets permanents.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-remote-service-binding"></a>A. Création d’une liaison de service distant  
 L'exemple suivant crée une liaison pour le service `//Adventure-Works.com/services/AccountsPayable`. [!INCLUDE[ssSB](../../includes/sssb-md.md)] utilise le certificat appartenant au principal de base de données `APUser` pour s'authentifier auprès du service distant et échanger la clé de chiffrement de la session avec le service distant.  
  
```  
CREATE REMOTE SERVICE BINDING APBinding  
    TO SERVICE '//Adventure-Works.com/services/AccountsPayable'  
    WITH USER = APUser ;  
```  
  
### <a name="b-creating-a-remote-service-binding-using-anonymous-authentication"></a>B. Création d'une liaison de service distant avec une authentification anonyme  
 L'exemple suivant crée une liaison pour le service `//Adventure-Works.com/services/AccountsPayable`. [!INCLUDE[ssSB](../../includes/sssb-md.md)] utilise le certificat appartenant au principal de base de données `APUser` pour échanger la clé de chiffrement de la session avec le service distant. Il ne s'authentifie pas auprès du service distant. Dans la base de données qui héberge le service distant, les messages sont remis en tant que le **invité** utilisateur.  
  
```  
CREATE REMOTE SERVICE BINDING APBinding  
    TO SERVICE '//Adventure-Works.com/services/AccountsPayable'  
    WITH USER = APUser, ANONYMOUS=ON ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [MODIFIER les liaisons de SERVICE distant &#40; Transact-SQL &#41;](../../t-sql/statements/alter-remote-service-binding-transact-sql.md)   
 [SUPPRIMER les liaisons de SERVICE distant &#40; Transact-SQL &#41;](../../t-sql/statements/drop-remote-service-binding-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  


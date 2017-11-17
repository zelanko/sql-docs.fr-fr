---
title: "Autorisations d’accorder au Service Broker (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 06/10/2016
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
dev_langs:
- TSQL
helpviewer_keywords:
- granting permissions [SQL Server], Service Broker
- routes [Service Broker], permissions
- Service Broker, permissions
- GRANT statement, Service Broker
- remote service bindings [Service Broker], permissions
- message types [Service Broker], permissions
- contracts [Service Broker], permissions
ms.assetid: c5579976-97c4-4123-be0c-d0b98a9e38fb
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 185950b1872ca5f11663f3d5051d1a2303cce090
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="grant-service-broker-permissions-transact-sql"></a>GRANT - Autorisations sur Service Broker (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Accorde des autorisations à un contrat Service Broker, un type de message, une liaison distante, un itinéraire ou un service.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GRANT permission  [ ,...n ] ON  
    {    
              [ CONTRACT :: contract_name ]   
       | [ MESSAGE TYPE :: message_type_name ]    
       | [ REMOTE SERVICE BINDING :: remote_binding_name ]    
       | [ ROUTE :: route_name ]   
       | [ SERVICE :: service_name ]      
    }  
    TO database_principal [ ,...n ]   
    [ WITH GRANT OPTION ]  
        [ AS granting_principal ]  
```  
  
## <a name="arguments"></a>Arguments  
 *autorisation*  
 Spécifie une autorisation qu'il est possible d'accorder sur un élément sécurisable Service Broker.  Voir ci-dessous.  
  
 CONTRAT **::***nom_contract*  
 Indique le contrat sur lequel l'autorisation est accordée. Le qualificateur d’étendue « :: » est requis.  
  
 TYPE DE MESSAGE **::***message_type_name*  
 Spécifie le type de message sur lequel l'autorisation est accordée. Le qualificateur d'étendue "::" est indispensable.  
  
 REMOTE SERVICE BINDING **::***remote_binding_name*  
 Spécifie la liaison de service distant sur laquelle l'autorisation est accordée. Le qualificateur d'étendue "::" est indispensable.  
  
 ITINÉRAIRE **::***route_name*  
 Indique l'itinéraire sur lequel l'autorisation est accordée. Le qualificateur d'étendue "::" est indispensable.  
  
 SERVICE **::***service_name*  
 Indique le service sur lequel l'autorisation est accordée. Le qualificateur d'étendue "::" est indispensable.  
  
 *principal_base_de_données*  
 Spécifie le principal auquel l'autorisation est accordée. Il peut s'agir :  
  
-   d'un utilisateur de base de données ;  
  
-   d'un rôle de base de données ;  
  
-   d'un rôle d'application ;  
  
-   d'un utilisateur de base de données mappé sur une connexion Windows ;  
  
-   d'un utilisateur de base de données mappé sur un groupe Windows ;  
  
-   d'un utilisateur de base de données mappé sur un certificat ;  
  
-   d'un utilisateur de base de données mappé à une clé asymétrique ;  
  
-   d'un utilisateur de base de données qui n'est pas mappé sur le principal d'un serveur.  
  
 GRANT OPTION  
 Indique que le principal a également la possibilité d'accorder l'autorisation spécifiée à d'autres principaux.  
  
 *granting_principal*  
 Spécifie un principal dont le principal qui exécute cette requête dérive son droit d'accorder l'autorisation. Il peut s'agir :  
  
-   d'un utilisateur de base de données ;  
  
-   d'un rôle de base de données ;  
  
-   d'un rôle d'application ;  
  
-   d'un utilisateur de base de données mappé sur une connexion Windows ;  
  
-   d'un utilisateur de base de données mappé sur un groupe Windows ;  
  
-   d'un utilisateur de base de données mappé sur un certificat ;  
  
-   d'un utilisateur de base de données mappé à une clé asymétrique ;  
  
-   d'un utilisateur de base de données qui n'est pas mappé sur le principal d'un serveur.  
  
## <a name="remarks"></a>Notes  
  
## <a name="service-broker-contracts"></a>Contrats Service Broker  
 Un contrat Service Broker est un élément sécurisable au niveau base de données contenu dans la base de données parente dans la hiérarchie des autorisations. Les autorisations les plus particulières et les plus limitées qu'il est possible d'accorder sur un contrat Service Broker sont mentionnées ci-dessous, ainsi que les autorisations plus générales qui les englobent implicitement.  
  
|Autorisation d'un contrat Service Broker|Impliquée par une autorisation d'un contrat Service Broker|Impliquée par une autorisation de base de données|  
|----------------------------------------|---------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY CONTRACT|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-message-types"></a>Types de messages Service Broker  
 Un type de message Service Broker est un élément sécurisable au niveau base de données contenu dans la base de données parente dans la hiérarchie des autorisations. Les autorisations les plus particulières et les plus limitées qu'il est possible d'accorder sur un type de message Service Broker sont mentionnées ci-dessous, ainsi que les autorisations plus générales qui les englobent implicitement.  
  
|Autorisation d'un type de message Service Broker|Impliquée par une autorisation d'un type de message Service Broker|Impliquée par une autorisation de base de données|  
|--------------------------------------------|-------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY MESSAGE TYPE|  
|REFERENCES|CONTROL|REFERENCES|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-remote-service-bindings"></a>Liaisons de service distant Service Broker  
 Une liaison de service distant Service Broker est un élément sécurisable au niveau base de données contenu dans la base de données parente dans la hiérarchie des autorisations. Les autorisations les plus particulières et les plus limitées qu'il est possible d'accorder sur une liaison de service distant Service Broker sont mentionnées ci-dessous, ainsi que les autorisations plus générales qui les englobent implicitement.  
  
|Autorisation de liaison de service distant Service Broker|Impliquée par une autorisation de liaison de service distant Service Broker|Impliquée par une autorisation de base de données|  
|------------------------------------------------------|-----------------------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY REMOTE SERVICE BINDING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="service-broker-routes"></a>Itinéraires Service Broker  
 Un itinéraire Service Broker est un élément sécurisable au niveau base de données contenu dans la base de données parente dans la hiérarchie des autorisations. Les autorisations les plus particulières et les plus limitées qu'il est possible d'accorder sur un itinéraire Service Broker sont mentionnées ci-dessous, ainsi que les autorisations plus générales qui les englobent implicitement.  
  
|Autorisation d'un itinéraire Service Broker|Impliquée par une autorisation d'un itinéraire Service Broker|Impliquée par une autorisation de base de données|  
|-------------------------------------|------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROUTE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
### <a name="service-broker-services"></a>Services Service Broker  
 Un service Service Broker est un élément sécurisable au niveau base de données contenu dans la base de données parente dans la hiérarchie des autorisations. Les autorisations les plus particulières et les plus limitées qu'il est possible d'accorder à un service Service Broker sont mentionnées ci-dessous, ainsi que les autorisations plus générales qui les englobent implicitement.  
  
|Autorisation d'un service Service Broker|Impliquée par une autorisation d'un service Service Broker|Impliquée par une autorisation de base de données|  
|---------------------------------------|--------------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|SEND|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY SERVICE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 Le fournisseur d'autorisations (ou le principal spécifié avec l'option AS) doit posséder l'autorisation elle-même avec l'option GRANT OPTION ou une autorisation plus élevée qui implique l'autorisation accordée.  
  
 En cas d'utilisation de l'option AS, ces critères s'appliquent.  
  
|En tant que *granting_principal*|Autres autorisations nécessaires|  
|------------------------------|------------------------------------|  
|Utilisateur de base de données|L’autorisation IMPERSONATE sur l’utilisateur, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données mappé à une connexion Windows|L’autorisation IMPERSONATE sur l’utilisateur, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données mappé à un groupe Windows|L’appartenance au groupe Windows, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données mappé à un certificat|L’appartenance au **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance à la **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données mappé à une clé asymétrique|L’appartenance au **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance à la **sysadmin** rôle serveur fixe.|  
|Utilisateur de base de données qui n'est mappé sur aucun principal d'un serveur|L’autorisation IMPERSONATE sur l’utilisateur, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Rôle de base de données|L’autorisation ALTER sur le rôle, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
|Rôle d'application|L’autorisation ALTER sur le rôle, l’appartenance à la **db_securityadmin** des rôles de base de données fixe le **db_owner** fixe, un rôle de base de données ou l’appartenance au **sysadmin** rôle serveur fixe.|  
  
 Les propriétaires d'objets peuvent accorder des autorisations sur les objets qu'ils possèdent. Les principaux ayant l'autorisation CONTROL sur un élément sécurisable peuvent accorder une autorisation sur cet élément.  
  
 Les détenteurs de l’autorisation CONTROL SERVER, tels que les membres de la **sysadmin** rôle serveur fixe, peuvent accorder une autorisation sur n’importe quel élément sécurisable du serveur. Les détenteurs de l’autorisation CONTROL sur une base de données, tels que les membres de la **db_owner** rôle de base de données fixe, peuvent accorder une autorisation sur n’importe quel élément sécurisable dans la base de données. Les détenteurs de l'autorisation CONTROL sur un schéma peuvent accorder une autorisation sur n'importe quel objet dans ce schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [Autorisations &#40;moteur de base de données&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


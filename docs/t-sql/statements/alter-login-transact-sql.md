---
title: ALTER LOGIN (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_LOGIN_TSQL
- ALTER LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER LOGIN statement
- change password
- mapping logins [SQL Server]
- logins [SQL Server], modifying
- passwords [SQL Server], modifying
- names [SQL Server], logins
- modifying login accounts
ms.assetid: e247b84e-c99e-4af8-8b50-57586e1cb1c5
caps.latest.revision: 68
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9dd47cb63c56dbbfb5f31ea3f7b2c8d4f45e9d73
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-login-transact-sql"></a>ALTER LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Modifie les propriétés d'un compte de connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-- Syntax for SQL Server  
  
ALTER LOGIN login_name   
    {   
    <status_option>   
    | WITH <set_option> [ ,... ]  
    | <cryptographic_credential_option>  
    }   
[;]  
  
<status_option> ::=  
        ENABLE | DISABLE  
  
<set_option> ::=              
    PASSWORD = 'password' | hashed_password HASHED  
    [   
      OLD_PASSWORD = 'oldpassword'  
      | <password_option> [<password_option> ]   
    ]  
    | DEFAULT_DATABASE = database  
    | DEFAULT_LANGUAGE = language  
    | NAME = login_name  
    | CHECK_POLICY = { ON | OFF }  
    | CHECK_EXPIRATION = { ON | OFF }  
    | CREDENTIAL = credential_name  
    | NO CREDENTIAL  
  
<password_option> ::=   
    MUST_CHANGE | UNLOCK  
  
<cryptographic_credentials_option> ::=   
    ADD CREDENTIAL credential_name  
  | DROP CREDENTIAL credential_name  
```  
  
```  
-- Syntax for Azure SQL Database  
  
ALTER LOGIN login_name   
  {   
      <status_option>   
    | WITH <set_option> [ ,.. .n ]   
  }   
[;]  
  
<status_option> ::=  
    ENABLE | DISABLE  
  
<set_option> ::=   
    PASSWORD ='password'   
    [  
      OLD_PASSWORD ='oldpassword'  
    ]   
    | NAME = login_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER LOGIN login_name   
    {   
    <status_option>   
    | WITH <set_option> [ ,... ]  
    }   
  
<status_option> ::=ENABLE | DISABLE  
  
<set_option> ::=              
    PASSWORD ='password'   
    [   
      OLD_PASSWORD ='oldpassword'  
      | <password_option> [<password_option> ]   
    ]  
    | NAME = login_name  
    | CHECK_POLICY = { ON | OFF }  
    | CHECK_EXPIRATION = { ON | OFF }   
      
<password_option> ::=   
    MUST_CHANGE | UNLOCK  
```  
  
## <a name="arguments"></a>Arguments  
 *login_name*  
 Spécifie le nom de la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cours de modification. Les connexions de domaine doivent être placées entre crochets au format [domaine\utilisateur].  
  
 ENABLE | DISABLE  
 Active ou désactive cette connexion. La désactivation d'une connexion n'a aucune incidence sur le comportement des connexions qui sont déjà en cours. (Utilisez la `KILL` instruction pour mettre fin à des connexions existantes.) Les connexions désactivées conservent leurs autorisations et peuvent toujours être usurpées.  
  
 Mot de passe **='***mot de passe***'**  
 S'applique uniquement aux connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Spécifie le mot de passe de la connexion en cours de modification. Les mots de passe respectent la casse.  
  
 En continu des connexions actives à la base de données SQL requièrent une nouvelle autorisation (opération effectuée par le moteur de base de données) au moins toutes les 10 heures. Le moteur de base de données tente de renouvellement d’autorisation à l’aide du mot de passe envoyé à l’origine et aucune entrée utilisateur n’est requise. Pour des raisons de performances, lorsqu’un mot de passe est réinitialisé dans la base de données SQL, la connexion ne sera pas s’authentifier à nouveau, même si la connexion est réinitialisée suite à un regroupement de connexion. Cela est différent du comportement de local SQL Server. Si le mot de passe a été modifié, car la connexion a été initialement autorisée, la connexion doit se terminer et établir une nouvelle connexion à l’aide du nouveau mot de passe. Un utilisateur avec l’autorisation de supprimer la connexion de base de données peut terminer explicitement une connexion à la base de données SQL à l’aide de la commande KILL. Pour plus d’informations, consultez [KILL &#40; Transact-SQL &#41; ](../../t-sql/language-elements/kill-transact-sql.md).  
  
 Mot de passe  **=**  *hashed_password*  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 S'applique uniquement au mot clé HASHED. Spécifie la valeur hachée du mot de passe de la connexion créée.  
  
> [!IMPORTANT]  
>  Lorsqu'un compte de connexion (ou un utilisateur de base de données à relation contenant-contenu) se connecte et est authentifié, la connexion met en cache les informations d'identité sur la connexion. Dans le cas d'une connexion d'authentification Windows, ces informations incluent des données sur l'appartenance aux groupes Windows. L'identité de la connexion reste authentifiée tant que la connexion est conservée. Pour imposer des modifications d'identité, une réinitialisation du mot de passe, par exemple, ou la modification de l'appartenance au groupe Windows, le compte de connexion doit fermer une session de l'autorité d'authentification (Windows ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) et ouvrir une nouvelle session. Un membre du rôle serveur fixe **sysadmin** ou tout compte de connexion doté de l’autorisation **ALTER ANY CONNECTION** peut utiliser la commande **KILL** pour mettre fin à une connexion et obliger le compte de connexion à se reconnecter. [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] peut réutiliser les informations de connexion lors de l’ouverture de plusieurs connexions dans les fenêtres de l’Explorateur d’objets et de l’éditeur de requête. Fermez toutes les connexions pour imposer une reconnexion.  
  
 HASHED  
   
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 S’applique à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion uniquement. Spécifie que le mot de passe entré après l'argument PASSWORD est déjà haché. Si cette option n'est pas sélectionnée, le mot de passe est haché avant d'être stocké dans la base de données. Cette option doit être utilisée uniquement pour la synchronisation de connexion entre deux serveurs. N'utilisez pas l'option HASHED pour modifier des mots de passe de manière régulière.  
  
 OLD_PASSWORD **='***oldpassword***'**  
 S'applique uniquement aux connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Mot de passe actuel de la connexion à laquelle un nouveau mot de passe doit être attribué. Les mots de passe respectent la casse.  
  
 MUST_CHANGE  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 S'applique uniquement aux connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous incluez cette option, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] demande un mot de passe actualisé lors de la première utilisation de la connexion modifiée.  
  
 DEFAULT_DATABASE  **=**  *base de données*  
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie une base de données par défaut à affecter à la connexion.  
  
 DEFAULT_LANGUAGE  **=**  *language*  
 
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Spécifie une langue par défaut à affecter à la connexion. La langue par défaut pour toutes les connexions de base de données SQL est l’anglais et ne peut pas être modifiée. La langue par défaut de la `sa` connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur Linux, est l’anglais, mais il peut être modifié.  
  
 NOM = *login_name*  
 Nouveau nom de la connexion à renommer. S'il s'agit d'une connexion Windows, le SID du principal Windows correspondant au nouveau nom doit correspondre au SID de la connexion dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le nouveau nom d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion ne peut pas contenir une barre oblique inverse (\\).  
  
 CHECK_EXPIRATION = {ON | **OFF** }  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 S'applique uniquement aux connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Spécifie si les règles d'expiration des mots de passe doivent être imposées sur cette connexion. La valeur par défaut est OFF.  
  
 CHECK_POLICY  **=**  { **ON** | {OFF}  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 S'applique uniquement aux connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Spécifie que les stratégies de mot de passe Windows de l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] s'exécute doivent être imposées sur cette connexion. La valeur par défaut est ON.  
  
 Informations d’identification = *credential_name*  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Nom des informations d'identification à mapper sur une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les informations d'identification doivent déjà exister sur le serveur. Pour plus d’informations, consultez [informations d’identification &#40; moteur de base de données &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md). Informations d’identification ne peut pas être mappée à la connexion sa.  
  
 NO CREDENTIAL  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Supprime tout mappage existant de la connexion sur des informations d'identification du serveur. Pour plus d’informations, consultez [informations d’identification &#40; moteur de base de données &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md).  
  
 UNLOCK  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 S'applique uniquement aux connexions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Spécifie qu'une connexion verrouillée doit être déverrouillée.  
  
 ADD CREDENTIAL  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Ajoute des informations d'identification du fournisseur EKM (Extensible Key Management) à la connexion. Pour plus d’informations, consultez [gestion de clés Extensible &#40; Gestion de clés extensible &#41; ](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
 DROP CREDENTIAL  
 **S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
Supprime une information d’identification du fournisseur de gestion de clés Extensible (EKM) de la connexion. Pour plus d’informations, consultez [gestion de clés Extensible &#40; Gestion de clés extensible &#41; ](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>Notes  
 Lorsque CHECK_POLICY a la valeur ON, l'argument HASHED ne peut pas être utilisé.  
  
 Lorsque CHECK_POLICY prend la valeur ON, le comportement suivant a lieu :  
  
-   L'historique du mot de passe est initialisé avec la valeur du hachage de mot de passe actuel.  
  
 Lorsque CHECK_POLICY prend la valeur OFF, le comportement suivant a lieu :  
  
-   CHECK_EXPIRATION ON prend également la valeur OFF.  
  
-   L'historique du mot de passe est supprimé.  
  
-   La valeur de *lockout_time* est réinitialisé.  
  
Si MUST_CHANGE est spécifié, CHECK_EXPIRATION et CHECK_POLICY doivent prendre la valeur ON. Sans quoi, l'instruction échoue.  
  
Si CHECK_POLICY prend la valeur OFF, CHECK_EXPIRATION ne peut pas prendre la valeur ON. Si cette combinaison d'options est utilisée dans une instruction ALTER LOGIN, l'instruction échoue.  
  
Vous ne pouvez pas utiliser ALTER_LOGIN avec l'argument DISABLE pour refuser l'accès à un groupe Windows. Par exemple, ALTER_LOGIN [*domaine\groupe*] DISABLE retournera le message d’erreur suivant :  
  
 « Msg 15151, Niveau 16, État 1, Ligne 1 »  
  
 « Impossible de trouver la connexion '*domaine\groupe*', car il n’existe pas ou vous n’êtes pas autorisé. »  
  
 C'est la procédure normale.  
  
Dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)], les données de connexion requises pour authentifier une connexion et les règles de pare-feu de niveau serveur sont temporairement mis en cache dans chaque base de données. Ce cache est actualisé régulièrement. Pour forcer une actualisation du cache d’authentification et assurez-vous qu’une base de données a la version la plus récente de la table de connexions, exécutez [DBCC FLUSHAUTHCACHE &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation ALTER ANY LOGIN.  
  
 Si l'option CREDENTIAL est utilisée, exige également l'autorisation ALTER ANY CREDENTIAL.  
  
 Si la connexion est en cours de modification est un membre de la **sysadmin** rôle serveur fixe ou détient l’autorisation CONTROL SERVER, également l’autorisation CONTROL SERVER lorsque les modifications suivantes :  
  
-   réinitialisation du mot de passe sans fournir l'ancien mot de passe ;  
  
-   activation de MUST_CHANGE, CHECK_POLICY ou CHECK_EXPIRATION ;  
  
-   modification du nom de la connexion ;  
  
-   activation ou désactivation de la connexion ;  
  
-   mappage de la connexion sur une autre information d'identification.  
  
 Un principal peut modifier le mot de passe, la langue et la base de données par défaut de sa propre connexion.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-enabling-a-disabled-login"></a>A. Activation d'une connexion désactivée  
 L'exemple suivant active la connexion `Mary5`.  
  
```tsql  
ALTER LOGIN Mary5 ENABLE;  
```  
  
### <a name="b-changing-the-password-of-a-login"></a>B. Modification du mot de passe d'une connexion  
 L'exemple suivant remplace le mot de passe de la connexion `Mary5` par un mot de passe fort.  
  
```tsql  
ALTER LOGIN Mary5 WITH PASSWORD = '<enterStrongPasswordHere>';  
```  
  
### <a name="c-changing-the-name-of-a-login"></a>C. Modification du nom d'une connexion  
 L'exemple suivant remplace le nom de connexion `Mary5` par `John2`.  
  
```tsql  
ALTER LOGIN Mary5 WITH NAME = John2;  
```  
  
### <a name="d-mapping-a-login-to-a-credential"></a>D. Mappage d'une connexion sur des informations d'identification  
 L'exemple suivant mappe la connexion `John2` aux informations d'identification `Custodian04`.  
  
```tsql  
ALTER LOGIN John2 WITH CREDENTIAL = Custodian04;  
```  
  
### <a name="e-mapping-a-login-to-an-extensible-key-management-credential"></a>E. Mappage d'une connexion à des informations d'identification de gestion de clés extensible  
 L'exemple suivant mappe la connexion `Mary5` aux informations d'identification EKM `EKMProvider1`.  
  
 
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```tsql  
ALTER LOGIN Mary5  
ADD CREDENTIAL EKMProvider1;  
GO  
```  
  
### <a name="f-unlocking-a-login"></a>F. Déverrouillage d'une connexion  
 Pour déverrouiller une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], exécutez l'instruction suivante, en remplaçant * * * * par le mot de passe de compte souhaité.  
  
  
```tsql  
ALTER LOGIN [Mary5] WITH PASSWORD = '****' UNLOCK ;  

GO  
```  
  
 Pour déverrouiller une connexion sans modifier le mot de passe, désactivez la stratégie de contrôle, puis réactivez-la.  
  
```tsql  
ALTER LOGIN [Mary5] WITH CHECK_POLICY = OFF;  
ALTER LOGIN [Mary5] WITH CHECK_POLICY = ON;  
GO  
```  
  
### <a name="g-changing-the-password-of-a-login-using-hashed"></a>G. Modification du mot de passe d'une connexion à l'aide de HASHED  
 L'exemple suivant modifie le mot de passe de la connexion `TestUser` en une valeur déjà hachée.  
  
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
```tsql  
ALTER LOGIN TestUser WITH   
PASSWORD = 0x01000CF35567C60BFB41EBDE4CF700A985A13D773D6B45B90900 HASHED ;  
GO  
```  
  
 
  
## <a name="see-also"></a>Voir aussi  
 [Informations d’identification &#40; moteur de base de données &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [DROP LOGIN &#40; Transact-SQL &#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [Gestion de clés extensible &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  




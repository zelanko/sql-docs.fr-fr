---
title: CREATE LOGIN (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CREATE_LOGIN_TSQL
- CREATE LOGIN
- LOGIN_TSQL
- LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- passwords [SQL Server], logins
- mapping logins [SQL Server]
- logins [SQL Server], creating
- CREATE LOGIN statement
- permissions [SQL Server], logins
- Windows domain accounts [SQL Server]
- re-hashing passwords
- certificates [SQL Server], logins
ms.assetid: eb737149-7c92-4552-946b-91085d8b1b01
caps.latest.revision: 101
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2b8859b2cc7aed93f941756400caa387061034b6
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/04/2018
ms.locfileid: "37784270"
---
# <a name="create-login-transact-sql"></a>CREATE LOGIN (Transact-SQL)

Crée une connexion pour des bases de données SQL Server, SQL Database, SQL Data Warehouse ou Parallel Data Warehouse. Cliquez sur l’un des onglets suivants pour accéder à la syntaxe, aux arguments, aux remarques et aux exemples propres à chaque version.

Pour plus d’informations sur les conventions de la syntaxe, consultez [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).
 
# <a name="sql-servertabsqlserver"></a>[SQL Server](#tab/sqlserver)
  
## <a name="syntax"></a>Syntaxe 
  
```  
-- Syntax for SQL Server  
CREATE LOGIN login_name { WITH <option_list1> | FROM <sources> }  
  
<option_list1> ::=   
    PASSWORD = { 'password' | hashed_password HASHED } [ MUST_CHANGE ]  
    [ , <option_list2> [ ,... ] ]  
  
<option_list2> ::=    
    SID = sid  
    | DEFAULT_DATABASE = database      
    | DEFAULT_LANGUAGE = language  
    | CHECK_EXPIRATION = { ON | OFF}  
    | CHECK_POLICY = { ON | OFF}  
    | CREDENTIAL = credential_name   
  
<sources> ::=  
    WINDOWS [ WITH <windows_options>[ ,... ] ]  
    | CERTIFICATE certname  
    | ASYMMETRIC KEY asym_key_name  
  
<windows_options> ::=        
    DEFAULT_DATABASE = database  
    | DEFAULT_LANGUAGE = language  
```  
  
## <a name="arguments"></a>Arguments  
*login_name*  
Spécifie le nom de la connexion créée. Il existe quatre types de connexions : connexions SQL Server, connexions Windows, connexions mappées par certificat et connexions mappées par clé asymétrique. Quand vous créez des connexions mappées à partir d’un compte de domaine Windows, vous devez utiliser le nom d’ouverture de session de l’utilisateur antérieur à Windows 2000 en respectant le format [\<domainName>\\<login_name>]. Vous ne pouvez pas utiliser un nom UPN au format login_name@DomainName. Consultez l’exemple D plus loin dans cet article. Les connexions d’authentification  sont de type **sysname** et doivent se conformer aux règles applicables aux [identificateurs](http://msdn.microsoft.com/library/ms175874.aspx) et ne peuvent pas contenir de barre oblique inverse (**\\**). Les connexions Windows peuvent contenir une barre oblique inverse (**\\**). Les connexions basées sur les utilisateurs Active Directory sont limitées aux noms de moins de 21 caractères. 

PASSWORD **='***password***'* S’applique uniquement aux connexions SQL Server. Spécifie le mot de passe de la connexion à créer. Il est recommandé d'utiliser un mot de passe fort. Pour plus d’informations, consultez [Mots de passe forts](../../relational-databases/security/strong-passwords.md) et [Stratégie de mot de passe](../../relational-databases/security/password-policy.md). À compter de SQL Server 2012 (11.x), les informations de mot de passe stockées sont calculées à l’aide de algorithme SHA-512 du mot de passe salé. 
  
Les mots de passe respectent la casse. Les mots de passe doivent comporter au moins 8 caractères, et ne peuvent pas dépasser 128 caractères. Les mots de passe peuvent inclure les caractères de A à Z, en minuscules ou en majuscules, les chiffres de 0 à 9 et la plupart des caractères non alphanumériques. Les mots de passe ne peuvent pas contenir de guillemets simples, ni le *login_name*. 
  
PASSWORD **=***hashed_password*  
S'applique uniquement au mot clé HASHED. Spécifie la valeur hachée du mot de passe de la connexion créée. 
  
HASHED S’applique uniquement aux connexions SQL Server. Spécifie que le mot de passe entré après l'argument PASSWORD est déjà haché. Si cette option n'est pas sélectionnée, la chaîne de caractères entrée comme mot de passe est hachée avant d'être stockée dans la base de données. Cette option doit être utilisée uniquement pour effectuer une migration de bases de données d'un serveur vers un autre. N'utilisez pas l'option HASHED pour créer des connexions. L’option HASHED ne peut pas être utilisée avec des hachages créés par SQL 7 ou antérieur.

MUST_CHANGE S’applique uniquement aux connexions SQL Server. Si vous incluez cette option, SQL Server demande à l’utilisateur un nouveau mot de passe la première fois que la nouvelle connexion est utilisée. 
  
CREDENTIAL **=***credential_name*  
Nom des informations d’identification à associer à la nouvelle connexion SQL Server. Les informations d'identification doivent déjà exister sur le serveur. À l'heure actuelle, cette option lie uniquement l'information d'authentification à une connexion. Les informations d’identification ne peuvent pas être mappées à la connexion de l’administrateur système. 
  
SID = *sid*  
Utilisé pour recréer une connexion. S’applique uniquement aux connexions d’authentification SQL Server, et non aux connexions d’authentification Windows. Spécifie le SID de la nouvelle connexion d’authentification SQL Server. Si cette option n’est pas sélectionnée, SQL Server attribue automatiquement un SID. La structure SID dépend de la version de SQL Server. SID de connexion SQL Server : valeur littérale 16 octets (**binary(16)**) basée sur un GUID. Par exemple, `SID = 0x14585E90117152449347750164BA00A7`. 
  
DEFAULT_DATABASE **=***database*  
Spécifie la base de données par défaut à affecter à la connexion. Si cette option est omise, la base de données par défaut est master. 
  
DEFAULT_LANGUAGE **=***language*  
Spécifie la langue par défaut à affecter à la connexion. Si cette option est omise, la langue par défaut est la langue par défaut actuellement définie pour le serveur. Si la langue par défaut du serveur est changée par la suite, la langue par défaut de la connexion reste la même. 
  
CHECK_EXPIRATION **=** { ON | **OFF** }  
S’applique uniquement aux connexions SQL Server. Spécifie si les règles d'expiration des mots de passe doivent être imposées sur cette connexion. La valeur par défaut est OFF. 
  
CHECK_POLICY **=** { **ON** | OFF }  
S’applique uniquement aux connexions SQL Server. Spécifie que les stratégies de mot de passe Windows de l’ordinateur sur lequel SQL Server s’exécute doivent s’appliquer à cette connexion. La valeur par défaut est ON. 
  
Si la stratégie windows requiert des mots de passe forts, les mots de passe doivent avoir au moins trois des quatre caractéristiques suivantes :  
  
- Une majuscule (A-Z). 
- Une minuscule (a-z). 
- Un chiffre (0-9). 
- Un des caractères non alphanumériques, tels qu'un espace, _, @, *, ^, % ! , $, # ou &. 
  
WINDOWS  
Spécifie que la connexion doit être mappée sur une connexion Windows. 
  
CERTIFICATE *certname*  
Spécifie le nom d'un certificat à associer à cette connexion. Ce certificat doit déjà se trouver dans la base de données master. 
  
ASYMMETRIC KEY *asym_key_name*  
Spécifie le nom d'une clé asymétrique à associer à cette connexion. Cette clé doit déjà se trouver dans la base de données master. 
  
## <a name="remarks"></a>Notes   
- Les mots de passe respectent la casse.
- Le hachage préalable des mots de passe est pris en charge uniquement quand vous créez des connexions SQL Server.
- Si MUST_CHANGE est spécifié, CHECK_EXPIRATION et CHECK_POLICY doivent prendre la valeur ON. Sans quoi, l'instruction échoue.
- La combinaison CHECK_POLICY = OFF et CHECK_EXPIRATION = ON n'est pas prise en charge.
- Quand CHECK_POLICY a la valeur OFF, *lockout_time* est réinitialisé et CHECK_EXPIRATION prend la valeur OFF. 
  
> [!IMPORTANT]  
>  CHECK_EXPIRATION et CHECK_POLICY sont uniquement appliqués à Windows Server 2003 et ultérieur. Pour plus d'informations, consultez [Password Policy](../../relational-databases/security/password-policy.md). 
  
- Les connexions créées à partir de certificats ou de clés asymétriques ne sont utilisées que pour la signature de code. Elles ne peuvent pas être utilisées pour se connecter à SQL Server. Vous pouvez créer une connexion à partir d'un certificat ou d'une clé asymétrique uniquement lorsque ceux-ci existent déjà dans la base de données master. 
- Pour obtenir un script de transfert des connexions, consultez [Comment transférer les connexions et les mots de passe entre des instances de SQL Server 2005 et SQL Server 2008](http://support.microsoft.com/kb/918992).
- La création d'une connexion active automatiquement la nouvelle connexion et accorde à la connexion l'autorisation **CONNECT SQL** au niveau du serveur. 
- Le [mode d’authentification](../../relational-databases/security/choose-an-authentication-mode.md) du serveur doit correspondre au type de connexion pour autoriser l’accès.
- Pour plus d’informations sur la conception d’un système d’autorisations, voir [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).

## <a name="permissions"></a>Autorisations  
- Seuls les utilisateurs ayant l’autorisation **ALTER ANY LOGIN** sur le serveur ou appartenant au rôle serveur fixe **securityadmin** peuvent créer des connexions. Pour plus d’informations, consultez [Rôles de niveau serveur](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#groups-and-roles) et [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md).https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles.
- Si l'option **CREDENTIAL** est utilisée, l'autorisation **ALTER ANY CREDENTIAL** est également exigée sur le serveur. 
  
## <a name="after-creating-a-login"></a>Après la création d’une connexion  
Après la création d’une connexion, celle-ci peut se connecter à SQL Server, mais elle dispose uniquement des autorisations accordées au rôle **public**. Envisagez d’effectuer certaines des activités suivantes. 
  
 - Pour vous connecter à une base de données, créez un utilisateur de base de données pour la connexion. Pour plus d’informations, consultez [CREATE USER](../../t-sql/statements/create-user-transact-sql.md). 
  
 - Créez un rôle serveur défini par l’utilisateur à l’aide de [CREATE SERVER ROLE](../../t-sql/statements/create-server-role-transact-sql.md). Utilisez **ALTER SERVER ROLE** ... **ADD MEMBER** pour ajouter la nouvelle connexion au rôle serveur défini par l’utilisateur. Pour plus d’informations, consultez [CREATE SERVER ROLE](../../t-sql/statements/create-server-role-transact-sql.md) et [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). 
  
 - Utilisez **sp_addsrvrolemember** pour ajouter la connexion à un rôle serveur fixe. Pour plus d’informations, consultez [Rôles de niveau serveur](../../relational-databases/security/authentication-access/server-level-roles.md) et [sp_addsrvrolemember](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md). 
  
 - Utilisez l’instruction **GRANT** pour accorder des autorisations au niveau du serveur à la nouvelle connexion ou à un rôle qui contient la connexion. Pour plus d’informations, consultez [GRANT](../../t-sql/statements/grant-transact-sql.md). 
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-login-with-a-password"></a>A. Création d'une connexion avec un mot de passe  
 L'exemple suivant crée une connexion pour un utilisateur particulier et attribue un mot de passe. 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-login-with-a-password-that-must-be-changed"></a>B. Création d’une connexion avec un mot de passe qui doit être changé
 L'exemple suivant crée une connexion pour un utilisateur particulier et attribue un mot de passe. L'option `MUST_CHANGE` exige que les utilisateurs modifient ce mot de passe la première fois qu'ils se connectent au serveur. 
  
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>' 
    MUST_CHANGE,  CHECK_EXPIRATION = ON;
GO  
``` 

> [!NOTE]
> L'option MUST_CHANGE ne peut être utilisée lorsque l'option CHECK_EXPIRATION est désactivée.
  
### <a name="c-creating-a-login-mapped-to-a-credential"></a>C. Création d'une connexion mappée sur une information d'identification  
 L'exemple suivant crée la connexion pour un utilisateur particulier, à l'aide de l'utilisateur. Cette connexion est mappée à l'information d'identification. 
  
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>',   
    CREDENTIAL = <credentialName>;  
GO  
```  
  
### <a name="d-creating-a-login-from-a-certificate"></a>D. Création d'une connexion à partir d'un certificat  
 L’exemple suivant crée la connexion pour un utilisateur particulier à partir d’un certificat dans master. 
  
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
```sql
USE MASTER;  
CREATE CERTIFICATE <certificateName>  
    WITH SUBJECT = '<login_name> certificate in master database',  
    EXPIRY_DATE = '12/05/2025';  
GO  
CREATE LOGIN <login_name> FROM CERTIFICATE <certificateName>;  
GO  
```  
  
### <a name="e-creating-a-login-from-a-windows-domain-account"></a>E. Création d'une connexion à partir d'un compte de domaine Windows  
 L'exemple suivant crée une connexion à partir d'un compte de domaine Windows. 
  
**S'applique à**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] jusqu'à [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. 
  
```sql  
CREATE LOGIN [<domainName>\<login_name>] FROM WINDOWS;  
GO  
```  
  
### <a name="f-creating-a-login-from-a-sid"></a>F. Création d'une connexion à partir d'un SID  
 L’exemple suivant crée d’abord une connexion d’authentification SQL Server et détermine le SID de la connexion. 
  
```sql  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 Ma requête retourne 0x241C11948AEEB749B0D22646DB1A19F2 comme SID. Votre requête retourne une valeur différente. Les instructions suivantes suppriment la connexion, puis recréent la connexion. Utilisez le SID de votre requête précédente. 
  
```sql  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
- [Prise en main des autorisations du moteur de base de données](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
- [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
- [Stratégie de mot de passe](../../relational-databases/security/password-policy.md)   
- [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)   
- [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)   
- [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
- [Créer un compte de connexion](../../relational-databases/security/authentication-access/create-a-login.md)  
  
# <a name="sql-databasetabsqldb"></a>[SQL Database](#tab/sqldb)
  
## <a name="syntax"></a>Syntaxe 
  
```
-- Syntax for Azure SQL Database  
CREATE LOGIN login_name  
 { WITH <option_list> }  
  
<option_list> ::=   
    PASSWORD = { 'password' }  
    [ , SID = sid ]  
```  

> [!IMPORTANT]  
> Sur [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), cette fonctionnalité T-SQL présente des changements de comportement. Pour plus d’informations sur tous les changements de comportement de T-SQL, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information).
  
## <a name="arguments"></a>Arguments  
*login_name*  
Spécifie le nom de la connexion créée. Azure SQL Database prend uniquement en charge les connexions SQL. 

PASSWORD **='** password**'*  
Spécifie le mot de passe de la connexion SQL en cours de création. Il est recommandé d'utiliser un mot de passe fort. Pour plus d’informations, consultez [Mots de passe forts](../../relational-databases/security/strong-passwords.md) et [Stratégie de mot de passe](../../relational-databases/security/password-policy.md). Depuis [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], les informations de mot de passe stockées sont calculées à l’aide de la valeur salt SHA-512 du mot de passe. 
  
Les mots de passe respectent la casse. Les mots de passe doivent comporter au moins 8 caractères, et ne peuvent pas dépasser 128 caractères. Les mots de passe peuvent inclure les caractères de A à Z, en minuscules ou en majuscules, les chiffres de 0 à 9 et la plupart des caractères non alphanumériques. Les mots de passe ne peuvent pas contenir de guillemets simples, ni le *login_name*. 

SID = *sid*  
Utilisé pour recréer une connexion. S’applique uniquement aux connexions d’authentification SQL Server, et non aux connexions d’authentification Windows. Spécifie le SID de la nouvelle connexion d’authentification SQL Server. Si cette option n’est pas sélectionnée, SQL Server attribue automatiquement un SID. La structure SID dépend de la version de SQL Server. Pour SQL Database, il s’agit d’un littéral 32 octets (**binary(32)**) composé de `0x01060000000000640000000000000000` plus 16 octets représentant un GUID. Par exemple, `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`. 
  
## <a name="remarks"></a>Notes   
- Les mots de passe respectent la casse.
- Pour obtenir un script de transfert des connexions, consultez [Comment transférer les connexions et les mots de passe entre des instances de SQL Server 2005 et SQL Server 2008](http://support.microsoft.com/kb/918992).
- La création d'une connexion active automatiquement la nouvelle connexion et accorde à la connexion l'autorisation **CONNECT SQL** au niveau du serveur. 
- Le [mode d’authentification](../../relational-databases/security/choose-an-authentication-mode.md) du serveur doit correspondre au type de connexion pour autoriser l’accès.
    - Pour plus d’informations sur la conception d’un système d’autorisations, voir [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).
  
## <a name="login"></a>Connexion

### <a name="sql-database-logins"></a>Connexions à une base de données SQL
L’instruction **CREATE LOGIN** doit être la seule instruction d’un traitement. 
  
Dans certaines méthodes de connexion à SQL Database, comme **sqlcmd**, vous devez ajouter le nom du serveur SQL Database au nom de connexion dans la chaîne de connexion à l’aide de la notation *\<connexion>*@*\<serveur>*. Par exemple, si votre connexion est `login1` et que le nom complet du serveur SQL Database est `servername.database.windows.net`, le paramètre *username* de la chaîne de connexion doit être `login1@servername`. Puisque la longueur totale du paramètre *username* est de 128 caractères, *login_name* est limité à 127 caractères moins la longueur du nom du serveur. Dans l'exemple, `login_name` peut contenir seulement 117 caractères car `servername` inclut 10 caractères. 
  
Dans SQL Database, vous devez être connecté à la base de données master pour créer une connexion. 
  
 Les règles SQL Server permettent de créer une connexion d’authentification SQL Server au format \<nom_connexion>@\<nom_serveur>. Si votre serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] est **myazureserver** et que l’identifiant de connexion est **myemail@live.com**, vous devez fournir votre identifiant de connexion comme suit : **myemail@live.com@myazureserver**. 
  
Dans SQL Database, les données de connexion exigées pour authentifier une connexion et les règles de pare-feu de niveau serveur sont temporairement mises en cache dans chaque base de données. Ce cache est régulièrement actualisé. Pour forcer une actualisation du cache d’authentification et garantir qu’une base de données a la version la plus récente de la table de connexions, exécutez [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md). 
  
 Pour plus d’informations sur les connexions SQL Database, consultez [Gestion des bases de données et des connexions dans Microsoft Azure SQL Database](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins). 
 
## <a name="permissions"></a>Autorisations

Seule la connexion principale au niveau du serveur (créée par le processus de configuration) ou les membres du rôle de base de données `loginmanager` dans la base de données master peuvent créer des connexions. Pour plus d’informations, consultez [Rôles de niveau serveur](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#groups-and-roles) et [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md).https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles.

## <a name="logins"></a>Connexions
- Nécessite l’autorisation **ALTER ANY LOGIN** sur le serveur ou l’appartenance au rôle serveur fixe **securityadmin**. Seul un compte Azure Active Directory (Azure AD) avec l’autorisation **ALTER ANY LOGIN** sur le serveur ou l’appartenance à l’autorisation securityadmin peut exécuter cette commande.
- Doit être un membre d’Azure AD dans le même répertoire que celui utilisé pour le serveur logique SQL Azure.
  
## <a name="after-creating-a-login"></a>Après la création d’une connexion  
Après la création d’une connexion, celle-ci peut se connecter à SQL Database, mais elle dispose uniquement des autorisations accordées au rôle **public**. Envisagez d’effectuer certaines des activités suivantes. 
  
- Pour vous connecter à une base de données, créez un utilisateur de base de données pour la connexion à cette base de données. Pour plus d’informations, consultez [CREATE USER](../../t-sql/statements/create-user-transact-sql.md). 
- Pour accorder des autorisations à un utilisateur dans une base de données, utilisez l’instruction **ALTER SERVER ROLE** … **ADD MEMBER** pour ajouter l’utilisation à l’un des rôles de base de données intégrés ou à un rôle personnalisé, ou accordez directement des autorisations à l’utilisateur à l’aide de l’instruction [GRANT]((../../t-sql/statements/grant-transact-sql.md). Pour plus d’informations, consultez [Utilisateurs non administrateurs](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#non-administrator-users), [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md).https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles et l’instruction [GRANT](grant-transact-sql.md).
- Pour accorder des autorisations à l’échelle du serveur, créez un utilisateur de base de données dans la base de données master et utilisez l’instruction **ALTER SERVER ROLE** … **ADD MEMBER** pour ajouter l’utilisation à l’un des rôles serveur d’administration. Pour plus d’informations, consultez [Rôles de niveau serveur](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#groups-and-roles), [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) et [Rôles serveur](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles).
- Utilisez l’instruction **GRANT** pour accorder des autorisations au niveau du serveur à la nouvelle connexion ou à un rôle qui contient la connexion. Pour plus d’informations, consultez [GRANT](../../t-sql/statements/grant-transact-sql.md).
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-login-with-a-password"></a>A. Création d'une connexion avec un mot de passe  
 L'exemple suivant crée une connexion pour un utilisateur particulier et attribue un mot de passe. 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-login-from-a-sid"></a>B. Création d'une connexion à partir d'un SID  
 L’exemple suivant crée d’abord une connexion d’authentification SQL Server et détermine le SID de la connexion. 
  
```sql  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 Ma requête retourne 0x241C11948AEEB749B0D22646DB1A19F2 comme SID. Votre requête retourne une valeur différente. Les instructions suivantes suppriment la connexion, puis recréent la connexion. Utilisez le SID de votre requête précédente. 
  
```sql  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Prise en main des autorisations du moteur de base de données](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Stratégie de mot de passe](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [Créer un compte de connexion](../../relational-databases/security/authentication-access/create-a-login.md)  
  
# <a name="sql-data-warehousetabsqldw"></a>[SQL Data Warehouse](#tab/sqldw)
  
## <a name="syntax"></a>Syntaxe 
  
```
-- Syntax for Azure SQL Data Warehouse  
CREATE LOGIN login_name  
 { WITH <option_list> }  
  
<option_list> ::=   
    PASSWORD = { 'password' }  
    [ , SID = sid ]  
```  
  
## <a name="arguments"></a>Arguments  
*login_name*  
Spécifie le nom de la connexion créée. Azure SQL Database prend uniquement en charge les connexions SQL. 

PASSWORD **='** password**'*  
Spécifie le mot de passe de la connexion SQL en cours de création. Il est recommandé d'utiliser un mot de passe fort. Pour plus d’informations, consultez [Mots de passe forts](../../relational-databases/security/strong-passwords.md) et [Stratégie de mot de passe](../../relational-databases/security/password-policy.md). Depuis [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], les informations de mot de passe stockées sont calculées à l’aide de la valeur salt SHA-512 du mot de passe. 
  
Les mots de passe respectent la casse. Les mots de passe doivent comporter au moins 8 caractères, et ne peuvent pas dépasser 128 caractères. Les mots de passe peuvent inclure les caractères de A à Z, en minuscules ou en majuscules, les chiffres de 0 à 9 et la plupart des caractères non alphanumériques. Les mots de passe ne peuvent pas contenir de guillemets simples, ni le *login_name*. 

 SID = *sid*  
 Utilisé pour recréer une connexion. S’applique uniquement aux connexions d’authentification SQL Server, et non aux connexions d’authentification Windows. Spécifie le SID de la nouvelle connexion d’authentification SQL Server. Si cette option n’est pas sélectionnée, SQL Server attribue automatiquement un SID. La structure SID dépend de la version de SQL Server. Pour SQL Data Warehouse, il s’agit d’un littéral 32 octets (**binary(32)**) composé de `0x01060000000000640000000000000000` plus 16 octets représentant un GUID. Par exemple, `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`. 
  
## <a name="remarks"></a>Notes   
- Les mots de passe respectent la casse.
- Pour obtenir un script de transfert des connexions, consultez [Comment transférer les connexions et les mots de passe entre des instances de SQL Server 2005 et SQL Server 2008](http://support.microsoft.com/kb/918992).
- La création d'une connexion active automatiquement la nouvelle connexion et accorde à la connexion l'autorisation **CONNECT SQL** au niveau du serveur. 
- Le [mode d’authentification](../../relational-databases/security/choose-an-authentication-mode.md) du serveur doit correspondre au type de connexion pour autoriser l’accès.
    - Pour plus d’informations sur la conception d’un système d’autorisations, voir [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).
  
## <a name="logins"></a>Connexions

L’instruction **CREATE LOGIN** doit être la seule instruction d’un traitement. 
  
Dans certaines méthodes de connexion à SQL Data Warehouse, comme **sqlcmd**, vous devez ajouter le nom du serveur SQL Data Warehouse au nom de connexion dans la chaîne de connexion à l’aide de la notation *\<connexion>*@*\<serveur>*. Par exemple, si votre connexion est `login1` et que le nom complet du serveur SQL Database Warehouse est `servername.database.windows.net`, le paramètre *username* de la chaîne de connexion doit être `login1@servername`. Puisque la longueur totale du paramètre *username* est de 128 caractères, *login_name* est limité à 127 caractères moins la longueur du nom du serveur. Dans l'exemple, `login_name` peut contenir seulement 117 caractères car `servername` inclut 10 caractères. 
  
Dans SQL Database Warehouse, vous devez être connecté à la base de données master pour créer une connexion. 
  
 Les règles SQL Server permettent de créer une connexion d’authentification SQL Server au format \<nom_connexion>@\<nom_serveur>. Si votre serveur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] est **myazureserver** et que l’identifiant de connexion est **myemail@live.com**, vous devez fournir votre identifiant de connexion comme suit : **myemail@live.com@myazureserver**. 
  
Dans SQL Database Warehouse, les données de connexion exigées pour authentifier une connexion et les règles de pare-feu de niveau serveur sont temporairement mises en cache dans chaque base de données. Ce cache est régulièrement actualisé. Pour forcer une actualisation du cache d’authentification et garantir qu’une base de données a la version la plus récente de la table de connexions, exécutez [DBCC FLUSHAUTHCACHE](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md). 
  
 Pour plus d’informations sur les connexions SQL Database Warehouse, consultez [Gestion des bases de données et des connexions dans Microsoft Azure SQL Database](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins). 
 
## <a name="permissions"></a>Autorisations

Seule la connexion principale au niveau du serveur (créée par le processus de configuration) ou les membres du rôle de base de données `loginmanager` dans la base de données master peuvent créer des connexions. Pour plus d’informations, consultez [Rôles de niveau serveur](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#groups-and-roles) et [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md).https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles.

## <a name="after-creating-a-login"></a>Après la création d’une connexion  
Après la création d’une connexion, celle-ci peut se connecter à SQL Database Warehouse, mais elle dispose uniquement des autorisations accordées au rôle **public**. Envisagez d’effectuer certaines des activités suivantes. 
  
- Pour vous connecter à une base de données, créez un utilisateur de base de données pour la connexion. Pour plus d’informations, consultez [CREATE USER](../../t-sql/statements/create-user-transact-sql.md).
- Pour accorder des autorisations à un utilisateur dans une base de données, utilisez l’instruction **ALTER SERVER ROLE** … **ADD MEMBER** pour ajouter l’utilisation à l’un des rôles de base de données intégrés ou à un rôle personnalisé, ou accordez directement des autorisations à l’utilisateur à l’aide de l’instruction [GRANT](grant-transact-sql.md). Pour plus d’informations, consultez [Utilisateurs non administrateurs](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#non-administrator-users), [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md).https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles et l’instruction [GRANT](grant-transact-sql.md).
- Pour accorder des autorisations à l’échelle du serveur, créez un utilisateur de base de données dans la base de données master et utilisez l’instruction **ALTER SERVER ROLE** … **ADD MEMBER** pour ajouter l’utilisation à l’un des rôles serveur d’administration. Pour plus d’informations, consultez [Rôles de niveau serveur](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#groups-and-roles), [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md) et [Rôles serveur](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles).

- Utilisez l’instruction **GRANT** pour accorder des autorisations au niveau du serveur à la nouvelle connexion ou à un rôle qui contient la connexion. Pour plus d’informations, consultez [GRANT](../../t-sql/statements/grant-transact-sql.md). 
  
## <a name="examples"></a>Exemples  
  
### <a name="a-creating-a-login-with-a-password"></a>A. Création d'une connexion avec un mot de passe  
L'exemple suivant crée une connexion pour un utilisateur particulier et attribue un mot de passe. 
  
```sql  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  

### <a name="b-creating-a-login-from-a-sid"></a>B. Création d'une connexion à partir d'un SID  
 L’exemple suivant crée d’abord une connexion d’authentification SQL Server et détermine le SID de la connexion. 
  
```sql  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 Ma requête retourne 0x241C11948AEEB749B0D22646DB1A19F2 comme SID. Votre requête retourne une valeur différente. Les instructions suivantes suppriment la connexion, puis recréent la connexion. Utilisez le SID de votre requête précédente. 
  
```sql  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Prise en main des autorisations du moteur de base de données](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Stratégie de mot de passe](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [Créer un compte de connexion](../../relational-databases/security/authentication-access/create-a-login.md)  
  
# <a name="sql-parallel-data-warehousetabsqlpdw"></a>[SQL Parallel Data Warehouse](#tab/sqlpdw)
  
## <a name="syntax"></a>Syntaxe 
  
```
-- Syntax for Parallel Data Warehouse  
CREATE LOGIN loginName { WITH <option_list1> | FROM WINDOWS }  
  
<option_list1> ::=   
    PASSWORD = { 'password' } [ MUST_CHANGE ]  
    [ , <option_list> [ ,... ] ]  
  
<option_list> ::=    
      CHECK_EXPIRATION = { ON | OFF}  
    | CHECK_POLICY = { ON | OFF}  
```  

## <a name="arguments"></a>Arguments  
*login_name*  
Spécifie le nom de la connexion créée. Il existe quatre types de connexions : connexions SQL Server, connexions Windows, connexions mappées par certificat et connexions mappées par clé asymétrique. Quand vous créez des connexions mappées à partir d’un compte de domaine Windows, vous devez utiliser le nom d’ouverture de session de l’utilisateur antérieur à Windows 2000 en respectant le format [\<domainName>\\<login_name>]. Vous ne pouvez pas utiliser un nom UPN au format login_name@DomainName. Consultez l’exemple D plus loin dans cet article. Les connexions d’authentification  sont de type **sysname** et doivent se conformer aux règles applicables aux [identificateurs](http://msdn.microsoft.com/library/ms175874.aspx) et ne peuvent pas contenir de barre oblique inverse (**\\**). Les connexions Windows peuvent contenir une barre oblique inverse (**\\**). Les connexions basées sur les utilisateurs Active Directory sont limitées aux noms de moins de 21 caractères. 

PASSWORD **='***password***'* S’applique uniquement aux connexions SQL Server. Spécifie le mot de passe de la connexion à créer. Il est recommandé d'utiliser un mot de passe fort. Pour plus d’informations, consultez [Mots de passe forts](../../relational-databases/security/strong-passwords.md) et [Stratégie de mot de passe](../../relational-databases/security/password-policy.md). À compter de SQL Server 2012 (11.x), les informations de mot de passe stockées sont calculées à l’aide de algorithme SHA-512 du mot de passe salé. 
  
Les mots de passe respectent la casse. Les mots de passe doivent comporter au moins 8 caractères, et ne peuvent pas dépasser 128 caractères. Les mots de passe peuvent inclure les caractères de A à Z, en minuscules ou en majuscules, les chiffres de 0 à 9 et la plupart des caractères non alphanumériques. Les mots de passe ne peuvent pas contenir de guillemets simples, ni le *login_name*. 
  
MUST_CHANGE S’applique uniquement aux connexions SQL Server. Si vous incluez cette option, SQL Server demande à l’utilisateur un nouveau mot de passe la première fois que la nouvelle connexion est utilisée. 
  
CHECK_EXPIRATION **=** { ON | **OFF** }  
S’applique uniquement aux connexions SQL Server. Spécifie si les règles d'expiration des mots de passe doivent être imposées sur cette connexion. La valeur par défaut est OFF. 
  
CHECK_POLICY **=** { **ON** | OFF }  
S’applique uniquement aux connexions SQL Server. Spécifie que les stratégies de mot de passe Windows de l’ordinateur sur lequel SQL Server s’exécute doivent s’appliquer à cette connexion. La valeur par défaut est ON. 
  
Si la stratégie windows requiert des mots de passe forts, les mots de passe doivent avoir au moins trois des quatre caractéristiques suivantes :  
  
- Une majuscule (A-Z). 
- Une minuscule (a-z). 
- Un chiffre (0-9). 
- Un des caractères non alphanumériques, tels qu'un espace, _, @, *, ^, % ! , $, # ou &. 
  
WINDOWS  
Spécifie que la connexion doit être mappée sur une connexion Windows. 
  
## <a name="remarks"></a>Notes   
- Les mots de passe respectent la casse.
- Si MUST_CHANGE est spécifié, CHECK_EXPIRATION et CHECK_POLICY doivent prendre la valeur ON. Sans quoi, l'instruction échoue.
- La combinaison CHECK_POLICY = OFF et CHECK_EXPIRATION = ON n'est pas prise en charge.
- Quand CHECK_POLICY a la valeur OFF, *lockout_time* est réinitialisé et CHECK_EXPIRATION prend la valeur OFF. 
  
> [!IMPORTANT]  
>  CHECK_EXPIRATION et CHECK_POLICY sont uniquement appliqués à Windows Server 2003 et ultérieur. Pour plus d'informations, consultez [Password Policy](../../relational-databases/security/password-policy.md). 
  
- Pour obtenir un script de transfert des connexions, consultez [Comment transférer les connexions et les mots de passe entre des instances de SQL Server 2005 et SQL Server 2008](http://support.microsoft.com/kb/918992).
- La création d'une connexion active automatiquement la nouvelle connexion et accorde à la connexion l'autorisation **CONNECT SQL** au niveau du serveur. 
- Pour plus d’informations sur la conception d’un système d’autorisations, voir [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md).

## <a name="permissions"></a>Autorisations  
Seuls les utilisateurs ayant l’autorisation **ALTER ANY LOGIN** sur le serveur ou appartenant au rôle serveur fixe **securityadmin** peuvent créer des connexions. Pour plus d’informations, consultez [Rôles de niveau serveur](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#groups-and-roles) et [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md).https://docs.microsoft.com/en-us/azure/sql-database/sql-database-manage-logins#additional-server-level-administrative-roles.
  
## <a name="after-creating-a-login"></a>Après la création d’une connexion  
Après la création d’une connexion, celle-ci peut se connecter à SQL Database Warehouse, mais elle dispose uniquement des autorisations accordées au rôle **public**. Envisagez d’effectuer certaines des activités suivantes. 
  
 - Pour vous connecter à une base de données, créez un utilisateur de base de données pour la connexion. Pour plus d’informations, consultez [CREATE USER](../../t-sql/statements/create-user-transact-sql.md). 
  
 - Créez un rôle serveur défini par l’utilisateur à l’aide de [CREATE SERVER ROLE](../../t-sql/statements/create-server-role-transact-sql.md). Utilisez **ALTER SERVER ROLE** ... **ADD MEMBER** pour ajouter la nouvelle connexion au rôle serveur défini par l’utilisateur. Pour plus d’informations, consultez [CREATE SERVER ROLE](../../t-sql/statements/create-server-role-transact-sql.md) et [ALTER SERVER ROLE](../../t-sql/statements/alter-server-role-transact-sql.md). 
  
 - Utilisez **sp_addsrvrolemember** pour ajouter la connexion à un rôle serveur fixe. Pour plus d’informations, consultez [Rôles de niveau serveur](../../relational-databases/security/authentication-access/server-level-roles.md) et [sp_addsrvrolemember](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md). 
  
 - Utilisez l’instruction **GRANT** pour accorder des autorisations au niveau du serveur à la nouvelle connexion ou à un rôle qui contient la connexion. Pour plus d’informations, consultez [GRANT](../../t-sql/statements/grant-transact-sql.md). 
  
## <a name="examples"></a>Exemples  
  
### <a name="g-creating-a-sql-server-authentication-login-with-a-password"></a>G. Création d’une connexion d’authentification SQL Server avec un mot de passe  
 L’exemple suivant crée la connexion `Mary7` avec le mot de passe `A2c3456`. 
  
```sql  
CREATE LOGIN Mary7 WITH PASSWORD = 'A2c3456$#' ;  
```  
  
### <a name="h-using-options"></a>H. Utilisation d’options  
 L’exemple suivant crée la connexion `Mary8` avec le mot de passe et certains arguments facultatifs. 
  
```sql  
CREATE LOGIN Mary8 WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
```  
  
### <a name="i-creating-a-login-from-a-windows-domain-account"></a>I. Création d'une connexion à partir d'un compte de domaine Windows  
 L’exemple suivant crée une connexion à partir d’un compte de domaine Windows nommé `Mary` dans le domaine `Contoso`. 
  
```sql  
CREATE LOGIN [Contoso\Mary] FROM WINDOWS;  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Prise en main des autorisations du moteur de base de données](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Stratégie de mot de passe](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA](../../t-sql/functions/eventdata-transact-sql.md)   
 [Créer un compte de connexion](../../relational-databases/security/authentication-access/create-a-login.md)  
  
---  

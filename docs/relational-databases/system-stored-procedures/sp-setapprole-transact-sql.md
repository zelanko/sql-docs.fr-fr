---
title: sp_setapprole (Transact-SQL) Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_setapprole
- sp_setapprole_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_setapprole
ms.assetid: cf0901c0-5f90-42d4-9d5b-8772c904062d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: b158c4571deadadeaee23ffa6e46eb48a8c8446e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299596"
---
# <a name="sp_setapprole-transact-sql"></a>sp_setapprole (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Active les autorisations associées à un rôle d'application dans la base de données active.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  

```sql
sp_setapprole [ @rolename = ] 'role',  
    [ @password = ] { encrypt N'password' }
      |  
        'password' [ , [ @encrypt = ] { 'none' | 'odbc' } ]  
        [ , [ @fCreateCookie = ] true | false ]  
    [ , [ @cookie = ] @cookie OUTPUT ]  
```

## <a name="arguments"></a>Arguments

`[ @rolename = ] 'role'`Est-ce le nom du rôle d’application défini dans la base de données actuelle. *rôle* est **sysname**, sans défaut. *rôle* doit exister dans la base de données actuelle.  
  
`[ @password = ] { encrypt N'password' }`Le mot de passe est-il nécessaire pour activer le rôle d’application. *mot de passe* est **sysname**, sans défaut. *mot de passe* peut être obscurci en utilisant la fonction **de cryptage** ODBC. Lorsque vous utilisez la fonction **de chiffrement,** le mot de passe doit être converti en chaîne Unicode en plaçant **N** avant la première marque de cotation.  
  
 L’option de chiffrement n’est pas pris en charge sur les connexions qui utilisent **SqlClient**.  
  
> [!IMPORTANT]  
> La fonction **de chiffrement** ODBC ne fournit pas de chiffrement. Vous ne devez pas compter sur cette fonction pour protéger des mots de passe transmis sur un réseau. Si ces informations sont transmises sur un réseau, utilisez TLS ou IPSec.
  
 **@encrypt'aucun'**  
 Indique qu'aucun codage ne doit être utilisé. Le mot de passe est transmis à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sous forme de texte brut. Il s’agit de la valeur par défaut.  
  
 **@encrypt'odbc'**  
 Spécifie que L’ODBC obscurcira le mot de passe en utilisant la [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]fonction **de cryptage** ODBC avant d’envoyer le mot de passe à la . Ceci peut être spécifié seulement si vous utilisez un client ODBC ou le fournisseur OLE DB pour SQL Server.  
  
`[ @fCreateCookie = ] true | false`Précise si un cookie doit être créé. **vrai** est implicitement converti en 1. **faux** est implicitement converti en 0.  
  
`[ @cookie = ] @cookie OUTPUT`Spécifie un paramètre de sortie pour contenir le cookie. Le cookie n’est généré que si la valeur de ** \@fCreateCookie** est **vraie**. **varbinary(8000)**  
  
> [!NOTE]  
> Le paramètre **OUTPUT** de cookie pour **sp_setapprole** est actuellement documenté comme **varbinary(8000)** , ce qui correspond à la longueur maximale correcte. Cependant, l’implémentation actuelle retourne **varbinary(50)**. Les applications doivent continuer à réserver **le varbinaire(8000)** de sorte que l’application continue à fonctionner correctement si la taille du retour de cookie augmente dans une version future.
  
## <a name="return-code-values"></a>Codet de retour

 0 (succès) et 1 (échec)  
  
## <a name="remarks"></a>Notes

 Après qu’un rôle d’application est activé en utilisant **sp_setapprole,** le rôle reste actif jusqu’à ce que l’utilisateur se déconnecte du serveur ou exécute **sp_unsetapprole**. **sp_setapprole** ne peuvent être exécutés [!INCLUDE[tsql](../../includes/tsql-md.md)] que par des déclarations directes. **sp_setapprole** ne peuvent pas être exécutés dans le cadre d’une autre procédure stockée ou dans le cadre d’une transaction définie par l’utilisateur.  
  
 Pour un aperçu des rôles d’application, voir [rôles d’application](../../relational-databases/security/authentication-access/application-roles.md).  
  
> [!IMPORTANT]  
> Pour protéger le mot de passe du rôle d’application lorsqu’il est transmis sur un réseau, vous devez toujours utiliser une connexion cryptée lorsque vous activez un rôle d’application.
> L’option [!INCLUDE[msCoName](../../includes/msconame-md.md)] **de cryptage** ODBC n’est pas pris en charge par **SqlClient**. Si vous devez stocker des informations d'identification, chiffrez-les à l'aide des fonctions API de chiffrement. Le *mot de passe* paramètre est stocké comme un hachage à sens unique. Pour préserver la compatibilité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]avec les versions antérieures de , la politique de complexité de mot de passe n’est pas appliquée par **sp_addapprole**. Pour faire respecter la politique de complexité des mots de passe, utilisez [CREATE APPLICATION ROLE](../../t-sql/statements/create-application-role-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations

Nécessite l’adhésion au **public** et la connaissance du mot de passe pour le rôle.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-activating-an-application-role-without-the-encrypt-option"></a>R. Activation d'un rôle d'application sans l'option encrypt

 Dans l'exemple ci-dessous, un rôle d'application nommé `SalesAppRole` est activé avec le mot de passe en texte brut `AsDeF00MbXX`, créé avec les autorisations spécialement conçues pour l'application utilisée par l'utilisateur en cours.

```sql
EXEC sys.sp_setapprole 'SalesApprole', 'AsDeF00MbXX';  
GO
```

### <a name="b-activating-an-application-role-with-a-cookie-and-then-reverting-to-the-original-context"></a>B. Activation d'un rôle d'application avec un cookie, puis retour au contexte d'origine

 Dans l'exemple ci-dessous, le rôle d'application `Sales11` est activé avec le mot de passe `fdsd896#gfdbfdkjgh700mM` et un cookie est créé. L'exemple retourne le nom de l'utilisateur actuel, puis revient au contexte d'origine en exécutant `sp_unsetapprole`.  

```sql
DECLARE @cookie varbinary(8000);  
EXEC sys.sp_setapprole 'Sales11', 'fdsd896#gfdbfdkjgh700mM'  
    , @fCreateCookie = true, @cookie = @cookie OUTPUT;  
-- The application role is now active.  
SELECT USER_NAME();  
-- This will return the name of the application role, Sales11.  
EXEC sys.sp_unsetapprole @cookie;  
-- The application role is no longer active.  
-- The original context has now been restored.  
GO  
SELECT USER_NAME();  
-- This will return the name of the original user.
GO
```

## <a name="see-also"></a>Voir aussi

 Procédures de stockage du système &#40;Procédures de stockage de sécurité&#41;de [transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md) [&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md) CREATE APPLICATION ROLE [&#40;Transact-SQL&#41;](../../t-sql/statements/create-application-role-transact-sql.md) DROP APPLICATION ROLE &#40;[Transact-SQL&#41;](../../t-sql/statements/drop-application-role-transact-sql.md) sp_unsetapprole &#40;[Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unsetapprole-transact-sql.md)

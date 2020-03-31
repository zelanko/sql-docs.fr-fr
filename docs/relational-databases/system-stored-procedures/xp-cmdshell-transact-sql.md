---
title: xp_cmdshell (Transact-SQL) Microsoft Docs
ms.custom: ''
ms.date: 03/30/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- xp_cmdshell
- xp_cmdshell_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: 18935cf4-b320-4954-b6c1-e007fcefe358
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 2ce32fc31373077418e77d31ce064d60e23f1b24
ms.sourcegitcommit: fc5b757bb27048a71bb39755648d5cefe25a8bc6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80402692"
---
# <a name="xp_cmdshell-transact-sql"></a>xp_cmdshell (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Engendre une commande d'environnement Windows et lui transmet une chaîne à traiter. Toute sortie est retournée sous forme de lignes de texte.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
xp_cmdshell { 'command_string' } [ , no_output ]  
```  
  
## <a name="arguments"></a>Arguments  
 **'** *command_string* **'**  
 Chaîne qui contient une commande à transmettre au système d'exploitation. *command_string* est **varchar(8000)** ou **nvarchar(4000)**, sans défaut. *command_string* ne peut contenir plus d’un ensemble de doubles guillemets. Une seule paire de guillemets est requise si des espaces sont présents dans les trajectoires de fichiers ou les noms de programme référencés dans *command_string*. Si l'incorporation d'espaces est source de problèmes, recourez à des noms de fichiers FAT 8.3.  
  
 **no_output**  
 Paramètre facultatif indiquant qu'aucune sortie ne doit être retournée au client.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 L'exécution de l'instruction `xp_cmdshell` ci-dessous retourne le contenu du répertoire en cours.  
  
```  
EXEC xp_cmdshell 'dir *.exe';  
GO  
```  
  
 Les lignes sont retournées dans une colonne **nvarchar(255).** Si **l’option no_output** est utilisée, seul ce qui suit sera retourné :  
  
```  
The command(s) completed successfully.  
```  
  
## <a name="remarks"></a>Notes   
 Le processus Windows engendré par **xp_cmdshell** a les mêmes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] droits de sécurité que le compte de service.  
  
 **xp_cmdshell** fonctionne de façon synchrone. Le contrôle n'est renvoyé à l'appelant que lorsque la commande de l'interpréteur de commandes est terminée.  
  
 **xp_cmdshell** peuvent être activés et désactivés en utilisant la gestion basée sur les politiques ou en exécutant **sp_configure**. Pour plus d’informations, consultez [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md) et xp_cmdshell Server Configuration [Option](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
> [!IMPORTANT]
>  Si **xp_cmdshell** est exécuté dans un lot et renvoie une erreur, le lot échouera.
  
## <a name="xp_cmdshell-proxy-account"></a>Compte proxy xp_cmdshell  
 Lorsqu’il est appelé par un utilisateur qui n’est pas un membre du rôle de serveur fixe **sysadmin,** **xp_cmdshell** se connecte à Windows en utilisant le nom de compte et mot de passe stockés dans l’identification nommée **«#xp_cmdshell_proxy_account».** Si cette pièce d’identification par procuration n’existe pas, **xp_cmdshell** échouera.  
  
 L’identifiant de compte proxy peut être créé en exécutant **sp_xp_cmdshell_proxy_account**. Cette procédure stockée accepte comme arguments un nom d'utilisateur et un mot de passe Windows. Par exemple, la commande ci-dessous crée des informations d'identification de proxy pour l'utilisateur de domaine Windows `SHIPPING\KobeR` qui possède le mot de passe Windows `sdfh%dkc93vcMt0`.  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'SHIPPING\KobeR','sdfh%dkc93vcMt0';  
```  
  
 Pour plus d’informations, voir [sp_xp_cmdshell_proxy_account &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Parce que les utilisateurs malveillants tentent parfois d’élever leurs privilèges en utilisant **xp_cmdshell**, **xp_cmdshell** est désactivé par défaut. Utilisez **sp_configure** ou **la gestion fondée sur les politiques** pour l’activer. Pour plus d’informations, consultez [xp_cmdshell (option de configuration de serveur)](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md).  
  
 Lors de la première application, **xp_cmdshell** nécessite l’autorisation CONTROL SERVER pour exécuter et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le processus Windows créé par **xp_cmdshell** a le même contexte de sécurité que le compte de service. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compte de service a souvent plus d’autorisations que nécessaire pour le travail effectué par le processus créé par **xp_cmdshell**. Pour renforcer la sécurité, l’accès à **xp_cmdshell** devrait être limité aux utilisateurs très privilégiés.  
  
 Pour permettre aux non-administrateurs d’utiliser **xp_cmdshell**et permettre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de créer des processus pour enfants avec le gage de sécurité d’un compte moins privilégié, suivez ces étapes :  
  
1.  Créez et personnalisez un compte d'utilisateur local Windows ou un compte de domaine avec les privilèges minimaux requis par vos processus.  
  
2.  Utilisez la procédure **sp_xp_cmdshell_proxy_account** système pour configurer **xp_cmdshell** pour utiliser ce compte le moins privilégié.  
  
    > [!NOTE]  
    >  Vous pouvez également configurer [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ce compte proxy en utilisant en cliquant sur les **propriétés droites** sur le nom de votre serveur dans Object Explorer, et en regardant sur **l’onglet De sécurité** pour la section **compte proxy Server.**  
  
3.  En [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], en utilisant la `GRANT exec ON xp_cmdshell TO N'<some_user>';` base de données principale, exécuter la déclaration pour donner aux utilisateurs spécifiques**non-sysadmin** la possibilité d’exécuter **xp_cmdshell**. L’utilisateur spécifié doit exister dans la base de données principale.  
  
 Maintenant, les non-administrateurs peuvent lancer des processus de système d’exploitation avec **xp_cmdshell** et ces processus s’exécutent avec les autorisations du compte proxy que vous avez configuré. Les utilisateurs avec l’autorisation CONTROL SERVER (membres du rôle de serveur fixe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sysadmin)** continueront à recevoir les autorisations du compte de service pour les processus pour enfants qui sont lancés par **xp_cmdshell**.  
  
 Pour déterminer le compte Windows utilisé par **xp_cmdshell** lors du lancement des processus du système d’exploitation, exécutez l’instruction suivante :  
  
```  
xp_cmdshell 'whoami.exe'  
  
```  
  
 Pour déterminer le contexte de sécurité pour une autre connexion, exécutez ce qui suit :  
  
```  
EXECUTE AS LOGIN = '<other_login>' ;  
GO  
xp_cmdshell 'whoami.exe' ;  
REVERT ;  
  
```  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-returning-a-list-of-executable-files"></a>R. Retour d'une liste de fichiers exécutables  
 L'exemple ci-dessous montre la procédure stockée étendue `xp_cmdshell` exécutant une commande de répertoire.  
  
```  
EXEC master..xp_cmdshell 'dir *.exe'  
```  
  
### <a name="b-returning-no-output"></a>B. Aucun renvoi d'information en sortie  
 L'exemple ci-dessous utilise `xp_cmdshell` pour exécuter une chaîne de commande sans retourner les informations en sortie au client.  
  
```  
USE master;  
  
EXEC xp_cmdshell 'copy c:\SQLbcks\AdvWorks.bck  
    \\server2\backups\SQLbcks', NO_OUTPUT;  
GO  
```  
  
### <a name="c-using-return-status"></a>C. Utilisation de l'état de retour  
 Dans l’exemple `xp_cmdshell` suivant, la procédure stockée étendue suggère également l’état de retour. La valeur du code de retour est stockée dans la variable `@result`.  
  
```  
DECLARE @result int;  
EXEC @result = xp_cmdshell 'dir *.exe';  
IF (@result = 0)  
   PRINT 'Success'  
ELSE  
   PRINT 'Failure';  
```  
  
### <a name="d-writing-variable-contents-to-a-file"></a>D. Écriture du contenu des variables dans un fichier  
 Dans l'exemple ci-dessous, le contenu de la variable `@var` est écrit dans un fichier nommé `var_out.txt` dans le répertoire actif sur le serveur.  
  
```  
DECLARE @cmd sysname, @var sysname;  
SET @var = 'Hello world';  
SET @cmd = 'echo ' + @var + ' > var_out.txt';  
EXEC master..xp_cmdshell @cmd;  
```  
  
### <a name="e-capturing-the-result-of-a-command-to-a-file"></a>E. Capture du résultat d’une commande dans un fichier  
 Dans l'exemple ci-dessous, le contenu du répertoire actif est écrit dans un fichier nommé `dir_out.txt` dans le répertoire actif du serveur.  
  
```  
DECLARE @cmd sysname, @var sysname;  
SET @var = 'dir/p';  
SET @cmd = @var + ' > dir_out.txt';  
EXEC master..xp_cmdshell @cmd;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures de stockage étendues générales &#40;&#41;transact-SQL](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)   
 [option de configuration de serveur xp_cmdshell](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)   
 [Configuration de surface](../../relational-databases/security/surface-area-configuration.md)   
 [sp_xp_cmdshell_proxy_account &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-xp-cmdshell-proxy-account-transact-sql.md)  
  
  

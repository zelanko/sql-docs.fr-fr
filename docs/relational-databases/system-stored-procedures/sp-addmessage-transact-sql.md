---
title: sp_addmessage (Transact-SQL) Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addmessage
- sp_addmessage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addmessage
ms.assetid: 54746d30-f944-40e5-a707-f2d9be0fb9eb
author: stevestein
ms.author: sstein
ms.openlocfilehash: d040fa0ccfe9b962f8847db0a841b95a534326fa
ms.sourcegitcommit: 1124b91a3b1a3d30424ae0fec04cfaa4b1f361b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80531033"
---
# <a name="sp_addmessage-transact-sql"></a>sp_addmessage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Stocke un nouveau message d’erreur [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]défini par l’utilisateur dans un cas de . Les messages stockés à l’aide **de sp_addmessage** peuvent être consultés en utilisant la vue du catalogue **sys.messages.**  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addmessage [ @msgnum= ] msg_id , [ @severity= ] severity , [ @msgtext= ] 'msg'   
     [ , [ @lang= ] 'language' ]   
     [ , [ @with_log= ] { 'TRUE' | 'FALSE' } ]   
     [ , [ @replace= ] 'replace' ]   
```  
  
## <a name="arguments"></a>Arguments  
`[ @msgnum = ] msg_id`Est l’id du message. *msg_id* est **int** avec un défaut de NULL. *msg_id* pour les messages d’erreur définis par l’utilisateur peut être un integer entre 50 001 et 2 147 483 647. La combinaison de *msg_id* et de *la langue* doit être unique; une erreur est retournée si l’ID existe déjà pour la langue spécifiée.  
  
`[ @severity = ]severity`Est-ce le niveau de gravité de l’erreur. *la sévérité* est **smallint** avec un défaut de NULL. Les niveaux valides vont de 1 à 25. Pour plus d’informations sur les niveaux de gravité, consultez [Niveaux de gravité des erreurs du moteur de base de données](../../relational-databases/errors-events/database-engine-error-severities.md).  
  
`[ @msgtext = ] 'msg'`Est-ce le texte du message d’erreur. *msg* est **nvarchar(255)** avec un défaut de NULL.  
  
`[ @lang = ] 'language'`Est-ce la langue de ce message. *la langue* est **sysname** avec un défaut de NULL. Étant donné que plusieurs langues peuvent être installées sur le même serveur, la *langue* spécifie la langue dans laquelle chaque message est écrit. Lorsque *la langue* est omise, la langue est la langue par défaut pour la session.  
  
`[ @with_log = ] { 'TRUE' | 'FALSE' }`Est de savoir si le message doit être écrit sur le journal de l’application Windows quand il se produit. with_log est **varchar(5)** avec un défaut de FALSE. ** \@** Si sa valeur est TRUE, l'erreur est automatiquement écrite dans le journal des applications Windows. Si sa valeur est FALSE, l'erreur n'est pas automatiquement écrite dans le journal des applications Windows ; c'est la façon dont elle a été déclenchée qui détermine si l'erreur sera ou non écrite dans le journal. Seuls les membres du rôle du serveur **sysadmin** peuvent utiliser cette option.  
  
> [!NOTE]  
>  Si un message est écrit au journal d’application [!INCLUDE[ssDE](../../includes/ssde-md.md)] Windows, il est également écrit au fichier de journal d’erreur.  
  
`[ @replace = ] 'replace'`Si spécifié comme la chaîne *remplace,* un message d’erreur existant est écrasé par un nouveau texte de message et le niveau de gravité. *remplacer* est **varchar(7)** par un défaut de NULL. Cette option doit être spécifiée si *msg_id* existe déjà. Si vous remplacez un message en anglais américain, le niveau de gravité est remplacé pour tous les messages dans toutes les autres langues qui ont la même *msg_id*.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 Pour les versions non anglaises de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la version anglaise d'un message doit exister préalablement à l'ajout d'un message dans une autre langue. Le degré de gravité des deux versions du message doit correspondre.  
  
 Lors de la localisation des messages qui contiennent des paramètres, utilisez les numéros de paramètres correspondant aux paramètres des messages d'origine. Insérez un point d'exclamation (!) après chaque numéro de paramètre.  
  
|Message d'origine|Message localisé|  
|----------------------|-----------------------|  
|''Message d'origine param 1 : %s,<br /><br /> param 2 : %d'|''Message localisé param 1 : %1!,<br /><br /> param 2 : %2!'|  
  
 La syntaxe pouvant différer d'une langue à l'autre, il se peut que les numéros de paramètres apparaissent dans un ordre différent par rapport au message d'origine.  
  
## <a name="permissions"></a>Autorisations  
Nécessite l’adhésion aux rôles de serveur fixe **sysadmin** ou **serveradmin.**  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-defining-a-custom-message"></a>R. Définition d'un message personnalisé  
 L’exemple suivant ajoute un message personnalisé à **sys.messages**.  
  
```  
USE master;  
GO  
EXEC sp_addmessage 50001, 16,   
   N'Percentage expects a value between 20 and 100.   
   Please reexecute with a more appropriate value.';  
GO  
```  
  
### <a name="b-adding-a-message-in-two-languages"></a>B. Ajout d'un message en deux langues  
 L'exemple suivant ajoute d'abord un message en anglais, puis ajoute ce même message en français`.`  
  
```  
USE master;  
GO  
EXEC sp_addmessage @msgnum = 60000, @severity = 16,   
   @msgtext = N'The item named %s already exists in %s.',   
   @lang = 'us_english';  
  
EXEC sp_addmessage @msgnum = 60000, @severity = 16,   
   @msgtext = N'L''élément nommé %1! existe déjà dans %2!',   
   @lang = 'French';  
GO  
```  
  
### <a name="c-changing-the-order-of-parameters"></a>C. Modification de l'ordre des paramètres  
 L'exemple suivant ajoute d'abord un message en anglais, puis un message localisé dans lequel l'ordre des paramètres est modifié.  
  
```  
USE master;  
GO  
  
EXEC sp_addmessage   
    @msgnum = 60000,   
    @severity = 16,  
    @msgtext =   
        N'This is a test message with one numeric  
        parameter (%d), one string parameter (%s),   
        and another string parameter (%s).',  
    @lang = 'us_english';  
  
EXEC sp_addmessage   
    @msgnum = 60000,   
    @severity = 16,  
    @msgtext =   
        -- In the localized version of the message,  
        -- the parameter order has changed. The   
        -- string parameters are first and second  
        -- place in the message, and the numeric   
        -- parameter is third place.  
        N'Dies ist eine Testmeldung mit einem   
        Zeichenfolgenparameter (%3!),  
        einem weiteren Zeichenfolgenparameter (%2!),   
        und einem numerischen Parameter (%1!).',  
    @lang = 'German';  
GO    
  
-- Changing the session language to use the U.S. English  
-- version of the error message.  
SET LANGUAGE us_english;  
GO  
  
RAISERROR(60000,1,1,15,'param1','param2') -- error, severity, state,  
GO                                       -- parameters.  
  
-- Changing the session language to use the German  
-- version of the error message.  
SET LANGUAGE German;  
GO  
  
RAISERROR(60000,1,1,15,'param1','param2'); -- error, severity, state,   
GO                                       -- parameters.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [sp_altermessage &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [sp_dropmessage &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/sp-dropmessage-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

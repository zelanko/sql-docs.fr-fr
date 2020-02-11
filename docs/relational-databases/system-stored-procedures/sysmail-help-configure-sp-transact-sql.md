---
title: sysmail_help_configure_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_help_configure_sp
- sysmail_help_configure_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_help_configure_sp
ms.assetid: e598d4c8-3041-4965-b046-dce3a8e3d3e0
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3d07f77c468bb14b28cd003f599bebd636d6f862
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74056163"
---
# <a name="sysmail_help_configure_sp-transact-sql"></a>sysmail_help_configure_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche les paramètres de configuration pour la messagerie de base de données.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_help_configure_sp  [ [ @parameter_name = ] 'parameter_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @parameter_name = ] 'parameter_name'`Nom du paramètre de configuration à récupérer. Lorsqu’il est spécifié, la valeur du paramètre de configuration est retournée dans le ** \@** paramètre de sortie parameter_value. Quand aucun ** \@parameter_name** n’est spécifié, cette procédure stockée retourne un jeu de résultats contenant tous les paramètres de configuration Database mail de l’instance.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Quand aucun ** \@parameter_name** n’est spécifié, retourne un jeu de résultats avec les colonnes suivantes.  
  
||||  
|-|-|-|  
|Nom de la colonne|Type de données|Description|  
|**paramName**|**nvarchar (256)**|Nom du paramètre de configuration.|  
|**valeur paramValue**|**nvarchar (256)**|Valeur du paramètre de configuration.|  
|**description**|**nvarchar (256)**|Description du paramètre de configuration.|  
  
## <a name="remarks"></a>Notes  
 La procédure stockée **sysmail_help_configure_sp** répertorie les paramètres de configuration de Database mail actuels pour l’instance.  
  
 Lorsqu’un ** \@parameter_name** est spécifié, mais qu’aucun paramètre de sortie n’est fourni pour ** \@parameter_value**, cette procédure stockée ne produit aucune sortie.  
  
 La procédure stockée **sysmail_help_configure_sp** se trouve dans la base de données **msdb** et appartient au schéma **dbo** . La procédure doit être appelée avec un nom en trois parties si la base de données active n’est pas **msdb**.  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d’exécution pour cette procédure sont octroyées par défaut aux membres du rôle serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant montre la liste des paramètres de configuration de la messagerie de base de données pour l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
EXECUTE msdb.dbo.sysmail_help_configure_sp ;  
```  
  
 Voici un exemple d'ensemble de résultats, modifié pour la longueur de ligne :  
  
```  
paramname                       paramvalue      description  
------------------------------- --------------- -----------------------------------------------------------------------------  
AccountRetryAttempts            1               Number of retry attempts for a mail server  
AccountRetryDelay               5000            Delay between each retry attempt to mail server  
DatabaseMailExeMinimumLifeTime  600             Minimum process lifetime in seconds  
DefaultAttachmentEncoding       MIME            Default attachment encoding  
LoggingLevel                    2               Database Mail logging level: normal - 1, extended - 2 (default), verbose - 3  
MaxFileSize                     1000000         Default maximum file size  
ProhibitedExtensions            exe,dll,vbs,js  Extensions not allowed in outgoing mails  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)   
 [Database Mail des procédures stockées &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  

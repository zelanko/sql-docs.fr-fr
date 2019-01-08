---
title: sysmail_configure_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_configure_sp_TSQL
- sysmail_configure_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_configure_sp
ms.assetid: 73b33c56-2bff-446a-b495-ae198ad74db1
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: abe47df497b61d35c66bfebfb3ba5a75fad0e183
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53588553"
---
# <a name="sysmailconfiguresp-transact-sql"></a>sysmail_configure_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les paramètres de configuration de la messagerie de base de données. Les paramètres de configuration spécifiés avec **sysmail_configure_sp** s’appliquent à l’intégralité [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_configure_sp [ [ @parameter_name = ] 'parameter_name' ]  
    [ , [ @parameter_value = ] 'parameter_value' ]  
    [ , [ @description = ] 'description' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [**@parameter_name** =] **'**_nom_paramètre_**'**  
 Nom du paramètre à modifier.  
  
 [**@parameter_value** =] **'**_parameter_value_**'**  
 Nouvelle valeur du paramètre.  
  
 [**@description** =] **'**_description_**'**  
 Description du paramètre.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 La messagerie de base de données utilise les paramètres suivants :  
  
||||  
|-|-|-|  
|Nom du paramètre|Description|Valeur par défaut|  
|*AccountRetryAttempts*|Nombre de fois où le processus de messagerie externe tente d'envoyer le message électronique à l'aide de chaque compte présent dans le profil spécifié.|**1**|  
|*AccountRetryDelay*|Quantité de temps, en secondes, d'attente du processus de messagerie externe entre chaque tentative d'envoi d'un message.|**5000**|  
|*DatabaseMailExeMinimumLifeTime*|Durée minimale (en secondes) pendant laquelle le processus de messagerie externe reste actif. Lorsque la messagerie de base de données envoie un nombre important de messages, augmentez cette valeur afin de conserver cette messagerie de base de données active et d'éviter la charge de gestion engendrée par des démarrages et arrêts fréquents.|**600**|  
|*DefaultAttachmentEncoding*|Encodage par défaut pour les pièces jointes de messagerie électronique.|MIME|  
|*MaxFileSize*|Taille maximale d'une pièce jointe, en octets.|**1000000**|  
|*ProhibitedExtensions*|Liste séparée par des virgules des extensions qui ne peuvent pas être envoyées en pièces jointes dans un message électronique.|**exe, dll, vbs, js**|  
|*LoggingLevel*|Spécifiez quels messages sont enregistrés dans le journal de la messagerie de base de données. L’une des valeurs numériques suivantes :<br /><br /> 1 - Mode normal. Seules les erreurs sont consignées dans le journal.<br /><br /> 2 - Mode étendu. Les erreurs, les avertissements et les messages à contenu informatif sont consignés dans le journal.<br /><br /> 3 - Mode documenté. Les erreurs, les avertissements, les messages informatifs et de réussite ainsi que d'autres messages internes sont consignés dans le journal. Utilisez ce mode lorsque vous tentez de résoudre des problèmes.|**2**|  
  
 La procédure stockée **sysmail_configure_sp** est dans le **msdb** de base de données et est détenue par le **dbo** schéma. La procédure doit être exécutée avec un nom en trois parties si la base de données actuelle n’est pas **msdb**.  
  
## <a name="permissions"></a>Autorisations  
 Autorisations d’exécution de cette procédure reviennent par défaut aux membres de la **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 **A. Paramétrage de la messagerie de base de données pour réessayer chaque compte 10 fois**  
  
 L'exemple suivant illustre le paramétrage de la base de données de messagerie afin de réessayer chaque compte à dix reprises, avant de considérer que le compte est injoignable.  
  
```  
EXECUTE msdb.dbo.sysmail_configure_sp  
    'AccountRetryAttempts', '10' ;  
```  
  
 **B. Définition de la taille de pièce jointe maximale à deux mégaoctets**  
  
 L'exemple suivant illustre le paramétrage de la taille de pièce jointe maximale à 2 mégaoctets.  
  
```  
EXECUTE msdb.dbo.sysmail_configure_sp  
    'MaxFileSize', '2097152' ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)   
 [sysmail_help_configure_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-help-configure-sp-transact-sql.md)   
 [Procédures stockées de messagerie de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  

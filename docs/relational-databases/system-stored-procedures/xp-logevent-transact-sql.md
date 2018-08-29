---
title: xp_logevent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- xp_logevent
- xp_logevent_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- xp_logevent
ms.assetid: 7b379ad0-5b12-4d2e-9c52-62465df1fdbd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 41755783a955b5980d6e52e2a3362258d4a7ec42
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43036497"
---
# <a name="xplogevent-transact-sql"></a>xp_logevent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Enregistre un message défini par l’utilisateur dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fichier journal et dans l’Observateur d’événements Windows. xp_logevent peut être utilisé pour envoyer une alerte sans envoyer de message au client.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
xp_logevent { error_number , 'message' } [ , 'severity' ]  
```  
  
## <a name="arguments"></a>Arguments  
 *error_number*  
 Numéro d'erreur défini par l'utilisateur, supérieur à 50000. La valeur maximale est 2147483647 (2^31 - 1).  
  
 **«** *message* **»**  
 Chaîne de caractères d'une longueur maximale de 2048 caractères.  
  
 **«** *gravité* **»**  
 Une des trois chaînes de caractères INFORMATIONAL, WARNING ou ERROR. *gravité* est facultatif, avec INFORMATIONAL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 xp_logevent retourne ce message d'erreur pour l'exemple de code ci-dessous :  
  
 `The command(s) completed successfully.`  
  
## <a name="remarks"></a>Notes  
 Lorsque vous envoyez des messages à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)] procédures, déclencheurs, lots et ainsi de suite, utilisent l’instruction RAISERROR au lieu de xp_logevent. xp_logevent ne pas appeler un gestionnaire de messages d’un client ou@ERROR. Pour écrire des messages dans l'Observateur d'événements Windows et dans le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], exécutez l'instruction RAISERROR.  
  
## <a name="permissions"></a>Permissions  
 Il faut appartenir au rôle de base de données fixe db_owner de la base de données master ou au rôle serveur fixe sysadmin.  
  
## <a name="examples"></a>Exemples  
 Cet exemple enregistre le message dans l'Observateur d'événements Windows et transmet les variables au message.  
  
```  
DECLARE @@TABNAME varchar(30), @@USERNAME varchar(30), @@MESSAGE varchar(255);  
SET @@TABNAME = 'customers';  
SET @@USERNAME = USER_NAME();  
SELECT @@MESSAGE = 'The table ' + @@TABNAME + ' is not owned by the user   
   ' + @@USERNAME + '.';  
  
USE master;  
EXEC xp_logevent 60000, @@MESSAGE, informational;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [PRINT &#40;Transact-SQL&#41;](../../t-sql/language-elements/print-transact-sql.md)   
 [RAISERROR &#40;Transact-SQL&#41;](../../t-sql/language-elements/raiserror-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées étendues générales &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)  
  
  

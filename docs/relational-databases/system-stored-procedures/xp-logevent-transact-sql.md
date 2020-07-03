---
title: xp_logevent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
ms.openlocfilehash: 08fbf39390a7a81fc3ce3e8563c3699ba77b833c
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890764"
---
# <a name="xp_logevent-transact-sql"></a>xp_logevent (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Enregistre un message défini par l’utilisateur dans le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fichier journal et dans le observateur d’événements Windows. xp_logevent peut être utilisé pour envoyer une alerte sans envoyer de message au client.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 Une des trois chaînes de caractères INFORMATIONAL, WARNING ou ERROR. *Severity* est facultatif, avec Informational comme valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 xp_logevent retourne ce message d'erreur pour l'exemple de code ci-dessous :  
  
 `The command(s) completed successfully.`  
  
## <a name="remarks"></a>Remarques  
 Lorsque vous envoyez des messages à partir de [!INCLUDE[tsql](../../includes/tsql-md.md)] procédures, de déclencheurs, de lots, etc., utilisez l’instruction RAISERROR au lieu de xp_logevent. xp_logevent n’appelle pas de gestionnaire de messages d’un client ou de Set @ @ERROR . Pour écrire des messages dans l'Observateur d'événements Windows et dans le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], exécutez l'instruction RAISERROR.  
  
## <a name="permissions"></a>Autorisations  
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
 [Procédures stockées système &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Procédures stockées étendues générales &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/general-extended-stored-procedures-transact-sql.md)  
  
  

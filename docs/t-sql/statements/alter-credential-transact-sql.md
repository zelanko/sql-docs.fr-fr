---
title: "Informations d’identification de ALTER (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 08/19/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER CREDENTIAL
- ALTER_CREDENTIAL_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- passwords [SQL Server], credentials
- credentials [SQL Server], ALTER CREDENTIAL statement
- modifying credentials
- authentication [SQL Server], credentials
- ALTER CREDENTIAL statement
ms.assetid: b08899a6-c09e-4af4-91aa-a978ada79264
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d183da3fef3f2802803d4dc9771dbc72e601321a
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="alter-credential-transact-sql"></a>ALTER CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie les propriétés d'une information d'identification.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ALTER CREDENTIAL credential_name WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
```  
  
## <a name="arguments"></a>Arguments  
 *credential_name*  
 Spécifie le nom d'une information d'identification à modifier.  
  
 IDENTITÉ **='***identity_name***'**  
 Spécifie le nom du compte à utiliser lors d'une connexion en dehors du serveur.  
  
 SECRET **='***secret***'**  
 Spécifie le secret requis pour l'authentification sortante. *secret* est facultatif.  
  
## <a name="remarks"></a>Notes  
 Lorsqu’une information d’identification est modifiée, les valeurs des deux *identity_name* et *secret* sont réinitialisés. Si l'argument facultatif SECRET n'est pas spécifié, sa valeur stockée est NULL.  
  
 Le secret est chiffré au moyen de la clé principale du service. Si cette clé est regénérée, le secret est à nouveau chiffré à l'aide de la nouvelle clé principale du service.  
  
 Informations d’identification sont visibles dans le **sys.credentials** affichage catalogue.  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation ALTER ANY CREDENTIAL. Si l'information d'identification est une information d'identification système, l'autorisation CONTROL SERVER est requise.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-changing-the-password-of-a-credential"></a>A. Modification du mot de passe d'une information d'identification  
 Le code exemple suivant modifie le secret stocké dans l'information d'identification nommée `Saddles`. L'information d'identification contient la connexion Windows `RettigB` et son mot de passe. Le nouveau mot de passe est ajouté à l'information d'identification à l'aide de la clause SECRET.  
  
```  
ALTER CREDENTIAL Saddles WITH IDENTITY = 'RettigB',   
    SECRET = 'sdrlk8$40-dksli87nNN8';  
GO  
```  
  
### <a name="b-removing-the-password-from-a-credential"></a>B. Suppression du mot de passe d'une information d'identification  
 Le code exemple suivant supprime le mot de passe de l'information d'identification nommée `Frames`. L'information d'identification contient la connexion Windows `Aboulrus8` et un mot de passe. Après l'exécution de l'instruction, le mot de passe de l'information d'identification a la valeur NULL car l'option SECRET n'est pas spécifiée.  
  
```  
ALTER CREDENTIAL Frames WITH IDENTITY = 'Aboulrus8';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations d’identification &#40; moteur de base de données &#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [SUPPRIMER les informations d’identification &#40; Transact-SQL &#41;](../../t-sql/statements/drop-credential-transact-sql.md)   
 [MODIFIER les informations d’identification inclus dans l’étendue de base de données &#40; Transact-SQL &#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  


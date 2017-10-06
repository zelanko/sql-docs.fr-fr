---
title: SUSER_SNAME (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUSER_SNAME_TSQL
- SUSER_SNAME
dev_langs:
- TSQL
helpviewer_keywords:
- security identification names [SQL Server]
- logins [SQL Server], users
- SIDs [SQL Server]
- SUSER_SNAME function
- users [SQL Server], logins
- logins [SQL Server], names
- IDs [SQL Server], logins
- identification numbers [SQL Server], logins
- names [SQL Server], logins
ms.assetid: 11ec7d86-d429-4004-a436-da25df9f8761
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 35e3429d49940cd863cd04fc336226268ddf61c9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="susersname-transact-sql"></a>SUSER_SNAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne le nom de connexion associé à un numéro d'identification de sécurité (SID).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SUSER_SNAME ( [ server_user_sid ] )   
```  
  
## <a name="arguments"></a>Arguments  
 *server_user_sid*  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 Correspond au numéro facultatif d'identification de sécurité de la connexion. *server_user_sid* est **varbinary(85)**. *server_user_sid* peut être le numéro d’identification de sécurité de n’importe quel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] utilisateur ou groupe Windows. Si *server_user_sid* est ne pas spécifié, les informations relatives à l’utilisateur actuel sont retournées. Si le paramètre contient le mot NULL, retourne NULL.  
  
## <a name="return-types"></a>Types de retour  
 **nvarchar (128)**  
  
## <a name="remarks"></a>Notes  
 La fonction SUSER_SNAME peut être utilisée comme une contrainte DEFAULT dans les fonctions ALTER TABLE ou CREATE TABLE. SUSER_SNAME peut être utilisé dans une liste de sélection, dans une clause WHERE, et dans tous les cas où une expression est autorisée. SUSER_SNAME doit toujours être suivi de parenthèses, même si aucun paramètre n'est spécifié.  
  
 Lorsqu'il est appelé sans argument, SUSER_SNAME retourne le nom du contexte de sécurité actuel. Lorsqu'il est appelé sans argument à l'intérieur d'un traitement qui a changé de contexte en utilisant EXECUTE AS, SUSER_SNAME retourne le nom du contexte qui a fait l'objet d'un emprunt d'identité. Lorsqu'il est appelé à partir d'un contexte faisant l'objet d'un emprunt d'identité, ORIGINAL_LOGIN retourne le nom du contexte d'origine.  
  
## <a name="includesssdsfullincludessssdsfull-mdmd-remarks"></a>Notes concernant [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]  
 SUSER_NAME retourne toujours le nom de connexion pour le contexte de sécurité actuel.  
  
 L'instruction SUSER_SNAME ne prend pas en charge l'exécution en utilisant un contexte de sécurité représenté par la clause EXECUTE AS.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-susersname"></a>A. Utilisation de SUSER_SNAME  
 L'exemple suivant retourne le nom de connexion pour le contexte de sécurité actuel.  
  
```  
SELECT SUSER_SNAME();  
GO  
```  
  
### <a name="b-using-susersname-with-a-windows-user-security-id"></a>B. Utilisation de SUSER_SNAME avec un ID de sécurité utilisateur Windows  
 Cet exemple retourne le nom de connexion associé à un numéro d'identification de sécurité Windows.  
  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SNAME(0x010500000000000515000000a065cf7e784b9b5fe77c87705a2e0000);  
GO  
```  
  
### <a name="c-using-susersname-as-a-default-constraint"></a>C. Utilisation de SUSER_SNAME comme contrainte DEFAULT  
 L'exemple suivant utilise `SUSER_SNAME` comme contrainte `DEFAULT` dans une instruction `CREATE TABLE`.  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE sname_example  
(  
login_sname sysname DEFAULT SUSER_SNAME(),  
employee_id uniqueidentifier DEFAULT NEWID(),  
login_date  datetime DEFAULT GETDATE()  
);   
GO  
INSERT sname_example DEFAULT VALUES;  
GO  
```  
  
### <a name="d-calling-susersname-in-combination-with-execute-as"></a>D. Appel de SUSER_SNAME en combinaison avec EXECUTE AS  
 Cet exemple montre le comportement de SUSER_SNAME lorsqu'il est appelé à partir d'un contexte ayant fait l'objet d'un emprunt d'identité.  
  
**S’applique aux**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SNAME();  
GO  
EXECUTE AS LOGIN = 'WanidaBenShoof';  
SELECT SUSER_SNAME();  
REVERT;  
GO  
SELECT SUSER_SNAME();  
GO  
  
```  
  
 Voici le résultat.  
  
 ```
sa  
WanidaBenShoof  
sa
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-susersname"></a>E. Utilisation de SUSER_SNAME  
 Cet exemple retourne le nom de connexion correspondant au numéro d'identification de sécurité portant la valeur `0x01`.  
  
```  
SELECT SUSER_SNAME(0x01);  
GO  
```  
  
### <a name="f-returning-the-current-login"></a>F. Retour de la connexion actuelle  
 L’exemple suivant retourne le nom de connexion de la connexion actuelle.  
  
```  
SELECT SUSER_SNAME() AS CurrentLogin;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SUSER_SID &#40; Transact-SQL &#41;](../../t-sql/functions/suser-sid-transact-sql.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [EXECUTE AS &#40; Transact-SQL &#41;](../../t-sql/statements/execute-as-transact-sql.md)  
  
  



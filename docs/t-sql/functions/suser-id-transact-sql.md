---
title: SUSER_ID (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUSER_ID_TSQL
- SUSER_ID
dev_langs: TSQL
helpviewer_keywords:
- users [SQL Server], IDs
- logins [SQL Server], IDs
- SUSER_ID function
- IDs [SQL Server], logins
- identification numbers [SQL Server], logins
- user IDs [SQL Server]
ms.assetid: 348911ab-b0b6-4867-aee7-e6f42e053a4a
caps.latest.revision: "22"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e4b00485c741857f1e3438c3e50995886900fe29
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="suserid-transact-sql"></a>SUSER_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le numéro d'identification de la connexion de l'utilisateur.  
  
> [!NOTE]  
>  En commençant par [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], SUSER_ID retourne la valeur répertoriée en tant que **principal_id** dans les **sys.server_principals** vue de catalogue.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SUSER_ID ( [ 'login' ] )   
```  
  
## <a name="arguments"></a>Arguments  
 **'** *connexion* **'**  
 Nom de connexion de l'utilisateur. *connexion* est **nchar**. Si *connexion* est spécifié en tant que **char**, *connexion* est implicitement converti en **nchar**. *connexion* peut être [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion ou utilisateur ou groupe Windows qui a l’autorisation de se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si *connexion* est ne pas spécifié, le numéro d’identification pour l’utilisateur actuel est retourné. Si le paramètre contient le mot NULL, retourne NULL.  
  
## <a name="return-types"></a>Types de retour  
 **int**  
  
## <a name="remarks"></a>Notes  
 SUSER_ID retourne un numéro d'identification uniquement pour les connexions qui ont été explicitement prévues dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cet ID est utilisé dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour assurer le suivi de la propriété et des autorisations. Il n'est pas équivalent à l'identificateur de sécurité (SID) de la connexion retourné par SUSER_SID. Si *connexion* est un compte de connexion SQL Server, le SID est mappé à un GUID. Si *connexion* est une connexion Windows ou de groupe Windows, le SID est mappé à un identificateur de sécurité Windows.  
  
 SUSER_SID retourne un numéro SUID uniquement pour une connexion qui a une entrée dans le **syslogins** (table système).  
  
 Les fonctions système sont utilisables dans la liste SELECT, dans la clause WHERE et en tout point où une expression est autorisée. En outre, elles doivent toujours être suivies de parenthèses, même si aucun paramètre n'est spécifié.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne le numéro d'identification pour la connexion `sa`.  
  
```  
SELECT SUSER_ID('sa');  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [SUSER_SID &#40; Transact-SQL &#41;](../../t-sql/functions/suser-sid-transact-sql.md)   
 [Fonctions système &#40; Transact-SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  

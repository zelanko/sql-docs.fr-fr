---
title: SUSER_ID (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUSER_ID_TSQL
- SUSER_ID
dev_langs:
- TSQL
helpviewer_keywords:
- users [SQL Server], IDs
- logins [SQL Server], IDs
- SUSER_ID function
- IDs [SQL Server], logins
- identification numbers [SQL Server], logins
- user IDs [SQL Server]
ms.assetid: 348911ab-b0b6-4867-aee7-e6f42e053a4a
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c66da357e43d1a43b3b97c7047d223751ecbe2ba
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2018
---
# <a name="suserid-transact-sql"></a>SUSER_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Retourne le numéro d'identification de la connexion de l'utilisateur.  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]
  
> [!NOTE]  
>  À compter de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], SUSER_ID renvoie la valeur répertoriée en tant que **principal_id** dans l'affichage catalogue **sys.server_principals**.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SUSER_ID ( [ 'login' ] )   
```  
  
## <a name="arguments"></a>Arguments  
 **'** *login* **'**  
 Nom de connexion de l'utilisateur. *login* est de type **nchar**. Si *login* est spécifié en tant que **char**, *login* est implicitement converti en **nchar**. *login* peut être une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou un utilisateur ou groupe Windows quelconque qui a l'autorisation de se connecter à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si *login* n'est pas spécifié, le numéro d'identification de la connexion de l'utilisateur actuel est renvoyé. Si le paramètre contient le mot NULL, retourne NULL.  
  
## <a name="return-types"></a>Types de retour  
 **Int**  
  
## <a name="remarks"></a>Notes   
 SUSER_ID retourne un numéro d'identification uniquement pour les connexions qui ont été explicitement prévues dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Cet ID est utilisé dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour assurer le suivi de la propriété et des autorisations. Il n'est pas équivalent à l'identificateur de sécurité (SID) de la connexion retourné par SUSER_SID. Si *login* est une connexion SQL Server, le SID est mappé à un identificateur global unique (GUID). Si *login* est une connexion d'utilisateur Windows ou un groupe Windows, le SID est mappé à un identificateur de sécurité Windows.  
  
 SUSER_SID renvoie un numéro SUID uniquement pour une connexion comportant une entrée dans la table système **syslogins**.  
  
 Les fonctions système sont utilisables dans la liste SELECT, dans la clause WHERE et en tout point où une expression est autorisée. En outre, elles doivent toujours être suivies de parenthèses, même si aucun paramètre n'est spécifié.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne le numéro d'identification pour la connexion `sa`.  
  
```  
SELECT SUSER_ID('sa');  
```  
  
## <a name="see-also"></a> Voir aussi  
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [SUSER_SID &#40;Transact-SQL&#41;](../../t-sql/functions/suser-sid-transact-sql.md)   
 [Fonctions système &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  

---
title: LOGINPROPERTY (Transact-SQL) | Documents Microsoft
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
- BadPasswordCount_TSQL
- BadPasswordTime_TSQL
- IsLockedIsMustChange
- PasswordLastSetTime
- LOGINPROPERTY_TSQL
- LockoutTime
- BadPasswordCount
- PasswordHash
- HistoryLengthIsExpired
- LockoutTime_TSQL
- PasswordHash_TSQL
- HistoryLengthIsExpired_TSQL
- PasswordLastSetTime_TSQL
- BadPasswordTime
- IsLockedIsMustChange_TSQL
- LOGINPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- default database
- LOGINPROPERTY function
ms.assetid: b34df777-79b0-49a5-88db-b99998479a5d
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 31cbf502614fb348f35474237009f444ed294384
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="loginproperty-transact-sql"></a>LOGINPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur les paramètres de stratégie de connexion.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
LOGINPROPERTY ( 'login_name' , 'property_name' )  
```  
  
## <a name="arguments"></a>Arguments  
 *login_name*  
 Nom d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour laquelle l'état des propriétés de connexion est retourné.  
  
 *PropertyName*  
 Expression contenant les informations de propriétés à retourner pour le compte de connexion. *PropertyName* peut prendre l’une des valeurs suivantes.  
  
|Valeur| Description|  
|-----------|-----------------|  
|**BadPasswordCount**|Retourne le nombre de tentatives de connexion consécutives effectuées avec un mot de passe incorrect.|  
|**BadPasswordTime**|Retourne l'heure de la dernière tentative de connexion effectuée avec un mot de passe incorrect.|  
|**DaysUntilExpiration**|Retourne le nombre de jours avant l'expiration du mot de passe.|  
|**DefaultDatabase**|Retourne le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données par défaut de connexion stockées dans les métadonnées ou **master** si aucune base de données n’est spécifié. Retourne la valeur NULL non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] configuré les utilisateurs (par exemple, les utilisateurs authentifiés Windows).|  
|**DefaultLanguage**|Retourne la langue par défaut de connexion telle que stockée dans les métadonnées. Retourne la valeur NULL non -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisateurs fournis, par exemple, Windows des utilisateurs authentifiés.|  
|**HistoryLength**|Retourne le nombre de mots de passe faisant l'objet d'un suivi pour le compte de connexion à l'aide du mécanisme d'application des stratégies de mot de passe. Si la valeur est 0, la stratégie de mot de passe n'est pas appliquée. La reprise de l'application de la stratégie du mot de passe redémarre à 1.|  
|**IsExpired**|Indique si le compte de connexion a expiré.|  
|**IsLocked**|Indique si le compte de connexion est verrouillé.|  
|**IsMustChange**|Indique si le compte de connexion doit modifier son mot de passe lors de la prochaine connexion.|  
|**LockoutTime**|Retourne la date à laquelle la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été verrouillée en raison du dépassement du nombre de tentatives de connexion autorisé.|  
|**PasswordHash**|Retourne le hachage du mot de passe.|  
|**PasswordLastSetTime**|Retourne la date à laquelle le mot de passe actuel a été défini.|  
|**PasswordHashAlgorithm**|Retourne l'algorithme utilisé pour hacher le mot de passe.|  
  
## <a name="returns"></a>Valeur renvoyée  
 Le type de données dépend de la valeur demandée.  
  
 **IsLocked**, **IsExpired**, et **IsMustChange** sont de type **int**.  
  
-   1 si la connexion est dotée de l'état spécifié.  
  
-   0 si la connexion n'est pas dotée de l'état spécifié.  
  
 **BadPasswordCount** et **HistoryLength** sont de type **int**.  
  
 **BadPasswordTime**, **LockoutTime**, **PasswordLastSetTime** sont de type **datetime**.  
  
 **PasswordHash** est de type **varbinary**.  
  
 NULL si la connexion n'est pas une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] valide.  
  
 **DaysUntilExpiration** est de type **int**.  
  
-   0 si la connexion a expiré ou si elle expirera le jour de l'interrogation.  
  
-   -1 si la stratégie de sécurité locale dans Windows ne fait jamais expirer le mot de passe.  
  
-   NULL si CHECK_POLICY ou CHECK_EXPIRATION a la valeur OFF pour une connexion, ou si le système d'exploitation ne prend pas en charge la stratégie de mot de passe.  
  
 **PasswordHashAlgorithm** est de type int.  
  
-   0 pour un hachage SQL7.0  
  
-   1 si un hachage SHA-1  
  
-   2 pour un hachage SHA-2  
  
-   NULL si le compte de connexion n'est pas un compte de connexion SQL Server valide.  
  
## <a name="remarks"></a>Notes  
 Cette fonction intégrée retourne des informations sur les paramètres de stratégie de mot de passe d'une connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les noms des propriétés ne sont pas la casse, les noms de propriété, tel que **BadPasswordCount** et **badpasswordcount** sont équivalents. Les valeurs de la **PasswordHash, PasswordHashAlgorithm**, et **PasswordLastSetTime** propriétés sont disponibles sur toutes les configurations prises en charge de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais les autres propriétés sont disponibles uniquement quand [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d’exécution [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] et que CHECK_POLICY et CHECK_EXPIRATION sont activés. Pour plus d'informations, consultez [Password Policy](../../relational-databases/security/password-policy.md).  
  
## <a name="permissions"></a>Permissions  
 Requiert l'autorisation VIEW sur la connexion. Pour la demande du hachage de mot de passe, requiert en outre l'autorisation CONTROL SERVER.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-checking-whether-a-login-must-change-its-password"></a>A. Détermination de la nécessité de modifier le mot de passe d'un compte de connexion  
 L’exemple suivant vérifie si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion `John3` doit modifier son mot de passe la prochaine fois qu’il se connecte à une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
SELECT LOGINPROPERTY('John3', 'IsMustChange');  
GO  
```  
  
### <a name="b-checking-whether-a-login-is-locked-out"></a>B. Vérification du verrouillage d'une connexion  
 L'exemple suivant vérifie si la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `John3` est verrouillée.  
  
```  
SELECT LOGINPROPERTY('John3', 'IsLocked');  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)  
  
  


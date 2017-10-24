---
title: SUSER_NAME (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUSER_NAME
- SUSER_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- security identification names [SQL Server]
- logins [SQL Server], users
- identification names for logins [SQL Server]
- users [SQL Server], logins
- SUSER_NAME function
- logins [SQL Server], names
- names [SQL Server], logins
ms.assetid: ae598d9f-9baa-49b8-b1c1-042854206de4
caps.latest.revision: 29
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a8d4eae9424d5c5cb2dbb2e7851d4e660fa0ba72
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="susername-transact-sql"></a>SUSER_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Retourne le nom d'identification de l'utilisateur pour la connexion.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SUSER_NAME ( [ server_user_id ] )   
```  
  
## <a name="arguments"></a>Arguments  
 *id_utilisateur_serveur*  
 Correspond au numéro d'identification de la connexion de l'utilisateur. *id_utilisateur_serveur*, qui est facultatif, est **int**. *id_utilisateur_serveur* peut être le numéro d’identification de n’importe quel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion ou [!INCLUDE[msCoName](../../includes/msconame-md.md)] utilisateur ou groupe qui a l’autorisation de se connecter à une instance de Windows [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si *id_utilisateur_serveur* est ne pas spécifié, le nom d’identification de l’utilisateur actuel est retourné. Si le paramètre contient le mot NULL, retourne NULL.  
  
## <a name="return-types"></a>Types de retour  
 **nvarchar (128)**  
  
## <a name="remarks"></a>Notes  
 Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0, le numéro d'identification de sécurité (SID, Security Identification Number) remplace le numéro d'identification de l'utilisateur du serveur (SUID, Server User Identification Number).  
  
 SUSER_NAME retourne un nom de connexion uniquement pour une connexion qui a une entrée dans le **syslogins** (table système).  
  
 SUSER_NAME peut être utilisée dans la liste de sélection, au sein d'une clause WHERE et n'importe où une expression est autorisée, et doit toujours être suivie par des parenthèses (même si aucun paramètre n'est indiqué).  
  
## <a name="examples"></a>Exemples  
 Dans l'exemple suivant, la procédure retourne le nom d'identification de la connexion utilisateur `1`.  
  
```  
SELECT SUSER_NAME(1);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SUSER_ID &#40; Transact-SQL &#41;](../../t-sql/functions/suser-id-transact-sql.md)   
 [Principaux &#40;moteur de base de données&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  


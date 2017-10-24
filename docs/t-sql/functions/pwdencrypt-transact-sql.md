---
title: PWDENCRYPT (Transact-SQL) | Documents Microsoft
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
- PWDENCRYPT
- PWDENCRYPT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PWDENCRYPT function [Transact-SQL]
ms.assetid: 333e9a43-1099-4b9b-b941-4b0b016f47f3
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dcae01f4b56e022f3b5966acd33877c851d9ae05
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="pwdencrypt-transact-sql"></a>PWDENCRYPT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le hachage de mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la valeur d'entrée qui utilise la version actuelle de l'algorithme de hachage de mot de passe.  
  
 PWDENCRYPT est une fonction ancienne susceptible de ne plus être prise en charge dans les futures versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilisez [HASHBYTES](../../t-sql/functions/hashbytes-transact-sql.md) à la place. HASHBYTES fournit davantage d'algorithmes de hachage.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PWDENCRYPT ( 'password' )  
```  
  
## <a name="arguments"></a>Arguments  
 *mot de passe*  
 Mot de passe à chiffrer. *mot de passe* est **sysname**.  
  
## <a name="return-types"></a>Types de retour  
 **varbinary(128)**  
  
## <a name="permissions"></a>Permissions  
 PWDENCRYPT est accessible publiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [PWDCOMPARE &#40; Transact-SQL &#41;](../../t-sql/functions/pwdcompare-transact-sql.md)  
  
  


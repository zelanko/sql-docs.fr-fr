---
title: PWDENCRYPT (Transact-SQL) | Microsoft Docs
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
- PWDENCRYPT
- PWDENCRYPT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PWDENCRYPT function [Transact-SQL]
ms.assetid: 333e9a43-1099-4b9b-b941-4b0b016f47f3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 06b080d784d9a8737c1fe524e6634517ca0c97f5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="pwdencrypt-transact-sql"></a>PWDENCRYPT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne le hachage de mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la valeur d'entrée qui utilise la version actuelle de l'algorithme de hachage de mot de passe.  
  
 PWDENCRYPT est une fonction ancienne susceptible de ne plus être prise en charge dans les futures versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilisez [HASHBYTES](../../t-sql/functions/hashbytes-transact-sql.md) à la place. HASHBYTES fournit davantage d'algorithmes de hachage.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PWDENCRYPT ( 'password' )  
```  
  
## <a name="arguments"></a>Arguments  
 *password*  
 Mot de passe à chiffrer. *password* est de type **sysname**.  
  
## <a name="return-types"></a>Types de retour  
 **varbinary(128)**  
  
## <a name="permissions"></a>Autorisations  
 PWDENCRYPT est accessible publiquement.  
  
## <a name="see-also"></a> Voir aussi  
 [Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [PWDCOMPARE &#40;Transact-SQL&#41;](../../t-sql/functions/pwdcompare-transact-sql.md)  
  
  

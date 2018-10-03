---
title: PWDENCRYPT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PWDENCRYPT
- PWDENCRYPT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- PWDENCRYPT function [Transact-SQL]
ms.assetid: 333e9a43-1099-4b9b-b941-4b0b016f47f3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aca4425147998df6679c503436b90e208e22ea16
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47675427"
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
  
## <a name="permissions"></a>Permissions  
 PWDENCRYPT est accessible publiquement.  
  
## <a name="see-also"></a> Voir aussi  
 [Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [PWDCOMPARE &#40;Transact-SQL&#41;](../../t-sql/functions/pwdcompare-transact-sql.md)  
  
  

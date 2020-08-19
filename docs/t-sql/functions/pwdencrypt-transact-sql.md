---
description: PWDENCRYPT (Transact-SQL)
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0b25d123f34de28d64e39e3593f918e01eada30b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88445591"
---
# <a name="pwdencrypt-transact-sql"></a>PWDENCRYPT (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Retourne le hachage de mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la valeur d'entrée qui utilise la version actuelle de l'algorithme de hachage de mot de passe.  
  
 PWDENCRYPT est une fonction ancienne susceptible de ne plus être prise en charge dans les futures versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilisez [HASHBYTES](../../t-sql/functions/hashbytes-transact-sql.md) à la place. HASHBYTES fournit davantage d'algorithmes de hachage.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
PWDENCRYPT ( 'password' )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
 *mot de passe*  
 Mot de passe à chiffrer. *password* est de type **sysname**.  
  
## <a name="return-types"></a>Types de retour  
 **varbinary(128)**  
  
## <a name="permissions"></a>Autorisations  
 PWDENCRYPT est accessible publiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de sécurité &#40;Transact-SQL&#41;](../../t-sql/functions/security-functions-transact-sql.md)   
 [PWDCOMPARE &#40;Transact-SQL&#41;](../../t-sql/functions/pwdcompare-transact-sql.md)  
  
  

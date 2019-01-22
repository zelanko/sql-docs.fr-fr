---
title: DROP SIGNATURE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP SIGNATURE
- DROP_SIGNATURE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting signatures
- dropping signatures
- DROP SIGNATURE statement
- removing signatures
- signatures [SQL Server]
- digital signatures [SQL Server]
ms.assetid: 8a1fd8c5-0e75-4b2f-9d3c-c296bed56cc7
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: a7def68fb093f056569836a3cbdad5f71b3fbd2f
ms.sourcegitcommit: c6e71ed14198da67afd7ba722823b1af9b4f4e6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54327690"
---
# <a name="drop-signature-transact-sql"></a>DROP SIGNATURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Supprime une signature numérique d'une procédure stockée, d'une fonction, d'un déclencheur ou d'un assembly.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP [ COUNTER ] SIGNATURE FROM module_name   
    BY <crypto_list> [ ,...n ]  
  
<crypto_list> ::=  
    CERTIFICATE cert_name  
    | ASYMMETRIC KEY Asym_key_name  
```  
  
## <a name="arguments"></a>Arguments  
 *module_name*  
 Nom d'une procédure stockée, d'une fonction, d'un assembly ou d'un déclencheur.  
  
 CERTIFICATE *cert_name*  
 Nom d'un certificat dont la procédure stockée, la fonction, l'assembly ou le déclencheur porte la signature.  
  
 ASYMMETRIC KEY *Asym_key_name*  
 Nom d'une clé asymétrique dont la procédure stockée, la fonction, l'assembly ou le déclencheur porte la signature.  
  
## <a name="remarks"></a>Notes   
 Des informations sur les signatures sont visibles dans l'affichage catalogue sys.crypt_properties.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'autorisation ALTER sur l'objet et l'autorisation CONTROL sur le certificat ou la clé asymétrique. Si une clé privée associée est protégée par un mot de passe, l'utilisateur doit également disposer de ce mot de passe.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime la signature du certificat `HumanResourcesDP` de la procédure stockée `HumanResources.uspUpdateEmployeeLogin`.  
  
```  
USE AdventureWorks2012;  
DROP SIGNATURE FROM HumanResources.uspUpdateEmployeeLogin   
    BY CERTIFICATE HumanResourcesDP;  
GO  
```  
  
## <a name="see-also"></a> Voir aussi  
 [sys.crypt_properties &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-crypt-properties-transact-sql.md)   
 [ADD SIGNATURE &#40;Transact-SQL&#41;](../../t-sql/statements/add-signature-transact-sql.md)  
  
  

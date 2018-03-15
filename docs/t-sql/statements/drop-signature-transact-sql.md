---
title: DROP SIGNATURE (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e9c58cc536c6ffa929dce2466f8a7c4c27528ba4
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
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
 Des informations sur les signatures sont visibles dans la vue de catalogue sys.crypt_properties.  
  
## <a name="permissions"></a>Autorisations  
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
  
  

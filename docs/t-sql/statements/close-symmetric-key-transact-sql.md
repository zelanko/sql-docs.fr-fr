---
title: "FERMER une clé symétrique (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 05/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CLOSE SYMMETRIC KEY
- CLOSE_SYMMETRIC_KEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- closing symmetric keys
- encryption [SQL Server], symmetric keys
- symmetric keys [SQL Server], closing
- CLOSE SYMMETRIC KEY statement
- cryptography [SQL Server], symmetric keys
ms.assetid: 3b083cbb-3c6a-4f59-8d34-601db1efcc83
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 18a4215cf009ebf89bf6ce709c0517455731c4b5
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="close-symmetric-key-transact-sql"></a>CLOSE SYMMETRIC KEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Ferme une clé symétrique ou ferme toutes les clés symétriques ouvertes pendant la session active.  
  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CLOSE { SYMMETRIC KEY key_name | ALL SYMMETRIC KEYS }  
```  
  
## <a name="arguments"></a>Arguments  
 *Key_name*  
 Nom de la clé symétrique à fermer.  
  
## <a name="remarks"></a>Notes  
 Les clés symétriques ouvertes sont liées à la session et non au contexte de sécurité. Une clé ouverte est disponible tant qu'elle n'a pas été explicitement fermée ou que la session n'a pas été arrêtée. Fermez toutes les clés symétriques se ferme toute clé principale de base de données qui a été ouverte dans la session active à l’aide de la [OPEN MASTER KEY](../../t-sql/statements/open-master-key-transact-sql.md) instruction.  Informations relatives aux clés ouvertes sont visibles dans le [sys.openkeys &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-openkeys-transact-sql.md) affichage catalogue.  
  
## <a name="permissions"></a>Permissions  
 Aucune autorisation explicite n'est requise pour fermer une clé symétrique.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-closing-a-symmetric-key"></a>A. Fermeture d'une clé symétrique  
 L'exemple suivant ferme la clé symétrique `ShippingSymKey04`.  
  
```  
CLOSE SYMMETRIC KEY ShippingSymKey04;  
GO  
```  
  
### <a name="b-closing-all-symmetric-keys"></a>B. Fermeture de toutes les clés symétriques  
 L'exemple suivant ferme toutes les clés symétriques ouvertes dans la session active, mais aussi la clé principale de la base de données qui a été ouverte explicitement.  
  
```  
CLOSE ALL SYMMETRIC KEYS;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [ALTER SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-symmetric-key-transact-sql.md)   
 [OPEN SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/open-symmetric-key-transact-sql.md)   
 [DROP SYMMETRIC KEY &#40; Transact-SQL &#41;](../../t-sql/statements/drop-symmetric-key-transact-sql.md)  
  
  


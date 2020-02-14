---
title: KEY_GUID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Key_GUID_TSQL
- Key_GUID
dev_langs:
- TSQL
helpviewer_keywords:
- symmetric keys [SQL Server], GUIDs
- KEY_GUID function
- GUIDs [SQL Server]
ms.assetid: 9246c7b2-7098-42c4-a222-cbf30267c46a
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 16230302a44ef9c56d3b2ab9ff17de6288ead371
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68109361"
---
# <a name="key_guid-transact-sql"></a>KEY_GUID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne le GUID d'une clé symétrique dans la base de données.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Key_GUID( 'Key_Name' )  
```  
  
## <a name="arguments"></a>Arguments  
 **'** *Key_Name* **'**  
 Nom de la clé symétrique dans la base de données.  
  
## <a name="return-types"></a>Types de retour  
 **uniqueidentifier**  
  
## <a name="remarks"></a>Notes  
 Si une valeur d'identité a été spécifiée lors de la création de la clé, le GUID de celle-ci est un hachage MD5 de cette valeur d'identité. Si aucune valeur d'identité n'a été spécifiée, le serveur a généré le GUID.  
  
 Si la clé est une clé temporaire, son nom doit commencer par un signe dièse (#).  
  
## <a name="permissions"></a>Autorisations  
 Les clés temporaires étant disponibles seulement dans la session où elles sont créées, aucune autorisation n'est nécessaire pour y accéder. Pour accéder à une clé qui n'est pas temporaire, l'appelant a besoin d'une autorisation sur celle-ci, pour laquelle il ne doit pas s'être vu refuser l'autorisation VIEW.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne le GUID d'une clé symétrique appelée `ABerglundKey1`.  
  
```  
SELECT Key_GUID('ABerglundKey1');  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE SYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [sys.symmetric_keys &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-symmetric-keys-transact-sql.md)   
 [sys.key_encryptions &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-key-encryptions-transact-sql.md)  
  
  

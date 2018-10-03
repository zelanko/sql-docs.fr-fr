---
title: Sys.sp_drop_trusted_assembly (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_drop_trusted_assembly_TSQL
- sp_drop_trusted_assembly
- sys.sp_drop_trusted_assembly_TSQL
- sys.sp_drop_trusted_assembly
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_drop_trusted_assembly
ms.assetid: ''
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d49d7cd38edb86fc7cebd28f5e59949066fc2f25
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732017"
---
# <a name="sysspdroptrustedassembly-transact-sql"></a>Sys.sp_drop_trusted_assembly (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Supprime un assembly à partir de la liste des assemblys de confiance sur le serveur.

 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


## <a name="syntax"></a>Syntaxe
```  
sp_drop_trusted_assembly 
    [ @hash = ] 'value'
```  

## <a name="arguments"></a>Arguments

[ @hash =] '*valeur*'  
La valeur de hachage SHA2_512 de l’assembly à supprimer de la liste des assemblys de confiance pour le serveur. Assemblys de confiance peuvent se charger lors de la sécurité clr stricte est activée, même si l’assembly n’est pas signé ou la base de données n’est pas marquée comme digne de confiance.

## <a name="remarks"></a>Notes  

Cette procédure supprime un assembly à partir de [sys.trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md).

## <a name="permissions"></a>Permissions

Nécessite l’appartenance dans le `sysadmin` rôle serveur fixe ou `CONTROL SERVER` autorisation.

## <a name="examples"></a>Exemples  

L’exemple suivant supprime un hachage de l’assembly à partir de la liste des assemblys de confiance pour le serveur.  

```  
EXEC sp_drop_trusted_assembly 
0x8893AD6D78D14EE43DF482E2EAD44123E3A0B684A8873C3F7BF3B5E8D8F09503F3E62370CE742BBC96FE3394477214B84C7C1B0F7A04DCC788FA99C2C09DFCCC; 
```  

## <a name="see-also"></a>Voir aussi  
  [Sys.sp_add_trusted_assembly](sys-sp-add-trusted-assembly-transact-sql.md) [sys.trusted_assemblies](../../relational-databases/system-catalog-views/sys-trusted-assemblies-transact-sql.md) [DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  


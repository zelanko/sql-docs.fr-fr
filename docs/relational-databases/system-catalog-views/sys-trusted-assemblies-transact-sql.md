---
title: sys.trusted_assemblies (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- trusted_assemblies_TSQL
- trusted_assemblies
- sys.trusted_assemblies_TSQL
- sys.trusted_assemblies
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trusted_assemblies
ms.assetid: 
caps.latest.revision: 
author: tmullaney
ms.author: thmullan;rickbyh
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 827e0d356114bf2254ebd265ca7ee29e0a00f595
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="systrustedassemblies-transact-sql"></a>sys.trusted_assemblies (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Contient une ligne pour chaque assembly approuvé pour le serveur.

 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


|Nom de colonne |Type de données | Description |
|--- |--- |--- |
|hachage |varbinary(8000) |SHA2_512 hachage du contenu de l’assembly. |
|description |nvarchar(4000) |Description définie par l’utilisateur facultative de l’assembly. Microsoft recommande d’utiliser le nom canonique qui encode le nom simple numéro de version, culture, clé publique et architecture de l’assembly de confiance. Cette valeur identifie l’assembly sur le côté du common language runtime (CLR) de manière unique et est identique à la valeur clr_name dans sys.assemblies. |
|create_date |datetime2 |Date de que l’assembly a été ajouté à la liste des assemblys de confiance. |
|created_by |nvarchar(128) |Nom de connexion du principal qui a ajouté l’assembly à la liste. |
| | | |


## <a name="remarks"></a>Notes  

Utilisez **devez ajouter sp_add_trusted_assembly** et **devez ajouter sys.trusted_assemblies** ajouter ou supprimer des assemblys à partir de `sys.trusted_assemblies`.

## <a name="see-also"></a>Voir aussi  
  [sys.sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md) [sys.sp_drop_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) [DROP ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  


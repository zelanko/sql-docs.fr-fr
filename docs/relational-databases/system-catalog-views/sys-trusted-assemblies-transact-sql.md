---
title: sys. trusted_assemblies (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql
ms.technology: system-objects
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
ms.assetid: ''
author: VanMSFT
ms.author: vanto
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9682535c82f8a579259993e82560dfe6bc930f93
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68061361"
---
# <a name="systrusted_assemblies-transact-sql"></a>sys.trusted_assemblies (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Contient une ligne pour chaque assembly approuvé pour le serveur.

 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  


|Nom de la colonne |Type de données |Description |
|--- |--- |--- |
|Hachage |varbinary(8000) |SHA2_512 hachage du contenu de l’assembly. |
|description |nvarchar(4000) |Description facultative définie par l’utilisateur de l’assembly. Microsoft recommande d’utiliser le nom canonique qui encode le nom simple, le numéro de version, la culture, la clé publique et l’architecture de l’assembly à approuver. Cette valeur identifie de façon unique l’assembly sur le côté common language runtime (CLR) et est identique à la valeur clr_name dans sys. Assemblies. |
|create_date |datetime2 |Date à laquelle l’assembly a été ajouté à la liste des assemblys approuvés. |
|created_by |nvarchar(128) |Nom de connexion du principal qui a ajouté l’assembly à la liste. |
| | | |


## <a name="remarks"></a>Notes  

Utilisez des **sp_add_trusted_assembly** et devez ajouter **sys. trusted_assemblies** ajouter ou supprimer des assemblys dans `sys.trusted_assemblies`.

## <a name="see-also"></a>Voir aussi  
  [sys. sp_add_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-add-trusted-assembly-transact-sql.md) [sys. sp_drop_trusted_assembly](../../relational-databases/system-stored-procedures/sys-sp-drop-trusted-assembly-transact-sql.md) [Drop assembly &#40;Transact-SQL&#41;](../../t-sql/statements/drop-assembly-transact-sql.md)  
  [sys.assemblies](../../relational-databases/system-catalog-views/sys-assemblies-transact-sql.md)  
  [sys.dm_clr_loaded_assemblies](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)  


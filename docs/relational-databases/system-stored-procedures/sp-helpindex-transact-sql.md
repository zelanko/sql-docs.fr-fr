---
description: sp_helpindex (Transact-SQL)
title: sp_helpindex (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpindex_TSQL
- sp_helpindex
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpindex
ms.assetid: c7f73ba0-ec35-4b10-aa5f-f1487e51fbf7
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: eba692ae14a1632a59c3a56c0f7ac68072dee7eb
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89549597"
---
# <a name="sp_helpindex-transact-sql"></a>sp_helpindex (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Affiche des informations sur les index d'une table ou d'une vue.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpindex [ @objname = ] 'name'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @objname = ] 'name'` Nom qualifié ou non qualifié d’une table ou d’une vue définie par l’utilisateur. Les guillemets ne sont nécessaires que si un nom qualifié de table ou de vue est spécifié. Si un nom qualifié complet (incluant un nom de base de données) est fourni, le nom de base de données doit être celui de la base de données active. *Name* est de type **nvarchar (776)**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**index_name**|**sysname**|Nom de l’index.|  
|**index_description**|**varchar (210)**|Description d'index incluant le groupe de fichiers sur lequel il est situé.|  
|**index_keys**|**nvarchar (2078)**|Colonnes de table ou de vue sur lesquelles est construit l'index.|  
  
 Le nom d'une colonne indexée décroissante apparaît dans l'ensemble de résultats, suivi du signe moins (-) ; une colonne indexée croissante (l'ordre de tri par défaut) apparaît sous son seul nom.  
  
## <a name="remarks"></a>Notes  
 Si des index ont été définis à l’aide de l’option NORECOMPUTE de UPDATE STATISTICs, ces informations sont incluses dans la colonne **index_description** .  
  
 **sp_helpindex** expose uniquement les colonnes d’index ordonnées ; par conséquent, il n’expose pas d’informations sur les index XML ou les index spatiaux.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 Cet exemple donne des informations sur les types des index de la table `Customer`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helpindex N'Sales.Customer';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de base de données des procédures stockées &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)  
  
  

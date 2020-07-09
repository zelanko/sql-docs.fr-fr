---
title: DROP AGGREGATE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_AGGREGATE_TSQL
- DROP AGGREGATE
dev_langs:
- TSQL
helpviewer_keywords:
- aggregate functions [SQL Server], removing
- removing user-defined functions
- dropping user-defined functions
- user-defined functions [CLR integration]
- deleting user-defined functions
- DROP AGGREGATE statement
ms.assetid: 84ffc4e7-c451-4f1f-9a67-7fc3a120e53f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7c96206e70c39d1d69cc30e8f7f464352dbe3522
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85882432"
---
# <a name="drop-aggregate-transact-sql"></a>DROP AGGREGATE (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Supprime une fonction d'agrégation définie par l'utilisateur de la base de données active. Les fonctions d’agrégation définies par l’utilisateur sont créées à l’aide de [CREATE AGGREGATE](../../t-sql/statements/create-aggregate-transact-sql.md).  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
DROP AGGREGATE [ IF EXISTS ] [ schema_name . ] aggregate_name  
```  
  
## <a name="arguments"></a>Arguments  
 *IF EXISTS*  
 **S’applique à**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (de [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] à la [version actuelle](https://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Supprime de manière conditionnelle l’agrégat, uniquement s’il existe déjà.  
  
 *schema_name*  
 Nom du schéma auquel appartient la fonction d'agrégation définie par l'utilisateur.  
  
 *aggregate_name*  
 Nom de la fonction d'agrégation définie par l'utilisateur à supprimer.  
  
## <a name="remarks"></a>Notes  
 DROP AGGREGATE ne s'exécute pas si des vues, fonctions ou procédures stockées créées avec une liaison de schéma référencent la fonction d'agrégation définie par l'utilisateur à supprimer.  
  
## <a name="permissions"></a>Autorisations  
 Pour exécuter DROP AGGREGATE, un utilisateur doit, au minimum, posséder l'autorisation ALTER sur le schéma auquel appartient l'agrégation définie par l'utilisateur ou l'autorisation CONTROL sur l'agrégation.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime l'agrégation `Concatenate`.  
  
```  
DROP AGGREGATE dbo.Concatenate;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE AGGREGATE &#40;Transact-SQL&#41;](../../t-sql/statements/create-aggregate-transact-sql.md)   
 [Créer des agrégats définis par l’utilisateur](../../relational-databases/user-defined-functions/create-user-defined-aggregates.md)  
  
  

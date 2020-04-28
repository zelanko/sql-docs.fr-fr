---
title: Définition des tables et des colonnes UDT | Microsoft Docs
description: Une fois que vous avez inscrit l’assembly qui contient une définition d’UDT, vous pouvez l’utiliser dans une définition de colonne.
ms.custom: ''
ms.date: 12/05/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
helpviewer_keywords:
- user-defined types [CLR integration], columns
- UDTs [CLR integration], columns
- columns [CLR integration]
- user-defined types [CLR integration], tables
- tables [CLR integration]
- UDTs [CLR integration], tables
- UDTs [CLR integration], indexes
- user-defined types [CLR integration], indexes
- indexes [CLR integration]
ms.assetid: aea495f4-ce26-4952-b019-38f012625f3f
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f46ebc5089a4cb2fdb974df52d9bc876f925da4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81486890"
---
# <a name="working-with-user-defined-types---defining-udt-tables-and-columns"></a>Utilisation de types définis par l’utilisateur - Définition de tables et de colonnes UDT
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Une fois que l’assembly contenant la définition de type défini par l’utilisateur (UDT) [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été enregistré dans une base de données, il peut être utilisé dans une définition de colonne. Pour plus d’informations, consultez [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md).  
  
## <a name="creating-tables-with-udts"></a>Création de tables avec UDT  
 Il n'existe aucune syntaxe particulière pour la création d'une colonne UDT dans une table. Vous pouvez utiliser le nom de l'UDT dans une définition de colonne comme s'il correspondait à l'un des types de données intrinsèques de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L’instruction CREATE TABLE [!INCLUDE[tsql](../../includes/tsql-md.md)] suivante crée une table nommée **points**, avec une colonne nommée **ID,** qui est définie comme une colonne d’identité **int** et la clé primaire pour la table. La deuxième colonne est nommée **PointValue**, avec un type de données **point**. Le nom de schéma utilisé dans cet exemple est **dbo**. Notez que vous devez disposer des autorisations nécessaires pour spécifier un nom de schéma. Si vous omettez le nom de schéma, le schéma par défaut de l'utilisateur de base de données est utilisé.  
  
```sql  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a>Création d'index sur des colonnes UDT  
 Il existe deux options pour indexer une colonne UDT :  
  
-   **Indexez la valeur complète.** Dans ce cas, si le type défini par l'utilisateur est ordonné binaire, vous pouvez créer un index sur la colonne UDT tout entière en utilisant l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX.  
  
-   **Indexez des expressions UDT.** Vous pouvez créer des index dans des colonnes calculées persistantes sur des expressions UDT. L'expression UDT peut être un champ, une méthode ou une propriété d'un UDT. L'expression doit être déterministe et ne doit pas accéder aux données.  
  
 Pour plus d’informations, consultez [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de types définis par l’utilisateur dans SQL Server](../../relational-databases/clr-integration-database-objects-user-defined-types/working-with-user-defined-types-in-sql-server.md)     
 [CREATe TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md)     
 [Types CLR définis par l'utilisateur](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)     

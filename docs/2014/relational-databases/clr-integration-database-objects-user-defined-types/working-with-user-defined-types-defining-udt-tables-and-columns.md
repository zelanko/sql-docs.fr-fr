---
title: Définition des tables et des colonnes UDT | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: aa9596629ed8b4877b1793fa0c56956c52989499
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84954549"
---
# <a name="defining-udt-tables-and-columns"></a>Définition de tables et de colonnes UDT
  Une fois que l’assembly contenant la définition de type défini par l’utilisateur (UDT) a été enregistré dans une [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données, il peut être utilisé dans une définition de colonne.  
  
## <a name="creating-tables-with-udts"></a>Création de tables avec UDT  
 Il n'existe aucune syntaxe particulière pour la création d'une colonne UDT dans une table. Vous pouvez utiliser le nom de l'UDT dans une définition de colonne comme s'il correspondait à l'un des types de données intrinsèques de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. L’instruction CREATE TABLE suivante [!INCLUDE[tsql](../../includes/tsql-md.md)] crée une table nommée **points**, avec une colonne nommée **ID,** qui est définie comme une `int` colonne d’identité et la clé primaire de la table. La deuxième colonne est nommée **PointValue**, avec un type de données **point**. Le nom de schéma utilisé dans cet exemple est **dbo**. Notez que vous devez disposer des autorisations nécessaires pour spécifier un nom de schéma. Si vous omettez le nom de schéma, le schéma par défaut de l'utilisateur de base de données est utilisé.  
  
```  
CREATE TABLE dbo.Points   
(ID int IDENTITY(1,1) PRIMARY KEY, PointValue Point)  
```  
  
## <a name="creating-indexes-on-udt-columns"></a>Création d'index sur des colonnes UDT  
 Il existe deux options pour indexer une colonne UDT :  
  
-   Indexez la valeur complète. Dans ce cas, si le type défini par l'utilisateur est ordonné binaire, vous pouvez créer un index sur la colonne UDT tout entière en utilisant l'instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX.  
  
-   Indexez des expressions UDT. Vous pouvez créer des index dans des colonnes calculées persistantes sur des expressions UDT. L'expression UDT peut être un champ, une méthode ou une propriété d'un UDT. L'expression doit être déterministe et ne doit pas accéder aux données.  
  
 Pour plus d’informations, consultez [types CLR définis par l’utilisateur](clr-user-defined-types.md) et [create index &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de types définis par l'utilisateur dans SQL Server](working-with-user-defined-types-in-sql-server.md)  
  
  

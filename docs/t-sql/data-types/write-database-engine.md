---
title: "Write (moteur de base de données) | Documents Microsoft"
ms.custom: 
ms.date: 7/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Write_TSQL
- Write
dev_langs:
- TSQL
helpviewer_keywords:
- Write [Database Engine]
ms.assetid: 7c554334-d2d9-4eae-a4ae-097aa4020e1a
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 60707b57671c2ad607bd85b0fedececccd478038
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="write-database-engine"></a>Write (moteur de base de données)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Écrit une représentation binaire de d’écriture **SqlHierarchyId** dans le passé **BinaryWriter**. L’écriture ne peut pas être appelée à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Utilisez plutôt CAST ou CONVERT.
  
## <a name="syntax"></a>Syntaxe  
  
```sql
void Write( BinaryWriter w )   
```  
  
## <a name="arguments"></a>Arguments  
*w*  
A **BinaryWriter** objet auquel la représentation binaire de ce **hierarchyid** nœud sera écrite.
  
## <a name="return-types"></a>Types de retour  
**CLR de type de retour : void**
  
## <a name="remarks"></a>Notes  
Écriture est utilisée en interne par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lorsqu’il est nécessaire, comme lors du chargement des données d’une **hierarchyid** colonne. Écriture est également appelée en interne lorsqu’une conversion est effectuée entre **hierarchyid** et **varbinary**.
  
## <a name="examples"></a>Exemples  
  
```sql
MemoryStream stream = new MemoryStream();  
BinaryWriter bw = new BinaryWriter(stream);  
hid.Write(bw);  
byte[] encoding = stream.ToArray();  
  
```  
  
## <a name="see-also"></a>Voir aussi
[Lecture &#40; moteur de base de données &#41;](../../t-sql/data-types/read-database-engine.md)  
[ToString &#40; moteur de base de données &#41;](../../t-sql/data-types/tostring-database-engine.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Référence de méthodes de type de données hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  


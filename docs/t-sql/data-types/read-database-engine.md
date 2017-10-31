---
title: "Lecture (moteur de base de données) | Documents Microsoft"
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Read_TSQL
- Read
dev_langs:
- TSQL
helpviewer_keywords:
- Read [Database Engine]
ms.assetid: f2b8207c-b69f-4327-a874-100b3a1f27d8
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 21f27c627a36f747d9e3ecbb52d14d1ac6bc5d28
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="read-database-engine"></a>Read (moteur de base de données)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Lecture lit la représentation binaire de **SqlHierarchyId** à partir du passé **BinaryReader** et définit les **SqlHierarchyId** objet à cette valeur. En lecture ne peut pas être appelée à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Utilisez plutôt CAST ou CONVERT.
  
## <a name="syntax"></a>Syntaxe  
  
```sql
void Read( BinaryReader r )   
```  
  
## <a name="arguments"></a>Arguments  
*r*  
 Le **BinaryReader** objet qui produit un flux binaire correspondant à une représentation binaire d’un **hierarchyid** nœud.  
  
## <a name="return-types"></a>Types de retour
 **CLR de type de retour : void**  
  
## <a name="remarks"></a>Notes  
 En lecture ne valide pas son entrée. Si une entrée binaire non valide est fournie, en lecture peut lever une exception. Ou, elle peut réussir et produire un non valide **SqlHierarchyId** objet dont les méthodes peuvent donner des résultats imprévisibles ou lever une exception.  
  
 Lecture peut uniquement être appelée sur un nouvellement créé **SqlHierarchyId** objet.  
  
 Lecture est utilisé en interne par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lorsqu’il est nécessaire, comme lors de l’écriture de données à **hierarchyid** colonne. En lecture est également appelée en interne lorsqu’une conversion est effectuée entre **varbinary** et **hierarchyid**.  
  
## <a name="examples"></a>Exemples  
  
```sql
Byte[] encoding = new byte[] { 0x58 };  
MemoryStream stream = new MemoryStream(encoding, false /*not writable*/);  
BinaryReader br = new BinaryReader(stream);  
SqlHierarchyId hid = new SqlHierarchyId();  
hid.Read(br);   
```  
  
## <a name="see-also"></a>Voir aussi  
[Écriture &#40; moteur de base de données &#41;](../../t-sql/data-types/write-database-engine.md)  
[ToString &#40; moteur de base de données &#41;](../../t-sql/data-types/tostring-database-engine.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Référence de méthodes de type de données hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  


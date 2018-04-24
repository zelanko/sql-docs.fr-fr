---
title: Write (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 7/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|data-types
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 984f54540aa43c238a2139ca4d40c7ee1f9b76b2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="write-database-engine"></a>Write (moteur de base de données)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Write écrit une représentation binaire de **SqlHierarchyId** dans le **BinaryWriter** passé. Write ne peut pas être appelée au moyen de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Utilisez plutôt CAST ou CONVERT.
  
## <a name="syntax"></a>Syntaxe  
  
```sql
void Write( BinaryWriter w )   
```  
  
## <a name="arguments"></a>Arguments  
*w*  
Objet **BinaryWriter** dans lequel la représentation binaire de ce nœud **hierarchyid** sera écrite.
  
## <a name="return-types"></a>Types de retour  
**Type de retour CLR : void**
  
## <a name="remarks"></a>Notes   
Write est utilisée en interne par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cas de nécessité, par exemple lors du chargement de données à partir d’une colonne **hierarchyid**. Write est également appelée en interne quand une conversion est effectuée entre **hierarchyid** et **varbinary**.
  
## <a name="examples"></a>Exemples  
  
```sql
MemoryStream stream = new MemoryStream();  
BinaryWriter bw = new BinaryWriter(stream);  
hid.Write(bw);  
byte[] encoding = stream.ToArray();  
  
```  
  
## <a name="see-also"></a>Voir aussi
[Read &#40;moteur de base de données&#41;](../../t-sql/data-types/read-database-engine.md)  
[ToString &#40;moteur de base de données&#41;](../../t-sql/data-types/tostring-database-engine.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Référence de méthodes de type de données hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  

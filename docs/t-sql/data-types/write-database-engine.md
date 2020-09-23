---
description: Write (moteur de base de données)
title: Write (moteur de base de données) | Microsoft Docs
ms.custom: ''
ms.date: 07/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Write_TSQL
- Write
dev_langs:
- TSQL
helpviewer_keywords:
- Write [Database Engine]
ms.assetid: 7c554334-d2d9-4eae-a4ae-097aa4020e1a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f62ec1073df44ff755277e60bd61906c25ed4723
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91116125"
---
# <a name="write-database-engine"></a>Write (moteur de base de données)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Write écrit une représentation binaire de **SqlHierarchyId** dans le **BinaryWriter** passé. Write ne peut pas être appelée au moyen de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Utilisez plutôt CAST ou CONVERT.
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
void Write( BinaryWriter w )
```  

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
*w*  
Objet **BinaryWriter** dans lequel la représentation binaire de ce nœud **hierarchyid** sera écrite.
  
## <a name="return-types"></a>Types de retour  
**Type de retour CLR : void**
  
## <a name="remarks"></a>Notes  
Write est utilisée en interne par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cas de nécessité, par exemple lors du chargement de données à partir d’une colonne **hierarchyid**. Write est également appelée en interne quand une conversion est effectuée entre **hierarchyid** et **varbinary**.
  
## <a name="examples"></a>Exemples  
  
```csharp
MemoryStream stream = new MemoryStream();  
BinaryWriter bw = new BinaryWriter(stream);  
hid.Write(bw);  
byte[] encoding = stream.ToArray();  
```  
  
## <a name="see-also"></a>Voir aussi
[Read &#40;moteur de base de données&#41;](../../t-sql/data-types/read-database-engine.md)  
[ToString &#40;moteur de base de données&#41;](../../t-sql/data-types/tostring-database-engine.md)  
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[Référence de méthodes de type de données hierarchyid](https://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  

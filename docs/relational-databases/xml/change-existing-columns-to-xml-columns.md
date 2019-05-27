---
title: Transformer les colonnes existantes en colonnes XML | Microsoft Docs
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- tables [XML]
ms.assetid: 0d951424-9862-41fe-bd46-127f1c059bcb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c82450feef43d1ac03fbca9f45f11d03a79e098
ms.sourcegitcommit: 982a1dad0b58315cff7b54445f998499ef80e68d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66175356"
---
# <a name="change-existing-columns-to-xml-columns"></a>Transformer les colonnes existantes en colonnes XML

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

L'instruction ALTER TABLE prend en charge le type de données **xml** . Par exemple, vous pouvez modifier n'importe quelle colonne de type chaîne au type de données **xml** . Dans ces cas-là, les documents contenus dans la colonne doivent être corrects. En outre, si vous convertissez la colonne du type chaîne dans le type xml typé, les documents de la colonne sont validés par rapport aux schémas XSD spécifiés.  
  
```sql
CREATE TABLE T (Col1 int primary key, Col2 nvarchar(max));
GO  
INSERT INTO T   
  VALUES (1, '<Root><Product ProductID="1"/></Root>');
GO  
ALTER TABLE T   
  ALTER COLUMN Col2 xml;
```  
  
Vous pouvez convertir une colonne de type `xml` non typée en colonne XML typée. Par exemple :  
  
```sql
CREATE TABLE T (Col1 int primary key, Col2 xml);
GO  
INSERT INTO T   
  values (1, '<p1:ProductDescription ProductModelID="1"   
xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
            </p1:ProductDescription>');
GO   
-- Make it a typed xml column by specifying a schema collection.  
ALTER TABLE T   
  ALTER COLUMN Col2 xml (Production.ProductDescriptionSchemaCollection);
```  
  
> [!NOTE]  
> Le script sera exécuté sur la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] car la collection de schémas XML, `Production.ProductDescriptionSchemaCollection`, est créée dans le cadre de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
 Dans l'exemple précédent, toutes les instances stockées dans la colonne sont validées et typées par rapport aux schémas XSD de la collection spécifiée. Si la colonne contient une ou plusieurs instances XML non valides au regard du schéma spécifié, l'instruction `ALTER TABLE` échoue et vous ne pouvez pas convertir la colonne XML non typée en colonne XML typée.  
  
> [!NOTE]  
> Si une table est volumineuse, la modification d'une colonne de type **xml** peut s'avérer coûteuse. En effet, le système doit vérifier que chaque document est correct et, s'il s'agit d'un document XML typé, il doit le valider.  
  
Pour plus d’informations sur le XML typé, consultez [Comparer du XML typé et du XML non typé](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  

---
title: 'Spécification de l’attribut SQL : inverse sur SQL : Relationship (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- bulk load [SQLXML]
- inverse attribute
- relationships [SQLXML], inverse orders
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- updategrams [SQLXML], relationships
- sql:inverse
ms.assetid: 08904cbd-9c86-493d-90c3-f5e1d13ce59d
author: MightyPen
ms.author: genemi
ms.reviewer: ''
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1d8a6390ded6250355936dbef29051f76be14266
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65980692"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>Spécification de l'attribut sql:inverse sur sql:relationship (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Le **SQL : inverse** attribut est utile uniquement lorsque le schéma XSD est utilisé pour le chargement en masse ou par une mise à jour. Le **SQL : inverse** attribut peut être spécifié sur le  **\<SQL : Relationship >** élément. Dans les codes de mise à jour, la logique de code de mise à jour interprète le schéma pour déterminer les tables et colonnes mises à jour par l'opération de code de mise à jour. Les relations parent-enfant spécifiées dans le schéma déterminent l'ordre dans lequel les enregistrements sont modifiés (insérés ou supprimés).  
  
 Si vous avez un schéma XSD dans lequel la relation parent-enfant est spécifiée dans l'ordre inverse de la relation clé primaire/clé étrangère entre les colonnes de base de données correspondantes, l'opération d'insertion ou de suppression du code de mise à jour échouera à cause de la violation de clé primaire/clé étrangère. Dans ce cas, le **SQL : inverse** attribut est spécifié (**SQL : inverse = « true »**) dans le  **\<SQL : Relationship >** élément et la logique de mise à jour inverse son interprétation de la relation parent-enfant spécifiée dans le schéma.  
  
 Le **SQL : inverse** attribut prend une valeur booléenne (0 = Faux, 1 = true). Les valeurs acceptables sont 0, 1, true et false.  
  
 Pour un exemple d’utilisation à l’aide du **SQL : inverse** annotation, consultez [spécifiant un schéma de mappage annoté dans une mise à jour](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Spécification de relations à l’aide de SQL : Relationship &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  

---
title: 'Définir l’attribut SQL : inverse sur SQL : Relationship (SQLXML)'
description: 'Découvrez comment utiliser l’attribut SQL : inverse sur l’élément SQL : Relationship pour spécifier les relations entre les colonnes de base de données dans une opération mise à jour.'
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
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b714a70cb3d537d3f9859945b5fdee6842aa5d58
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97479340"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>Spécification de l'attribut sql:inverse sur sql:relationship (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  L’attribut **SQL : inverse** est utile uniquement lorsque le schéma XSD est utilisé pour le chargement en masse ou par un mise à jour. L’attribut **SQL : inverse** peut être spécifié sur l' **\<sql:relationship>** élément. Dans les codes de mise à jour, la logique de code de mise à jour interprète le schéma pour déterminer les tables et colonnes mises à jour par l'opération de code de mise à jour. Les relations parent-enfant spécifiées dans le schéma déterminent l'ordre dans lequel les enregistrements sont modifiés (insérés ou supprimés).  
  
 Si vous avez un schéma XSD dans lequel la relation parent-enfant est spécifiée dans l'ordre inverse de la relation clé primaire/clé étrangère entre les colonnes de base de données correspondantes, l'opération d'insertion ou de suppression du code de mise à jour échouera à cause de la violation de clé primaire/clé étrangère. Dans ce cas, l’attribut **SQL : inverse** est spécifié (**SQL : inverse = "true"**) dans l' **\<sql:relationship>** élément, et la logique mise à jour inverse son interprétation de la relation parent-enfant spécifiée dans le schéma.  
  
 L’attribut **SQL : inverse** prend une valeur booléenne (0 = false, 1 = true). Les valeurs acceptables sont 0, 1, true et false.  
  
 Pour obtenir un exemple fonctionnel à l’aide de l’annotation **SQL : inversée** , consultez [spécification d’un schéma de mappage annoté dans un mise à jour](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Spécification de relations à l’aide de SQL : Relationship &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  

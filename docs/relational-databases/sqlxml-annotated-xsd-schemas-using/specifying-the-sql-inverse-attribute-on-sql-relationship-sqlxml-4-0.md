---
title: Définir sql:attribut inverse sur sql:relation (SQLXML)
description: Apprenez à utiliser l’attribut sql:inverse sur l’élément de relation sql:pour spécifier les relations entre les colonnes de base de données dans une opération updategram.
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fe5409120a3d0c5df3cf05318b0b85fd22d07bdf
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388093"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>Spécification de l'attribut sql:inverse sur sql:relationship (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **L’attribut sql:inverse** n’est utile que lorsque le schéma XSD est utilisé pour la charge en vrac ou par un updategram. **L’attribut sql:inverse** peut être spécifié sur le ** \<sql:relation>** élément. Dans les codes de mise à jour, la logique de code de mise à jour interprète le schéma pour déterminer les tables et colonnes mises à jour par l'opération de code de mise à jour. Les relations parent-enfant spécifiées dans le schéma déterminent l'ordre dans lequel les enregistrements sont modifiés (insérés ou supprimés).  
  
 Si vous avez un schéma XSD dans lequel la relation parent-enfant est spécifiée dans l'ordre inverse de la relation clé primaire/clé étrangère entre les colonnes de base de données correspondantes, l'opération d'insertion ou de suppression du code de mise à jour échouera à cause de la violation de clé primaire/clé étrangère. Dans de tels cas, **l’attribut sql:inverse** est spécifié (**sql:inverse "vrai"**) dans le ** \<sql:relation>** élément, et la logique updategram inverse son interprétation de la relation parent-enfant spécifiée dans le schéma.  
  
 **L’attribut sql: inverse** prend une valeur Boolean (0-faux, 1-true). Les valeurs acceptables sont 0, 1, true et false.  
  
 Pour un échantillon de travail à l’aide de **l’annotation sql:inverse,** voir [spécifier un schéma de cartographie annoté dans un Updategram](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier les relations à l’aide de sql:relation &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  

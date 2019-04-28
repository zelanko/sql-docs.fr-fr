---
title: 'Spécification de l’attribut SQL : inverse sur SQL : Relationship (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bf8d5dee0d72800c5b6250d83106cda552004536
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62717876"
---
# <a name="specifying-the-sqlinverse-attribute-on-sqlrelationship-sqlxml-40"></a>Spécification de l'attribut sql:inverse sur sql:relationship (SQLXML 4.0)
  L'attribut `sql:inverse` est utile uniquement lorsque le schéma XSD est utilisé pour le chargement en masse ou par un code de mise à jour (updategram). Le `sql:inverse` attribut peut être spécifié sur le  **\<SQL : Relationship >** élément. Dans les codes de mise à jour, la logique de code de mise à jour interprète le schéma pour déterminer les tables et colonnes mises à jour par l'opération de code de mise à jour. Les relations parent-enfant spécifiées dans le schéma déterminent l'ordre dans lequel les enregistrements sont modifiés (insérés ou supprimés).  
  
 Si vous avez un schéma XSD dans lequel la relation parent-enfant est spécifiée dans l'ordre inverse de la relation clé primaire/clé étrangère entre les colonnes de base de données correspondantes, l'opération d'insertion ou de suppression du code de mise à jour échouera à cause de la violation de clé primaire/clé étrangère. Dans ce cas, le `sql:inverse` attribut est spécifié (`sql:inverse="true"`) dans le  **\<SQL : Relationship >** élément et l’inverse logique de mise à jour son interprétation de la relation parent-enfant spécifiée dans le schéma.  
  
 L'attribut `sql:inverse` prend une valeur booléenne (0=faux, 1=vrai). Les valeurs acceptables sont 0, 1, true et false.  
  
 Pour un exemple d’utilisation à l’aide du `sql:inverse` annotation, consultez [spécifiant un schéma de mappage annoté dans une mise à jour](../sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Spécification de relations à l’aide de SQL : Relationship &#40;SQLXML 4.0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
  
  

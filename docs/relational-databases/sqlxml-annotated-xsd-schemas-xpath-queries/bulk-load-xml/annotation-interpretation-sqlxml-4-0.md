---
title: Interprétation des annotations (SQLXML)
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, XML Bulk Load
- XML Bulk Load [SQLXML], annotation intepretations
- annotations [SQLXML]
- bulk load [SQLXML], annotation interpretations
- annotated XDR schemas, XML Bulk Load
ms.assetid: 1c46bdb6-2812-4a13-b60b-7101c04b299f
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4dc5842487c0740386d97f3ec187dff144520a74
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75246748"
---
# <a name="annotation-interpretation-sqlxml-40"></a>Interprétation d'annotation (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Les rubriques de cette section décrivent comment le chargement en masse XML interprète les annotations dans le schéma XSD. Le comportement décrit ici s'applique également aux annotations dans le schéma XDR.  
  
> [!NOTE]  
>  Les informations fournies dans ces rubriques décrivent uniquement les annotations utilisées par le chargement en masse XML lors de son traitement. Pour obtenir la liste complète des annotations pour le schéma XSD prises en charge par SQLXML 4,0, consultez [utilisation des annotations dans les schémas xsd &#40;sqlxml 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md). Pour obtenir la liste des annotations prises en charge pour les schémas XDR, consultez [schémas XDR Annotés &#40;dépréciés dans SQLXML 4,0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [SQL : Relationship et la règle de classement des clés &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 Décrit comment l’annotation **SQL : Relationship** est interprétée dans le chargement en masse XML.  
  
 [SQL : mappé &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-mapped.md)  
 Décrit comment l’annotation **SQL : mapped** est interprétée dans le chargement en masse XML.  
  
 [SQL : Limit-Field et SQL : limit-value &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Décrit comment les annotations **SQL : Limit-Field** et **SQL : limit-value** sont interprétées dans le chargement en masse XML.  
  
 [SQL : overflow-field &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 Décrit comment l’annotation **SQL : overflow** est interprétée dans le chargement en masse XML.  
  
 [Autres annotations &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-other-annotations.md)  
 Décrit comment les annotations suivantes sont interprétées dans le chargement en masse XML : **SQL : id-prefix**, **SQL : use-cdata**, **SQL : URL-enencoder**, **SQL : is-mapping-schema**, **SQL : key-fields**.  
  
  

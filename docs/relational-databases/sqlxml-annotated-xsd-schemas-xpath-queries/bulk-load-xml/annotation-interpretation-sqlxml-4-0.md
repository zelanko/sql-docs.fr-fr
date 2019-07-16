---
title: Interprétation des annotations (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 80db781d32c8d48f9df48c27baa1807eef5a9f7b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68054387"
---
# <a name="annotation-interpretation-sqlxml-40"></a>Interprétation d'annotation (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Les rubriques de cette section décrivent comment le chargement en masse XML interprète les annotations dans le schéma XSD. Le comportement décrit ici s'applique également aux annotations dans le schéma XDR.  
  
> [!NOTE]  
>  Les informations fournies dans ces rubriques décrivent uniquement les annotations utilisées par le chargement en masse XML lors de son traitement. Pour obtenir une liste complète des annotations pour le schéma XSD sont pris en charge par SQLXML 4.0, consultez [à l’aide des Annotations dans les schémas XSD &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md). Pour obtenir la liste des annotations prises en charge pour les schémas XDR, consultez [de schémas XDR annotés &#40;déconseillé dans SQLXML 4.0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [SQL : Relationship et la règle de tri par clé &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 Décrit comment la **SQL : Relationship** annotation est interprétée de chargement en masse XML.  
  
 [SQL : mappé &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-mapped.md)  
 Décrit comment la **sql : mappé** annotation est interprétée de chargement en masse XML.  
  
 [SQL : limit-champ et SQL : limit-valeur &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Décrit comment la **SQL : limit-champ** et **SQL : limit-valeur** annotations sont interprétées dans le chargement en masse XML.  
  
 [sql:overflow-field &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 Décrit comment la **SQL : Overflow** annotation est interprétée de chargement en masse XML.  
  
 [Autres Annotations &#40;SQLXML 4.0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-other-annotations.md)  
 Décrit comment les annotations suivantes sont interprétées dans le chargement en masse XML : **SQL : ID-préfixe**, **SQL : use-cdata**, **SQL : url-encode**, **sql : schéma de mappage est**, **SQL : Key-champs**.  
  
  

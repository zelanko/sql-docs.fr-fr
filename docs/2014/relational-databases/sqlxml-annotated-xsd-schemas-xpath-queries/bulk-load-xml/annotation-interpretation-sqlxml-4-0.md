---
title: Interprétation d’annotation (SQLXML 4.0) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, XML Bulk Load
- XML Bulk Load [SQLXML], annotation intepretations
- annotations [SQLXML]
- bulk load [SQLXML], annotation interpretations
- annotated XDR schemas, XML Bulk Load
ms.assetid: 1c46bdb6-2812-4a13-b60b-7101c04b299f
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ba4c9e6506b67802a8a9571df80ff4db7d2b3934
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051006"
---
# <a name="annotation-interpretation-sqlxml-40"></a>Interprétation d'annotation (SQLXML 4.0)
  Les rubriques de cette section décrivent comment le chargement en masse XML interprète les annotations dans le schéma XSD. Le comportement décrit ici s'applique également aux annotations dans le schéma XDR.  
  
> [!NOTE]  
>  Les informations fournies dans ces rubriques décrivent uniquement les annotations utilisées par le chargement en masse XML lors de son traitement. Pour obtenir une liste complète des annotations pour le schéma XSD sont pris en charge par SQLXML 4.0, consultez [à l’aide des Annotations dans les schémas XSD &#40;SQLXML 4.0&#41;](../../sqlxml-annotated-xsd-schemas-using/using-annotations-in-xsd-schemas-sqlxml-4-0.md). Pour une liste des annotations prises en charge pour les schémas XDR, consultez [de schémas XDR annotés &#40;déconseillé dans SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [SQL : Relationship et la règle de tri par clé &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-relationship-and-key-ordering-rule.md)  
 Décrit comment l'annotation `sql:relationship` est interprétée dans le chargement en masse XML.  
  
 [SQL : mappé &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-mapped.md)  
 Décrit comment l'annotation `sql:mapped` est interprétée dans le chargement en masse XML.  
  
 [SQL : limit-champ et SQL : limit-valeur &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Décrit comment les annotations `sql:limit-field` et `sql:limit-value` sont interprétées dans le chargement en masse XML.  
  
 [SQL : Overflow-champ &#40;SQLXML 4.0&#41;](annotation-interpretation-sql-overflow-field.md)  
 Décrit comment l'annotation `sql:overflow` est interprétée dans le chargement en masse XML.  
  
 [Autres Annotations &#40;SQLXML 4.0&#41;](annotation-interpretation-other-annotations.md)  
 Décrit comment les annotations suivantes sont interprétées dans le chargement en masse XML :  `sql:id-prefix`, `sql:use-cdata`, `sql:url-encode`, `sql:is-mapping-schema`, `sql:key-fields`.  
  
  
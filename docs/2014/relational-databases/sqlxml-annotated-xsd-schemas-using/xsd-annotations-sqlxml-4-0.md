---
title: Annotations XSD (SQLXML 4.0) | Microsoft Docs
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
- annotated XSD schemas, annotations listed
- XSD schemas [SQLXML], annotations
ms.assetid: c62a6785-8d66-40a2-9c5d-80c73d600a3b
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: eeb6f6c72d6d453aaa2d656e725fd2b8ee5d9e45
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211129"
---
# <a name="xsd-annotations-sqlxml-40"></a>Annotations XSD (SQLXML 4.0)
  Le tableau ci-dessous répertorie les annotations XSD introduites dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les compare avec les annotations XDR introduites dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
|Annotation XSD|Description|Lien de rubrique|Annotation XDR|  
|--------------------|-----------------|----------------|--------------------|  
|`sql:encode`|Lorsqu'un élément ou un attribut XML est mappé à une colonne BLOB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], autorise la demande d'un URI de référence. Cet URI peut être utilisé ultérieurement pour retourner les données BLOB.|[Demande de références URL à des données BLOB à l’aide de sql : encode &#40;SQLXML 4.0&#41;](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)|`url-encode`|  
|`sql:guid`|Vous permet de spécifier s'il convient d'utiliser une valeur GUID générée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d'utiliser la valeur fournie dans le code de mise à jour (updategram) pour cette colonne.|[Utilisation des annotations sql:identity et sql:guid](using-the-sql-identity-and-sql-guid-annotations.md)|Non pris en charge|  
|`sql:hide`|Masque l'élément ou l'attribut spécifié dans le schéma dans le document XML résultant.|[Masquage d’éléments et d’attributs à l’aide de sql:hide](hiding-elements-and-attributes-by-using-sql-hide.md)|Non pris en charge|  
|`sql:identity`|Peut être spécifié sur un nœud quelconque qui est mappé à une colonne de base de données de type IDENTITY. La valeur spécifiée pour cette annotation définit comment la colonne de type IDENTITY correspondante dans la base de données est mise à jour.|[Utilisation des annotations sql:identity et sql:guid](using-the-sql-identity-and-sql-guid-annotations.md)|Non pris en charge|  
|`sql:inverse`|Indique à la logique de mise à jour d’inverser son interprétation de la relation parent-enfant qui a été spécifiée à l’aide de  **\<SQL : Relationship >**.|[Spécification de l’attribut SQL : inverse sur SQL : Relationship &#40;SQLXML 4.0&#41;](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)|Non pris en charge|  
|`sql:is-constant`|Crée un élément XML qui n'est mappé à aucune table. L'élément apparaît dans le résultat de la requête.|[Création d’éléments constants à l’aide de sql : constante est &#40;SQLXML 4.0&#41;](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)|Identique|  
|`sql:key-fields`|Permet de spécifier une ou des colonnes qui identifient de façon unique les lignes d'une table.|[Identification des colonnes de clé à l’aide de SQL : Key-champs &#40;SQLXML 4.0&#41;](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)|Identique|  
|`sql:limit-field`<br /><br /> `sql:limit-value`|Permet de limiter les valeurs retournées en fonction d'une valeur de limitation.|[Filtrage des valeurs à l’aide de SQL : limit-champ et SQL : limit-valeur &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)|Identique|  
|`sql:mapped`|Permet à des éléments de schéma d'être exclus du résultat.|[Exclusion d’éléments de schéma du Document XML résultant avec sql : mappé &#40;SQLXML 4.0&#41;](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)|`map-field`|  
|`sql:max-depth`|Vous permet de spécifier la profondeur dans les relations récursives spécifiées dans le schéma.|[Spécification de la profondeur dans les relations récursives à l’aide de sql:max-depth](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)|Non pris en charge|  
|`sql:overflow-field`|Identifie la colonne de la base de données qui contient les données de dépassement.|[Récupération des données à l’aide de SQL : Overflow-champ &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)|Identique|  
|`sql:prefix`|Crée des attributs ID, IDREF et IDREFS XML valides. Ajoute les valeurs des attributs ID, IDREF et IDREFS avec une chaîne.|[Création d’ID valide, IDREF et IDREFS à des attributs de Type à l’aide de SQL : Prefix &#40;SQLXML 4.0&#41;](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)|Identique|  
|`sql:relationship`|Spécifie des relations entre des éléments XML. Les attributs `parent`, `child`, `parent-key` et `child-key` sont utilisés pour établir la relation.|[Spécification de relations à l’aide de SQL : Relationship &#40;SQLXML 4.0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)|Les noms des attributs sont différents :<br /><br /> `key-relation`<br /><br /> `foreign-relation`<br /><br /> `key`<br /><br /> `foreign-key`|  
|`sql:use-cdata`|Permet de spécifier les sections CDATA à utiliser pour certains éléments dans le document XML.|[Création de Sections CDATA à l’aide de SQL : use-cdata &#40;SQLXML 4.0&#41;](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)|Identique|  
  
> [!NOTE]  
>  L'attribut natif XSD `targetNamespace` remplace l'annotation `target-namespace` introduite dans le schéma de mappage [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] XDR.  
  
## <a name="see-also"></a>Voir aussi  
 [En spécifiant une cible Namespace à l’aide de l’attribut targetNamespace &#40;SQLXML 4.0&#41;](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
  
  

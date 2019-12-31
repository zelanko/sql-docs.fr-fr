---
title: Annotations XSD (SQLXML)
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, annotations listed
- XSD schemas [SQLXML], annotations
ms.assetid: c62a6785-8d66-40a2-9c5d-80c73d600a3b
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: acd1dc15531f2e4830993eed1404db4d7205feef
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75246802"
---
# <a name="xsd-annotations-sqlxml-40"></a>Annotations XSD (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Le tableau ci-dessous répertorie les annotations XSD introduites dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les compare avec les annotations XDR introduites dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
|Annotation XSD|Description|Lien de rubrique|Annotation XDR|  
|--------------------|-----------------|----------------|--------------------|  
|**sql:encode**|Lorsqu'un élément ou un attribut XML est mappé à une colonne BLOB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], autorise la demande d'un URI de référence. Cet URI peut être utilisé ultérieurement pour retourner les données BLOB.|[Demande de références URL à des données BLOB à l’aide de SQL : encode &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)|**Encoder par URL**|  
|**SQL : GUID**|Vous permet de spécifier s'il convient d'utiliser une valeur GUID générée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d'utiliser la valeur fournie dans le code de mise à jour (updategram) pour cette colonne.|[Utilisation des annotations sql:identity et sql:guid](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)|Non pris en charge|  
|**sql:hide**|Masque l'élément ou l'attribut spécifié dans le schéma dans le document XML résultant.|[Masquage d'éléments et d'attributs à l'aide de sql:hide](../../relational-databases/sqlxml-annotated-xsd-schemas-using/hiding-elements-and-attributes-by-using-sql-hide.md)|Non pris en charge|  
|**sql:identity**|Peut être spécifié sur un nœud quelconque qui est mappé à une colonne de base de données de type IDENTITY. La valeur spécifiée pour cette annotation définit comment la colonne de type IDENTITY correspondante dans la base de données est mise à jour.|[Utilisation des annotations sql:identity et sql:guid](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)|Non pris en charge|  
|**sql:inverse**|Indique à la logique mise à jour d’inverser son interprétation de la relation parent-enfant qui a été spécifiée à l’aide ** \<de SQL : Relationship>**.|[Spécification de l’attribut SQL : inverse sur SQL : Relationship &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)|Non pris en charge|  
|**sql:is-constant**|Crée un élément XML qui n'est mappé à aucune table. L'élément apparaît dans le résultat de la requête.|[Création d’éléments constants à l’aide de SQL : is-constant &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)|Identique|  
|**sql:key-fields**|Permet de spécifier une ou des colonnes qui identifient de façon unique les lignes d'une table.|[Identification des colonnes clés à l’aide de SQL : key-fields &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)|Identique|  
|**sql:limit-field**<br /><br /> **sql:limit-value**|Permet de limiter les valeurs retournées en fonction d'une valeur de limitation.|[Filtrage des valeurs à l’aide de SQL : Limit-Field et SQL : limit-value &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/filtering-values-using-sql-limit-field-and-sql-limit-value-sqlxml-4-0.md)|Identique|  
|**sql:mapped**|Permet à des éléments de schéma d'être exclus du résultat.|[Exclusion d’éléments de schéma du document XML obtenu à l’aide de SQL : mapped &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)|**champ de mappage**|  
|**sql:max-depth**|Vous permet de spécifier la profondeur dans les relations récursives spécifiées dans le schéma.|[Spécification de la profondeur dans les relations récursives à l'aide de sql:max-depth](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)|Non pris en charge|  
|**sql:overflow-field**|Identifie la colonne de la base de données qui contient les données de dépassement.|[Récupération de données non consommées à l’aide de SQL : overflow-field &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/retrieving-unconsumed-data-using-the-sql-overflow-field-sqlxml-4-0.md)|Identique|  
|**sql:prefix**|Crée des attributs ID, IDREF et IDREFS XML valides. Ajoute les valeurs des attributs ID, IDREF et IDREFS avec une chaîne.|[Création d’attributs de type ID, IDREF et IDREFS valides à l’aide de SQL : prefix &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)|Identique|  
|**sql:relationship**|Spécifie des relations entre des éléments XML. Les attributs **parent**, **enfant**, **parent-** clé et **clé enfant** sont utilisés pour établir la relation.|[Spécification de relations à l’aide de SQL : Relationship &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)|Les noms des attributs sont différents :<br /><br /> **clé-relation**<br /><br /> **relation étrangère**<br /><br /> **essentiel**<br /><br /> **clé étrangère**|  
|**sql:use-cdata**|Permet de spécifier les sections CDATA à utiliser pour certains éléments dans le document XML.|[Création de sections CDATA à l’aide de SQL : use-cdata &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)|Identique|  
  
> [!NOTE]  
>  L’attribut **targetNamespace** natif XSD remplace l’annotation de l' **espace de noms cible** qui a [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] été introduite dans le schéma de mappage XDR.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécification d’un espace de noms cible à l’aide de l’attribut targetNamespace &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
  
  

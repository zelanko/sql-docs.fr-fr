---
title: Annotations XSD (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 583f9803ea7a11384ff0b27a73cfd95be5a24101
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68066868"
---
# <a name="xsd-annotations-sqlxml-40"></a>Annotations XSD (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Le tableau ci-dessous répertorie les annotations XSD introduites dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et les compare avec les annotations XDR introduites dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
|Annotation XSD|Description|Lien de rubrique|Annotation XDR|  
|--------------------|-----------------|----------------|--------------------|  
|**sql:encode**|Lorsqu'un élément ou un attribut XML est mappé à une colonne BLOB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], autorise la demande d'un URI de référence. Cet URI peut être utilisé ultérieurement pour retourner les données BLOB.|[Demande de références URL à des données BLOB à l’aide de sql : encode &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)|**url-encode**|  
|**sql:guid**|Vous permet de spécifier s'il convient d'utiliser une valeur GUID générée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d'utiliser la valeur fournie dans le code de mise à jour (updategram) pour cette colonne.|[Utilisation des annotations sql:identity et sql:guid](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)|Non pris en charge|  
|**sql:hide**|Masque l'élément ou l'attribut spécifié dans le schéma dans le document XML résultant.|[Masquage d’éléments et d’attributs à l’aide de sql:hide](../../relational-databases/sqlxml-annotated-xsd-schemas-using/hiding-elements-and-attributes-by-using-sql-hide.md)|Non pris en charge|  
|**sql:identity**|Peut être spécifié sur un nœud quelconque qui est mappé à une colonne de base de données de type IDENTITY. La valeur spécifiée pour cette annotation définit comment la colonne de type IDENTITY correspondante dans la base de données est mise à jour.|[Utilisation des annotations sql:identity et sql:guid](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)|Non pris en charge|  
|**sql:inverse**|Indique à la logique de mise à jour d’inverser son interprétation de la relation parent-enfant qui a été spécifiée à l’aide de  **\<SQL : Relationship >** .|[Spécification de l’attribut SQL : inverse sur SQL : Relationship &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)|Non pris en charge|  
|**sql:is-constant**|Crée un élément XML qui n'est mappé à aucune table. L'élément apparaît dans le résultat de la requête.|[Création d’éléments constants à l’aide de sql : constante est &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)|Identique|  
|**sql:key-fields**|Permet de spécifier une ou des colonnes qui identifient de façon unique les lignes d'une table.|[Identification des colonnes de clé à l’aide de SQL : Key-champs &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)|Identique|  
|**sql:limit-field**<br /><br /> **sql:limit-value**|Permet de limiter les valeurs retournées en fonction d'une valeur de limitation.|[Filtrage des valeurs à l’aide de SQL : limit-champ et SQL : limit-valeur &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/filtering-values-using-sql-limit-field-and-sql-limit-value-sqlxml-4-0.md)|Identique|  
|**sql:mapped**|Permet à des éléments de schéma d'être exclus du résultat.|[Exclusion d’éléments de schéma du Document XML résultant avec sql : mappé &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)|**map-field**|  
|**sql:max-depth**|Vous permet de spécifier la profondeur dans les relations récursives spécifiées dans le schéma.|[Spécification de la profondeur dans les relations récursives à l’aide de sql:max-depth](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)|Non pris en charge|  
|**sql:overflow-field**|Identifie la colonne de la base de données qui contient les données de dépassement.|[Récupération des données à l’aide de SQL : Overflow-champ &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/retrieving-unconsumed-data-using-the-sql-overflow-field-sqlxml-4-0.md)|Identique|  
|**sql:prefix**|Crée des attributs ID, IDREF et IDREFS XML valides. Ajoute les valeurs des attributs ID, IDREF et IDREFS avec une chaîne.|[Création d’ID valide, IDREF et IDREFS à des attributs de Type à l’aide de SQL : Prefix &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)|Identique|  
|**sql:relationship**|Spécifie des relations entre des éléments XML. Le **parent**, **enfant**, **-clé parente**, et **-clé enfant** attributs sont utilisés pour établir la relation.|[Spécification de relations à l’aide de SQL : Relationship &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)|Les noms des attributs sont différents :<br /><br /> **relation de clé**<br /><br /> **foreign-relation**<br /><br /> **key**<br /><br /> **foreign-key**|  
|**sql:use-cdata**|Permet de spécifier les sections CDATA à utiliser pour certains éléments dans le document XML.|[Création de Sections CDATA à l’aide de SQL : use-cdata &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)|Identique|  
  
> [!NOTE]  
>  Natif XSD **targetNamespace** attribut remplace le **espace de noms cible** annotation qui a été introduite dans le [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] schéma de mappage XDR.  
  
## <a name="see-also"></a>Voir aussi  
 [En spécifiant une cible Namespace à l’aide de l’attribut targetNamespace &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
  
  

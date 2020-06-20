---
title: Utilisation d’annotations dans les schémas XSD (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, about annotated XSD schemas
- annotations [SQLXML]
- relationships [SQLXML]
- relationships [SQLXML], hierarchical relationships
- hierarchical relationships [SQLXML]
- mapping schema [SQLXML], scenarios for using
ms.assetid: 78f318a4-7a36-473b-9852-a4bae6940ce5
author: rothja
ms.author: jroth
ms.openlocfilehash: 5237c5c24b302e0ce1996e03e89b3e01ba6d8f51
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85003011"
---
# <a name="using-annotations-in-xsd-schemas-sqlxml-40"></a>Utilisation des annotations dans les schémas XSD (SQLXML 4.0)
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] SQLXML 4.0, le langage de schéma XSD prend en charge les annotations d'une manière similaire aux annotations introduites avec le langage de schéma XDR (XML-Data Reduced). Des annotations supplémentaires ont été introduites dans XSD qui ne sont pas prises en charge dans XDR.  
  
 Ces annotations peuvent être utilisées dans le schéma XSD pour spécifier le mappage des données XML et des données relationnelles. Est inclus le mappage entre les éléments et les attributs du schéma XSD avec les tables (vues) et les colonnes des bases de données.  
  
 Si vous ne spécifiez pas les annotations, le mappage par défaut a lieu. Par défaut, un élément XSD avec un type complexe est mappé avec un nom de table (vue) de la base de données spécifiée, et un élément ou attribut avec un type simple est mappé avec la colonne du même nom en tant qu'élément ou attribut.  
  
 Ces annotations peuvent également être utilisées pour spécifier les relations hiérarchiques dans XML, représentant ainsi les relations dans la base de données, car un schéma XSD est simplement une vue XML de données relationnelles.  
  
 Cette section fournit les descriptions des annotations que vous pouvez utiliser avec les schémas XSD, ainsi que des exemples d'utilisation.  
  
> [!NOTE]  
>  Tous les exemples de cette section spécifient des requêtes XPath simples sur le schéma XSD annoté décrit dans chaque exemple. Ces exemples présument que vous connaissiez le langage XPath.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Annotations XSD &#40;SQLXML 4,0&#41;](xsd-annotations-sqlxml-4-0.md)  
 Répertorie les annotations que vous pouvez utiliser avec les schémas XSD, leurs descriptions et les annotations équivalentes pour XDR.  
  
 [Mappage par défaut d’éléments et d’attributs XSD à des tables et des colonnes &#40;SQLXML 4,0&#41;](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
 Explique le mappage par défaut et fournit des exemples de tâches en rapport avec le mappage par défaut.  
  
 [Mappage explicite d’éléments et d’attributs XSD à des tables et des colonnes &#40;SQLXML 4,0&#41;](explicit-mapping-xsd-elements-and-attributes-to-tables-and-columns.md)  
 Explique le mappage explicite avec les annotations `sql:relation` et `sql:field` et fournit des exemples.  
  
 [Spécification de relations à l’aide de SQL : Relationship &#40;SQLXML 4,0&#41;](specifying-relationships-using-sql-relationship-sqlxml-4-0.md)  
 Décrit et fournit des exemples de l'annotation `sql:relationship`.  
  
 [Spécification de l’attribut SQL : inverse sur SQL : Relationship &#40;SQLXML 4,0&#41;](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)  
 Décrit l'annotation `sql:inverse`.  
  
 [Création d’éléments constants à l’aide de SQL : is-constant &#40;SQLXML 4,0&#41;](creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)  
 Décrit et fournit des exemples de l'annotation `sql:is-constant`.  
  
 [Exclusion d’éléments de schéma du document XML obtenu à l’aide de SQL : mapped &#40;SQLXML 4,0&#41;](excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)  
 Décrit et fournit des exemples de l'annotation `sql:mapped`.  
  
 [Filtrage des valeurs à l’aide de SQL : Limit-Field et SQL : limit-value &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-limit-field-and-sql-limit-value.md)  
 Décrit et fournit des exemples des annotations `sql:limit-field` et `sql:limit-value`.  
  
 [Identification des colonnes clés à l’aide de SQL : key-fields &#40;SQLXML 4,0&#41;](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)  
 Décrit et fournit des exemples de l'annotation `sql:key-fields`.  
  
 [Spécification d’un espace de noms cible à l’aide de l’attribut targetNamespace &#40;SQLXML 4,0&#41;](specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
 Décrit et fournit des exemples de l’attribut **targetNamespace** .  
  
 [Création d’attributs de type ID, IDREF et IDREFS valides à l’aide de SQL : prefix &#40;SQLXML 4,0&#41;](creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)  
 Décrit et fournit des exemples de l'annotation `sql:prefix`.  
  
 [Les contraintes de type de données et l’annotation sql : DataType &#40;SQLXML 4,0&#41;](data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)  
 Décrit et fournit des exemples de l'annotation `sql:datatype`.  
  
 [Mappage de types de données XSD à des types de données XPath &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/xpath-data-types-sqlxml-4-0.md)  
 Fournit une table qui compare les types de données XSD, XDR et Xpath, et répertorie les conversions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] appropriées.  
  
 [Création de sections CDATA à l’aide de SQL : use-cdata &#40;SQLXML 4,0&#41;](creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)  
 Décrit et fournit des exemples de l'annotation `sql:use-data`.  
  
 [Demande de références URL à des données BLOB à l’aide de SQL : encode &#40;SQLXML 4,0&#41;](requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)  
 Décrit et fournit des exemples de l'annotation `sql:encode`.  
  
 [Récupération de données non consommées à l’aide de SQL : overflow-field &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/annotation-interpretation-sql-overflow-field.md)  
 Décrit et fournit des exemples de l'annotation `sql:overflow-field`.  
  
 [Masquage d'éléments et d'attributs à l'aide de sql:hide](hiding-elements-and-attributes-by-using-sql-hide.md)  
 Décrit et fournit des exemples de l'annotation `sql:hide`.  
  
 [Utilisation des annotations sql:identity et sql:guid](using-the-sql-identity-and-sql-guid-annotations.md)  
 Décrit et fournit des exemples des annotations `sql:identity` et `sql:guid`.  
  
 [Spécification de la profondeur dans les relations récursives à l'aide de sql:max-depth](specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)  
 Décrit et fournit des exemples de l'annotation `sql:max-depth`.  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur la sécurité des schémas annotés &#40;SQLXML 4,0&#41;](../sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)  
  
  

---
title: Présentation des schémas XSD annotés (SQLXML)
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- mapping schema [SQLXML], about mapping schema
- views [SQLXML]
- valid XSD schemas [SQLXML]
- annotations [SQLXML]
- XSD schemas [SQLXML], creating XML views
- annotated XSD schemas, creating XML views
- minimum XSD schema
- annotated XSD schemas, examples
- XML views [SQLXML]
ms.assetid: 15282db1-65c4-43be-bdb7-e9ef49cb33a2
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 81791c2b48e414f4f147bfff47cf1d9166d4a2a5
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75247056"
---
# <a name="introduction-to-annotated-xsd-schemas-sqlxml-40"></a>Introduction aux schémas XSD annotés (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Vous pouvez créer des vues XML de données relationnelles à l'aide du langage XSD (XML Schema Definition). Ces vues peuvent ensuite être interrogées à l'aide de requêtes XML Path (XPath). Cette opération équivaut à créer des vues à l'aide d'instructions CREATE VIEW et à spécifier ensuite des requêtes SQL contre les vues.  
  
 Un schéma XML décrit la structure d'un document XML, ainsi que diverses contraintes agissant sur les données du document. Lorsque vous spécifiez des requêtes XPath à exécuter dans le schéma, la structure du document XML retournée est déterminée par le schéma dans lequel la requête XPath est exécutée.  
  
 Dans un schéma XSD, l' ** \<élément xsd : Schema>** englobe l’ensemble du schéma ; toutes les déclarations d’éléments doivent être contenues dans l' ** \<élément xsd : Schema>** . Vous pouvez décrire des attributs qui définissent l’espace de noms dans lequel le schéma réside et les espaces de noms utilisés dans le schéma en tant que propriétés de l' ** \<élément xsd : Schema>** .  
  
 Un schéma XSD valide doit contenir l' ** \<élément xsd : Schema>** défini comme suit :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<!-- additional schema definitions here -->  
</xsd:schema>  
```  
  
 L' ** \<élément xsd : Schema>** est dérivé de la spécification d’espace de noms http://www.w3.org/2001/XMLSchemadu schéma XML à l’adresse.  
  
## <a name="annotations-to-the-xsd-schema"></a>Annotations dans le schéma XSD  
 Vous pouvez utiliser un schéma XSD avec des annotations qui décrivent le mappage à une base de données, interroger la base de données, puis retourner les résultats sous la forme d'un document XML. Les annotations sont fournies pour mapper un schéma XSD à des tables et des colonnes de base de données. Vous pouvez définir et exécuter des requêtes XPath dans la vue XML créée par le schéma XSD pour interroger la base de données et obtenir des résultats sous forme de données XML.  
  
> [!NOTE]  
>  Dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0, le langage de schéma XSD prend en charge les annotations introduites avec le langage de schéma XDR (XML-Data Reduced) dans [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]. Le langage XDR annoté est déconseillé dans SQLXML 4.0.  
  
 Dans le contexte de la base de données relationnelle, il est utile de mapper le schéma XSD arbitraire à un magasin relationnel. Une manière d'y parvenir consiste à annoter le schéma XSD. Un schéma XSD avec les annotations est appelé schéma de *mappage*, qui fournit des informations relatives à la façon dont les données XML doivent être mappées à la Banque de données relationnelle. Un schéma de mappage constitue en réalité une vue XML des données relationnelles. Ces mappages peuvent servir à extraire des données relationnelles sous la forme d'un document XML.  
  
## <a name="namespace-for-annotations"></a>Espace de noms des annotations  
 Dans un schéma XSD, les annotations sont spécifiées à l’aide de l’espace de noms **urn : schemas-microsoft-com : mapping-schema**. Comme indiqué dans l’exemple suivant, le moyen le plus simple de spécifier l’espace de noms consiste à le spécifier dans la ** \<balise xsd : Schema>** .  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
...  
</xsd:schema>  
```  
  
 Le préfixe d’espace de noms utilisé est arbitraire. Dans cette documentation, le préfixe **SQL** est utilisé pour désigner l’espace de noms d’annotation et pour distinguer les annotations de cet espace de noms de celles d’autres espaces de noms.  
  
## <a name="example-of-an-annotated-xsd-schema"></a>Exemple de schéma XSD annoté  
 Dans l’exemple suivant, le schéma XSD se compose d’un ** \<élément person. contact>** . L' ** \<élément Employee>** a un attribut **ContactID** et ** \<FirstName>** et ** \<LastName>** éléments enfants :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  <xsd:element name="Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"    
                     type="xsd:string" />   
        <xsd:element name="LName"  
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID" type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Des annotations sont ajoutées à ce schéma XSD pour mapper ses éléments et attributs aux tables et colonnes de base de données :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"  
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ConID"   
                       sql:field="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Dans le schéma de mappage, ** \<l’élément Contact>** est mappé à la table Person. contact de l’exemple de base de données AdventureWorks à l’aide de l’annotation **SQL : relation** . Les attributs ConID, FName et LName sont mappés aux colonnes ContactID, FirstName et LastName dans la table Person. contact à l’aide des annotations **SQL : Field** .  
  
 Ce schéma XSD annoté crée la vue XML des données relationnelles. Vous pouvez interroger cette vue XML au moyen du langage XPath. En guise de résultat, une requête XPath retourne un document XML au lieu de l'ensemble de lignes retourné par les requêtes SQL.  
  
> [!NOTE]  
>  Dans le schéma de mappage, le respect de la casse pour les valeurs relationnelles spécifiées (telles que le nom de table et le nom de colonne) varie selon que SQL Server utilise des paramètres de classement sensibles à la casse. Pour plus d’informations, consultez [Collation and Unicode Support](../../../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="other-resources"></a>Autres ressources  
 Vous trouverez des informations supplémentaires sur le langage XSD (XML Schema Definition), le langage XPath ( XML Path) et le langage XSLT (Extensible Stylesheet Language Transformations) sur les sites Web aux adresses suivantes :  
  
-   Schéma XML, partie 0 : introduction, recommandation du W3C (https://www.w3.org/TR/xmlschema-0/)  
  
-   Schéma XML, partie 1 : structures, recommandation du W3C (https://www.w3.org/TR/xmlschema-1/)  
  
-   Schéma XML, partie 2 : types de données, recommandation du W3C (https://www.w3.org/TR/xmlschema-2/)  
  
-   XML Path Language (XPath) (https://www.w3.org/TR/xpath)  
  
-   XSLT (XSL Transformations) (https://www.w3.org/TR/xslt)  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur la sécurité des schémas annotés &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/annotated-schema-security-considerations-sqlxml-4-0.md)   
 [Les schémas XDR annotés &#40;dépréciés dans SQLXML 4,0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md)  
  
  

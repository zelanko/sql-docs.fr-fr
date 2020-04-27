---
title: Utilisation de schémas XSD annotés dans les requêtes (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML]
- inline schemas [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- queries [SQLXML], annotated XSD schemas
- retrieving data
- mapping schema [SQLXML], queries
- multiple inline schemas
- annotated XSD schemas, queries
- XSD schemas [SQLXML], queries
- templates [SQLXML], annotated XSD schemas in queries
ms.assetid: 927a30a2-eae8-420d-851d-551c5f884f3c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c435ff3bacecb101784695fe42b8b2158625e058
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66014464"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a>Utilisation de schémas XSD annotés dans les requêtes (SQLXML 4.0)
  Vous pouvez spécifier des requêtes sur un schéma annoté afin de récupérer des données de la base de données ; pour ce faire, spécifiez des requêtes XPath dans un modèle par rapport au schéma XSD.  
  
 L' ** \<élément SQL : XPath-Query>** vous permet de spécifier une requête XPath sur la vue XML définie par le schéma annoté. Le schéma annoté sur lequel la requête XPath doit être exécutée est identifié à l’aide de `mapping-schema` l’attribut de l' ** \<élément SQL : XPath-Query>** .  
  
 Les modèles sont des documents XML valides qui contiennent une ou plusieurs requêtes. Les requêtes XPath et FOR XML retournent un fragment de document. Les modèles servent de conteneurs pour les fragments de documents ; par conséquent, les modèles offrent un moyen de spécifier un élément unique, de niveau supérieur.  
  
 Les exemples de cette rubrique utilisent des modèles pour spécifier une requête XPath portant sur un schéma annoté afin de récupérer des données dans la base de données.  
  
 Considérons par exemple ce schéma annoté :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID" type="xsd:string" />   
       <xsd:attribute name="FirstName" type="xsd:string" />   
       <xsd:attribute name="LastName"  type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Pour les besoins de l'exemple, ce schéma XSD est stocké dans le fichier nommé Schema2.xml. Vous pouvez alors exécuter une requête XPath sur le schéma annoté spécifié dans le fichier modèle suivant (Schema2T.xml) :  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql"  
     >  
          Person.Contact[@ContactID="1"]  
</sql:xpath-query>  
```  
  
 Vous pouvez ensuite créer et utiliser le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter la requête dans le cadre d'un fichier modèle. Pour plus d’informations, consultez [schémas XDR Annotés &#40;déconseillés dans SQLXML 4,0&#41;](annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="using-inline-mapping-schemas"></a>Utilisation de schémas de mappage insérés  
 Un schéma annoté peut être inclus directement dans un modèle ; une requête XPath peut ensuite être spécifiée dans le modèle par rapport au schéma inséré. Le modèle peut également être un code de mise à jour (updategram).  
  
 Un modèle peut inclure plusieurs schémas insérés. Pour utiliser un schéma inline inclus dans un modèle, spécifiez l’attribut **ID** avec une valeur unique sur l' ** \<élément xsd : Schema>** , puis utilisez **#idvalue** pour référencer le schéma Inline. L’attribut **ID** est identique en ce qui concerne le comportement de **SQL : ID** ({urn : schemas-microsoft-com : XML-SQL} ID) utilisé dans les schémas XDR.  
  
 Par exemple, le modèle suivant spécifie deux schémas annotés insérés :  
  
```  
<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'>  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema1' sql:is-mapping-schema='1'>  
  <xsd:element name='Employees' ms:relation='HumanResources.Employee'>  
    <xsd:complexType>  
      <xsd:attribute name='LoginID'   
                     type='xsd:string'/>  
      <xsd:attribute name='Title'   
                     type='xsd:string'/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
        xmlns:ms='urn:schemas-microsoft-com:mapping-schema'  
        id='InLineSchema2' sql:is-mapping-schema='1'>  
  <xsd:element name='Contacts' ms:relation='Person.Contact'>  
    <xsd:complexType>  
  
      <xsd:attribute name='ContactID'   
                     type='xsd:string' />  
      <xsd:attribute name='FirstName'   
                     type='xsd:string' />  
      <xsd:attribute name='LastName'   
                     type='xsd:string' />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema1'>  
    /Employees[@LoginID='adventure-works\guy1']  
</sql:xpath-query>  
  
<sql:xpath-query xmlns:sql='urn:schemas-microsoft-com:xml-sql'   
        mapping-schema='#InLineSchema2'>  
    /Contacts[@ContactID='1']  
</sql:xpath-query>  
</ROOT>  
```  
  
 Le modèle spécifie également deux requêtes XPath. Chaque élément ** \<XPath-Query>** identifie de façon unique le schéma de mappage en spécifiant `mapping-schema` l’attribut.  
  
 Lorsque vous spécifiez un schéma inline dans le modèle, `sql:is-mapping-schema` l’annotation doit également être spécifiée sur l' ** \<élément xsd : Schema>** . `sql:is-mapping-schema` accepte une valeur booléenne (0 = false, 1 = true). Un schéma Inline avec **SQL : is-mapping-schema = "1"** est traité comme un schéma annoté inline et n’est pas retourné dans le document XML.  
  
 L'annotation `sql:is-mapping-schema` appartient à l'espace de noms du modèle `urn:schemas-microsoft-com:xml-sql`.  
  
 Pour tester cet exemple, enregistrez le modèle (InlineSchemaTemplate.xml) dans un répertoire local, puis créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) afin d'exécuter le modèle. Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Outre la spécification de l' `mapping-schema` attribut sur l’élément ** \<SQL : XPath-Query>** dans un modèle (lorsqu’il existe une requête XPath), ou sur ** \<l’élément attribut updg : Sync>** dans un mise à jour, vous pouvez effectuer les opérations suivantes :  
  
-   Spécifiez `mapping-schema` l’attribut sur l' ** \<élément racine>** (déclaration globale) dans le modèle. Ce schéma de mappage devient ensuite le schéma par défaut utilisé par l'ensemble des nœuds XPath et nœuds de code de mise à jour (updategram) qui n'ont pas d'annotation `mapping-schema` explicite.  
  
-   Spécifiez l'attribut `mapping schema` en utilisant l'objet `Command` ADO.  
  
 L' `mapping-schema` attribut qui est spécifié sur l' ** \<élément XPath-Query>** ou ** \<attribut updg : Sync>** a la priorité la plus élevée ; l’objet `Command` ADO a la priorité la plus faible.  
  
 Notez que si vous spécifiez une requête XPath dans un modèle et que vous ne spécifiez pas de schéma de mappage sur lequel la requête XPath est exécutée, la requête XPath est traitée comme une requête de type **dbobject** . Considérons par exemple le modèle suivant :  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 Le modèle spécifie une requête XPath mais ne spécifie pas de schéma de mappage. Par conséquent, cette requête est traitée comme une requête de type **dbobject** dans laquelle production. ProductPhoto est le nom @ProductPhotoIDde la table et = « 100 » est un prédicat qui recherche une photo du produit avec la valeur d’ID 100. @LargePhotocolonne à partir de laquelle la valeur doit être récupérée.  
  
  

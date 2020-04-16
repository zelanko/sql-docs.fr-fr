---
title: Utilisation de schémas XSD annotés dans les requêtes (SQLXML)
description: Découvrez comment spécifier les requêtes XPath contre un schéma XSD annoté dans SQLXML 4.0 pour récupérer les données de la base de données.
ms.date: 01/11/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e9ecd9d65d0f70f7c25328c15bb886ca52122de2
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388681"
---
# <a name="using-annotated-xsd-schemas-in-queries-sqlxml-40"></a>Utilisation de schémas XSD annotés dans les requêtes (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Vous pouvez spécifier des requêtes sur un schéma annoté afin de récupérer des données de la base de données ; pour ce faire, spécifiez des requêtes XPath dans un modèle par rapport au schéma XSD.  
  
 ** \<L’élément sql:xpath-query>** vous permet de spécifier une requête XPath par rapport à la vue XML qui est définie par le schéma annoté. Le schéma annoté contre lequel la requête XPath doit être exécutée est identifié en utilisant **l’attribut de cartographie-schéma** de ** \<l’élément sql:xpath-query>.**  
  
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
  
 Vous pouvez ensuite créer et utiliser le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter la requête dans le cadre d'un fichier modèle. Pour plus d’informations, voir [Annotated XDR Schemas &#40;Déprécié dans SQLXML 4.0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="using-inline-mapping-schemas"></a>Utilisation de schémas de mappage insérés  
 Un schéma annoté peut être inclus directement dans un modèle ; une requête XPath peut ensuite être spécifiée dans le modèle par rapport au schéma inséré. Le modèle peut également être un code de mise à jour (updategram).  
  
 Un modèle peut inclure plusieurs schémas insérés. Pour utiliser un schéma inline qui est inclus dans un modèle, spécifiez **l’attribut d’id** avec une valeur unique sur ** \<l’élément xsd:schema>,** puis utilisez **#idvalue** pour référencer le schéma inline. **L’attribut d’id** est identique dans le comportement à la **sql: id** (urn:schemas-microsoft-com:xml-sql-id) utilisé dans les schémas XDR.  
  
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
  
 Le modèle spécifie également deux requêtes XPath. Chacun des ** \<éléments de>xpath-requête** identifie uniquement le schéma de cartographie en spécifiant **l’attribut de cartographie-schéma.**  
  
 Lorsque vous spécifiez un schéma inline dans le modèle, **l’annotation sql:is-mapping-schema** doit également être spécifiée sur ** \<l’élément xsd:schema>.** Le **sql: est-cartographie-schéma** prend une valeur Boolean (0-faux, 1-true). Un schéma inline avec **sql: is-mapping-schema"1"** est traité comme schéma annoté en ligne et n’est pas retourné dans le document XML.  
  
 Le **sql:is-mapping-schema** annotation appartient à l’urne nomspace **modèle:schemas-microsoft-com:xml-sql**.  
  
 Pour tester cet exemple, enregistrez le modèle (InlineSchemaTemplate.xml) dans un répertoire local, puis créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) afin d'exécuter le modèle. Pour plus d’informations, voir [Utiliser ADO pour exécuter SQLXML 4.0 Requêtes](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 En plus de spécifier **l’attribut de cartographie-schéma** sur le ** \<sql:xpath-requête>** élément dans un modèle (quand il ya une requête XPath), ou sur ** \<updg:sync>** élément dans un updategram, vous pouvez faire ce qui suit:  
  
-   Spécifiez **l’attribut de cartographie-schéma** sur l’élément ** \<>ROOT** (déclaration globale) dans le modèle. Ce schéma de cartographie devient alors le schéma par défaut qui sera utilisé par tous les nœuds XPath et updategram qui n’ont pas d’annotation explicite **de cartographie-schéma.**  
  
-   Spécifier l’attribut **de schéma de cartographie** en utilisant l’objet ADO **Command.**  
  
 **L’attribut de cartographie-schéma** qui est spécifié sur le ** \<xpath-query>** ou ** \<updg:sync>** élément a la plus haute préséance; l’objet ADO **Command** a la priorité la plus basse.  
  
 Notez que si vous spécifiez une requête XPath dans un modèle et ne spécifiez pas un schéma de cartographie contre lequel la requête XPath est exécutée, la requête XPath est traitée comme une requête de type **dbobject.** Considérons par exemple le modèle suivant :  
  
```  
<sql:xpath-query   
     xmlns:sql="urn:schemas-microsoft-com:xmlsql">  
          Production.ProductPhoto[@ProductPhotoID='100']/@LargePhoto  
</sql:xpath-query>  
```  
  
 Le modèle spécifie une requête XPath mais ne spécifie pas de schéma de mappage. Par conséquent, cette requête est traitée comme une requête de type **dbobject** @ProductPhotoIDdans laquelle Production.ProductPhoto est le nom de table et '100' est un prédicat qui trouve une photo de produit avec la valeur d’identification de 100. @LargePhotoest la colonne à partir de laquelle récupérer la valeur.  
  
  

---
title: Masquage d'éléments et d'attributs à l'aide de sql:hide
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- hiding elements
- element mapping [SQLXML], hiding attributes and elements
- hide annotation
- sql:hide
- table/view mapping [SQLXML], hiding attributes and elements
- table mapping [SQLXML], hiding attributes and elements
- hiding attributes
- annotated XSD schemas, hiding attributes and elements
- attribute mapping [SQLXML], hiding attributes and elements
- column mapping [SQLXML]
- element hiding [SQLXML]
- XSD schemas [SQLXML], hiding attributes and elements
- attribute hiding [SQLXML]
ms.assetid: 0978301b-f068-46b6-82b9-dc555161f52e
author: MightyPen
ms.author: genemi
ms.reviewer: ''
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 670b11e86498116549c395c47364604e72b790a4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75246862"
---
# <a name="hiding-elements-and-attributes-by-using-sqlhide"></a>Masquage d'éléments et d'attributs à l'aide de sql:hide
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Lorsqu'une requête XPath est exécutée contre un schéma XSD, le document XML résultant possède des éléments et des attributs spécifiés dans le schéma. Vous pouvez spécifier que certains éléments et attributs soient masqués dans le schéma à l’aide de l’annotation **SQL : Hide** . Cela est utile lorsque les critères de sélection de la requête requièrent des éléments ou des attributs particuliers dans le schéma, mais que vous ne souhaitez pas les retourner dans le document XML généré.  
  
 L’annotation **SQL : Hide** prend une valeur booléenne (0 = false, 1 = true). Les valeurs acceptables sont 0, 1, true et false.  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l'aide des exemples suivants, vous devez répondre à certaines conditions requises. Pour plus d’informations, consultez [Configuration requise pour l’exécution d’exemples SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlhide-on-an-attribute"></a>R. Spécification de sql:hide sur un attribut  
 Dans cet exemple, le schéma XSD se compose d’un ** \<élément person. contact>** avec les attributs **ContactID**, **FirstName**et **LastName** .  
  
 L' ** \<élément person. contact>** est de type complexe et, par conséquent, est mappé à la table du même nom (mappage par défaut). Tous les attributs de ** \<l’élément person. contact>** sont de type simple et sont mappés à des colonnes portant le même nom dans Person. Contacttable dans la base de données AdventureWorks. Dans le schéma, l’annotation **SQL : Hide** est spécifiée sur l’attribut **ContactID** . Lorsqu’une requête XPath est spécifiée sur ce schéma, le **ContactID** n’est pas renvoyé dans le document XML.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact" >  
     <xsd:complexType>  
       <xsd:attribute name="ContactID"  sql:hide="true" />   
       <xsd:attribute name="FirstName"   type="xsd:string" />   
       <xsd:attribute name="LastName"    type="xsd:string" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom Hide.xml.  
  
2.  Copiez le modèle suivant et collez-le dans un fichier texte. Enregistrez le fichier sous le nom HideT.xml dans le répertoire où vous avez enregistré le fichier Hide.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="Hide.xml">  
            /Person.Contact[@ContactID="1"]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (Hide.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\Hide.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici l'ensemble de résultats obtenu :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <Person.Contact FirstName="Gustavo" LastName="Achong" />   
</ROOT>  
```  
  
 Quand **SQL : Hide** est spécifié sur un élément, l’élément et ses attributs ou éléments enfants n’apparaissent pas dans le document XML généré. Voici un autre schéma XSD dans lequel **SQL : Hide** est spécifié sur l' ** \<élément OD>** :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:annotation>  
    <xsd:documentation>  
      Sales.Customer-Sales.SalesOrderHeader-Sales.SalesOrderDetail Schema  
      Copyright 2004 Microsoft. All rights reserved.  
    </xsd:documentation>  
    <xsd:appinfo>  
      <sql:relationship name="CustomerOrder"  
         parent="Sales.Customer"  
                  parent-key="CustomerID"  
                  child-key="CustomerID"  
                  child="Sales.SalesOrderHeader" />  
       <sql:relationship name="OrderOrderDetails"  
                  parent="Sales.SalesOrderHeader"  
                  parent-key="SalesOrderID"  
                  child-key="SalesOrderID"  
                  child="Sales.SalesOrderDetail"/>  
    </xsd:appinfo>  
  </xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Sales.Customer">  
    <xsd:complexType>  
      <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"   
                     maxOccurs="unbounded"   
                     sql:relationship="CustomerOrder">  
          <xsd:complexType>  
            <xsd:sequence>  
               <xsd:element name="OD" sql:relation="Sales.SalesOrderDetail"                                       maxOccurs="unbounded"                                       sql:relationship="OrderOrderDetails"                                       sql:hide="1">  
                  <xsd:complexType>  
                    <xsd:attribute name="SalesOrderID" type="xsd:string"/>  
                    <xsd:attribute name="ProductID" type="xsd:string"/>  
                  </xsd:complexType>  
               </xsd:element>  
            </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string"/>  
          <xsd:attribute name="OID" sql:field="SalesOrderID"   
                                    type="xsd:string"/>  
          <xsd:attribute name="OrderDate" type="xsd:date"/>   
        </xsd:complexType>  
      </xsd:element>  
    </xsd:sequence>  
    <xsd:attribute name="CID" sql:field="CustomerID"   
                                type="xsd:string"/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Lorsqu’une requête XPath (par exemple `/Customers[@CID="1"]`) est spécifiée par rapport à ce schéma, le document XML généré n’inclut pas l' ** \<élément OD>** et ses enfants, comme indiqué dans ce résultat partiel :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customers CID="1">  
    <Order CustomerID="1" OID="43860" OrderDate="2001-08-01" />   
    <Order CustomerID="1" OID="44501" OrderDate="2001-11-01" />   
    <Order CustomerID="1" OID="45283" OrderDate="2002-02-01" />   
    <Order CustomerID="1" OID="46042" OrderDate="2002-05-01" />   
  </Customers>  
</ROOT>  
```  
  
  

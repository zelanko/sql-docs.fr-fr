---
title: Exemple de schéma XSD annoté pour obtenir des exemples XPath (SQLXML 4.0) | Documents Microsoft
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
- XPath queries [SQLXML], annotated XSD schemas in queries
- annotated XSD schemas, samples
- annotated XSD schemas, queries
ms.assetid: fefa2cc8-2d3c-4336-aeae-ce063a3a8df2
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f4d8c06249a89f46317babc55b52eb45d8f6f8be
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140241"
---
# <a name="sample-annotated-xsd-schema-for-xpath-examples-sqlxml-40"></a>Exemple de schéma XSD annoté pour les exemples XPath (SQLXML 4.0)
  Les exemples de requêtes XPath de cette section font référence à un schéma de mappage. Le schéma de mappage est un fichier de schéma XML (XSD) annoté. Pour plus d’informations sur les schémas de mappage, consultez [Introduction aux schémas de XSD annoté &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md).  
  
 Les éléments suivants sont nécessaires pour exécuter des requêtes XPath sur un schéma XSD annoté :  
  
-   Créez un modèle contenant une requête XPath. Dans le modèle, vous spécifiez le schéma de mappage sur lequel la requête XPath doit être exécutée. Dans ce cas, le schéma de mappage doit être stocké dans le répertoire (ou l'un de ses sous-répertoires, auquel cas un chemin d'accès relatif est spécifié comme valeur de l'attribut `mapping-schema` dans le modèle) associé au fichier de modèle.  
  
-   Créez une application de test qui utilise des extensions SQLXML pour ADO pour exécuter des requêtes. Pour plus d’informations, consultez [à l’aide d’ADO pour exécuter des requêtes SQLXML 4.0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Dans tous les exemples de cette section, les requêtes XPath sont spécifiées dans un modèle et le modèle est exécuté à l'aide d'ADO. Par conséquent, vous devez utiliser le fichier de schéma de mappage SampleSchema1.xml. Enregistrez ce fichier dans le répertoire où vos modèles sont stockés.  
  
## <a name="sample-annotated-xsd-schema-sampleschema1xml"></a>Exemple de schéma XSD annoté (SampleSchema1.xml)  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="CustOrders"  
                        parent="Sales.Customer"  
                        parent-key="CustomerID"  
                        child="Sales.SalesOrderHeader"  
                        child-key="CustomerID" />  
      <sql:relationship name="OrderOrderDetail"  
                        parent="Sales.SalesOrderHeader"  
                        parent-key="SalesOrderID"  
                        child="Sales.SalesOrderDetail"  
                        child-key="SalesOrderID" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustOrders" />  
     </xsd:sequence>  
     <xsd:attribute name="CustomerID" type="xsd:ID"/>  
     <xsd:attribute name="TerritoryID"/>  
     <xsd:attribute name="AccountNumber"/>  
     <xsd:attribute name="CustomerType"/>  
     <xsd:attribute name="Orders" type="xsd:IDREFS" sql:prefix="Ord-"/>  
  </xsd:complexType>  
  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" type="OrderType"/>  
  
  <xsd:complexType name="OrderType">  
     <xsd:sequence>  
        <xsd:element name="OrderDetail"   
                     sql:relation="Sales.SalesOrderDetail"  
                     sql:relationship="OrderOrderDetail" />  
     </xsd:sequence>  
     <xsd:attribute name="SalesOrderID" type="xsd:ID" sql:prefix="Ord-"/>  
     <xsd:attribute name="SalesPersonID"/>  
     <xsd:attribute name="OrderDate"/>  
     <xsd:attribute name="DueDate"/>  
     <xsd:attribute name="ShipDate"/>  
  </xsd:complexType>  
  
  <xsd:element name="OrderDetail" sql:relation="Sales.SalesOrderDetail" type="OrderDetailType"/>  
  
  <xsd:complexType name="OrderDetailType">  
    <xsd:attribute name="ProductID" type="xsd:IDREF"/>  
    <xsd:attribute name="UnitPrice"/>  
    <xsd:attribute name="OrderQty"/>  
    <xsd:attribute name="UnitPriceDiscount"/>  
  </xsd:complexType>  
  
  <xsd:element name="UnitPriceDiscount" sql:relation="Sales.SalesOrderDetail" type="DiscountType"/>  
  
  <xsd:complexType name="DiscountType">  
    <xsd:simpleContent>  
       <xsd:extension base="xsd:string">  
          <xsd:anyAttribute namespace="##other" processContents="lax"/>  
       </xsd:extension>  
    </xsd:simpleContent>  
  </xsd:complexType>  
  
  <xsd:element name="Contact" sql:relation="Person.Contact" type="ContactType"/>  
  
  <xsd:complexType name="ContactType">  
    <xsd:attribute name="ContactID"/>  
    <xsd:attribute name="LastName"/>  
    <xsd:attribute name="FirstName"/>  
    <xsd:attribute name="Title"/>  
  </xsd:complexType>  
  
</xsd:schema>  
```  
  
  
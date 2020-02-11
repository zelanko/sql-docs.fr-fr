---
title: 'SQL : Relationship et la règle de classement des clés (SQLXML 4,0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- sql:relationship
- key ordering rules [SQLXML]
- relationship annotation
ms.assetid: 914cb152-09f5-4b08-b35d-71940e4e9986
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 521614f8755261d0348ab95132c527c736c96311
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013508"
---
# <a name="sqlrelationship-and-the-key-ordering-rule-sqlxml-40"></a>sql:relationship et la règle de tri par clé (SQLXML 4.0)
  Dans la mesure où la fonctionnalité de chargement en masse XML génère des enregistrements lorsque les nœuds de ces derniers entrent dans l'étendue, et qu'elle envoie ces enregistrements à Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lorsque les nœuds correspondants sortent de l'étendue, les données de l'enregistrement doivent être présentes dans l'étendue du nœud.  
  
 Prenons le schéma XSD suivant, dans lequel la relation un-à-plusieurs entre ** \<les>client** et ** \<** les éléments de>de commande (un client peut passer plusieurs commandes) est `<sql:relationship>` spécifiée à l’aide de l’élément :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"<>   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustCustOrder"  
          parent="Cust"  
          parent-key="CustomerID"  
          child="CustOrder"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customers" sql:relation="Cust" >  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="CustomerID"  type="xsd:integer" />  
       <xsd:element name="CompanyName" type="xsd:string" />  
       <xsd:element name="City"        type="xsd:string" />  
       <xsd:element name="Order"   
                          sql:relation="CustOrder"  
                          sql:relationship="CustCustOrder" >  
         <xsd:complexType>  
          <xsd:attribute name="OrderID" type="xsd:integer" />  
         </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Lorsque le nœud de l’élément ** \<>du client** entre dans l’étendue, le chargement en masse XML génère un enregistrement de client. Cet enregistrement reste jusqu’à ce que le chargement en masse XML Lise ** \</Customer>**. Lors du traitement de l' ** \<ordre>** nœud d’élément, le `<sql:relationship>` chargement en masse XML utilise pour obtenir la valeur de la colonne de clé étrangère CustomerID de la table CustOrder à partir de l' ** \<élément parent>client** , car l' ** \<élément Order>** ne spécifie pas l’attribut **CustomerID** . Cela signifie que lors de la définition de l' `<sql:relationship>` ** \<élément Customer>** , vous devez spécifier l’attribut **CustomerID** dans le schéma avant de spécifier. Dans le cas contraire, lorsqu’une ** \<commande>** élément entre dans l’étendue, le chargement en masse XML génère un enregistrement pour la table CustOrder et, lorsque le chargement en masse XML atteint la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ** \<** balise de fin de la>/Order, il envoie l’enregistrement à sans la valeur de la colonne de clé étrangère CustomerID.  
  
 Enregistrez le schéma fourni dans cet exemple sous le nom SampleSchema.xml.  
  
### <a name="to-test-a-working-sample"></a>Pour tester un exemple fonctionnel  
  
1.  Créez les tables suivantes :  
  
    ```  
    CREATE TABLE Cust (  
                  CustomerID     int          PRIMARY KEY,  
               CompanyName    varchar(20)  NOT NULL,  
                  City           varchar(20)  DEFAULT 'Seattle')  
    GO  
    CREATE TABLE CustOrder (  
                  OrderID        varchar(10) PRIMARY KEY,  
               CustomerID     int         FOREIGN KEY REFERENCES                                          Cust(CustomerID))  
    GO  
    ```  
  
2.  Enregistrez l'exemple de données ci-après sous le nom SampleXMLData.xml :  
  
    ```  
    <ROOT>    
      <Customers>  
        <CompanyName>Hanari Carnes</CompanyName>  
        <City>NY</City>  
        <Order OrderID="1" />  
        <Order OrderID="2" />  
        <CustomerID>1111</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Toms Spezialitten</CompanyName>  
         <City>LA</City>    
        <Order OrderID="3" />  
        <CustomerID>1112</CustomerID>  
      </Customers>  
      <Customers>  
        <CompanyName>Victuailles en stock</CompanyName>  
        <Order OrderID="4" />  
        <CustomerID>1113</CustomerID>  
      </Customers>  
    </ROOT>  
    ```  
  
3.  Pour effectuer le chargement en masse XML, enregistrez l'exemple [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic Scripting Edition (VBScript) suivant sous le nom MySample.vbs, puis exécutez-le :  
  
    ```  
    set objBL = CreateObject("SQLXMLBulkLoad.SQLXMLBulkload.4.0")  
    objBL.ConnectionString = "provider=SQLOLEDB;data source=localhost;database=tempdb;integrated security=SSPI"  
    objBL.ErrorLogFile = "c:\error.log"  
    objBL.CheckConstraints = True  
    objBL.Transaction=True  
    objBL.Execute "c:\SampleSchema.xml", "c:\SampleXMLData.xml"  
    set objBL=Nothing  
    ```  
  
     Il en résulte que la fonctionnalité de chargement en masse XML insère une valeur NULL dans la colonne de clé étrangère CustomerID de la table CustOrder. Si vous révisez les exemples de données XML de ** \<** sorte que l’élément enfant CustomerID>apparaisse avant l' ** \<ordre>** élément enfant, vous obtenez le résultat attendu : le chargement en masse XML insère la valeur de clé étrangère spécifiée dans la colonne.  
  
 Voici le schéma XDR équivalent :  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"   
        xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
        xmlns:sql="urn:schemas-microsoft-com:xml-sql" >   
   <ElementType name="CustomerID"  />  
   <ElementType name="CompanyName" />  
   <ElementType name="City"        />  
  
   <ElementType name="root" sql:is-constant="1">  
      <element type="Customers" />  
   </ElementType>  
  
   <ElementType name="Customers" sql:relation="Cust" >  
      <element type="CustomerID" sql:field="CustomerID" />  
      <element type="CompanyName" sql:field="CompanyName" />  
      <element type="City" sql:field="City" />  
      <element type="Order" >  
                 <sql:relationship  
                        key-relation    ="Cust"  
                        key             ="CustomerID"  
                        foreign-key     ="CustomerID"  
                        foreign-relation="CustOrder" />  
      </element>  
   </ElementType>  
    <ElementType name="Order" sql:relation="CustOrder" >  
      <AttributeType name="OrderID" />  
      <AttributeType name="CustomerID" />  
      <attribute type="OrderID" />  
      <attribute type="CustomerID" />  
    </ElementType>  
</Schema>  
```  
  
  

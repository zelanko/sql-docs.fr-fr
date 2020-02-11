---
title: Schémas de mappage annotés pour un mise à jour (SQLXML)
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, updategrams
- data types [SQLXML], mapping schema in updategrams
- updategrams [SQLXML], annotated mapping schemas
- annotated XDR schemas, updategrams
- inverse attribute
- parent-child relationships [SQLXML]
- mapping-schema attribute
- mapping schema [SQLXML], updategrams
- sql:inverse
ms.assetid: 2e266ed9-4cfb-434a-af55-d0839f64bb9a
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 4feb8e282390b4808b69493a299cbad990f1e91b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75243569"
---
# <a name="specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-40"></a>Spécification d'un schéma de mappage annoté dans un code de mise à jour (updategram) (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Cette rubrique explique comment le schéma de mappage (XSD ou XDR) spécifié dans un code de mise à jour est utilisé pour traiter les mises à jour. Dans un mise à jour, vous pouvez fournir le nom d’un schéma de mappage annoté à utiliser pour mapper les éléments et les attributs du mise à jour aux tables et aux colonnes [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]dans. Lorsqu'un schéma de mappage est spécifié dans un code de mise à jour, les noms d'élément et d'attribut spécifiés dans le code de mise à jour doivent être mappés aux éléments et aux attributs dans le schéma de mappage.  
  
 Pour spécifier un schéma de mappage, vous utilisez l’attribut **mapping-schema** de l' ** \<élément Sync>** . Les exemples suivants présentent deux codes de mise à jour : l'un utilise un schéma de mappage simple et l'autre utilise un schéma plus complexe.  
  
> [!NOTE]  
>  Cette documentation suppose une connaissance suffisante des modèles et de la prise en charge des schémas de mappage dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Introduction aux schémas XSD Annotés &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md). Pour les applications héritées qui utilisent XDR, consultez [schémas XDR Annotés &#40;dépréciés dans SQLXML 4,0&#41;](../../../relational-databases/sqlxml/annotated-xsd-schemas/annotated-xdr-schemas-deprecated-in-sqlxml-4-0.md).  
  
## <a name="dealing-with-data-types"></a>Traitement des types de données  
 Si le schéma spécifie le type de données **image**, **Binary**ou **varbinary** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (à l’aide de **SQL : DataType**) et qu’il ne spécifie pas de type de données XML, mise à jour suppose que le type de données XML est **Binary base 64**. Si vos données sont de type **bin. base** , vous devez spécifier explicitement le type (**DT : type = bin. base** ou **type = "xsd : hexBinary"**).  
  
 Si le schéma spécifie le type de données XSD **DateTime**, **Date**ou **Time** , vous devez également spécifier le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] type de données correspondant à l’aide de **SQL : datatype = "DateTime"**.  
  
 Lors du traitement des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] paramètres de type **Money** , vous devez spécifier explicitement **SQL : datatype = "Money"** sur le nœud approprié dans le schéma de mappage.  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l’aide des exemples suivants, vous devez respecter les exigences spécifiées dans la [Configuration requise pour l’exécution d’exemples SQLXML](../../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-creating-an-updategram-with-a-simple-mapping-schema"></a>R. Création d'un code de mise à jour avec un schéma de mappage simple  
 Le schéma XSD suivant (SampleSchema. Xml) est un schéma de mappage qui mappe l' ** \<élément Customer>** à la table Sales. Customer :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
        <xsd:attribute name="CustID"    
                       sql:field="CustomerID"   
                       type="xsd:string" />  
        <xsd:attribute name="RegionID"    
                       sql:field="TerritoryID"    
                       type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Le code de mise à jour suivant insère un enregistrement dans la table Sales.Customer et compte sur le schéma de mappage précédent pour mapper correctement ces données à la table. Notez que le mise à jour utilise le même nom d’élément, ** \<>client **, comme défini dans le schéma. C'est absolument essentiel dans la mesure où le code de mise à jour spécifie un schéma particulier.  
  
##### <a name="to-test-the-updategram"></a>Pour tester le code de mise à jour  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom SampleUpdateSchema.xml.  
  
2.  Copiez le modèle de code de mise à jour ci-dessous et collez-le dans un fichier texte. Enregistrez le fichier sous le nom SampleUpdategram.xml dans le répertoire où vous avez enregistré le fichier SampleUpdateSchema.xml.  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleUpdateSchema.xml">  
        <updg:before>  
          <Customer CustID="1" RegionID="1"  />  
        </updg:before>  
        <updg:after>  
          <Customer CustID="1" RegionID="2" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (SampleUpdateSchema.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le schéma XDR équivalent :  
  
```  
<?xml version="1.0" ?>  
   <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
         xmlns:dt="urn:schemas-microsoft-com:datatypes"   
         xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
     <ElementType name="Customer" sql:relation="Sales.Customer" >  
       <AttributeType name="CustID" />  
       <AttributeType name="RegionID" />  
  
       <attribute type="CustID" sql:field="CustomerID" />  
       <attribute type="RegionID" sql:field="TerritoryID" />  
     </ElementType>  
   </Schema>   
```  
  
### <a name="b-inserting-a-record-by-using-the-parent-child-relationship-specified-in-the-mapping-schema"></a>B. Insertion d'un enregistrement à l'aide de la relation parent-enfant spécifiée dans le schéma de mappage  
 Les éléments du schéma peuvent être liés. L' ** \<élément SQL : Relationship>** spécifie la relation parent-enfant entre les éléments de schéma. Ces informations sont utilisées pour mettre à jour les tables correspondantes qui ont une relation clé primaire/clé étrangère.  
  
 Le schéma de mappage suivant (SampleSchema. Xml) se compose de deux éléments : ** \<Order>** et ** \<OD>**:  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="OD"   
                     sql:relation="Sales.SalesOrderDetail"  
                     sql:relationship="OrderOD" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID"   type="xsd:integer" />  
              <xsd:attribute name="ProductID" type="xsd:integer" />  
             <xsd:attribute name="UnitPrice"  type="xsd:decimal" />  
             <xsd:attribute name="OrderQty"   type="xsd:integer" />  
             <xsd:attribute name="UnitPriceDiscount"   type="xsd:decimal" />  
  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesOrderID"  type="xsd:integer" />  
        <xsd:attribute name="OrderDate"  type="xsd:date" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Le mise à jour suivant utilise ce schéma XSD pour ajouter un nouvel enregistrement de détail de commande (un ** \<élément OD>** dans le bloc ** \<after>** ) pour la commande 43860. L’attribut **mapping-schema** est utilisé pour spécifier le schéma de mappage dans le mise à jour.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before>  
       <Order SalesOrderID="43860" />  
    </updg:before>  
    <updg:after>  
      <Order SalesOrderID="43860" >  
           <OD ProductID="753" UnitPrice="$10.00"  
               Quantity="5" Discount="0.0" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Pour tester le code de mise à jour  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom SampleUpdateSchema.xml.  
  
2.  Copiez le modèle de code de mise à jour (updategram) ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom SampleUpdategram.xml dans le répertoire où vous avez enregistré le fichier SampleUpdateSchema.xml.  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (SampleUpdateSchema.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le schéma XDR équivalent :  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="OD" sql:relation="Sales.SalesOrderDetail" >  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="ProductID" />  
    <AttributeType name="UnitPrice"  dt:type="fixed.14.4" />  
    <AttributeType name="OrderQty" />  
    <AttributeType name="UnitPriceDiscount" />  
  
    <attribute type="SalesOrderID" />  
    <attribute type="ProductID" />  
    <attribute type="UnitPrice" />  
    <attribute type="OrderQty" />  
    <attribute type="UnitPriceDiscount" />  
</ElementType>  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader" >  
    <AttributeType name="CustomerID" />  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="OrderDate" />  
  
    <attribute type="CustomerID" />  
    <attribute type="SalesOrderID" />  
    <attribute type="OrderDate" />  
    <element type="OD" >  
             <sql:relationship   
                   key-relation="Sales.SalesOrderHeader"  
                   key="SalesOrderID"  
                   foreign-key="SalesOrderID"  
                   foreign-relation="Sales.SalesOrderDetail" />  
    </element>  
</ElementType>  
</Schema>  
```  
  
### <a name="c-inserting-a-record-by-using-the-parent-child-relationship-and-inverse-annotation-specified-in-the-xsd-schema"></a>C. Insertion d'un enregistrement à l'aide de la relation parent-enfant et de l'annotation inverse spécifiées dans le schéma XSD  
 Cet exemple montre comment la logique mise à jour utilise la relation parent-enfant spécifiée dans le XSD pour traiter les mises à jour, et comment l’annotation **inverse** est utilisée. Pour plus d’informations sur l’annotation **inverse** , consultez [spécification de l’attribut SQL : inverse sur sql : relationship &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md).  
  
 Cet exemple suppose que les tables suivantes se trouvent dans la base de données **tempdb** :  
  
-   
  `Cust (CustomerID, CompanyName)`, où `CustomerID` est la clé primaire  
  
-   
  `Ord (OrderID, CustomerID)`, où `CustomerID` est une clé étrangère qui fait référence à la clé primaire `CustomerID` dans la table `Cust`.  
  
 Le code de mise à jour utilise le schéma XSD suivant pour insérer des enregistrements dans les tables Cust et Ord :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
       <sql:relationship name="OrdCust" inverse="true"  
                  parent="Ord"  
                  parent-key="CustomerID"  
                  child-key="CustomerID"  
                  child="Cust"/>  
  </xsd:appinfo>  
</xsd:annotation>  
  
<xsd:element name="Order" sql:relation="Ord">  
  <xsd:complexType>  
    <xsd:sequence>  
      <xsd:element ref="Customer" sql:relationship="OrdCust"/>  
    </xsd:sequence>  
    <xsd:attribute name="OrderID"   type="xsd:int"/>  
    <xsd:attribute name="CustomerID" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
<xsd:element name="Customer" sql:relation="Cust">  
  <xsd:complexType>  
     <xsd:attribute name="CustomerID"  type="xsd:string"/>  
    <xsd:attribute name="CompanyName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:element>  
  
</xsd:schema>  
```  
  
 Dans cet exemple, le schéma XSD contient ** \<les éléments Customer>** et ** \<Order>** , et il spécifie une relation parent-enfant entre les deux éléments. Il identifie ** \<l’ordre>** en tant qu’élément parent et ** \<>client** comme élément enfant.  
  
 La logique de traitement du code de mise à jour utilise les informations relatives à la relation parent-enfant pour déterminer l'ordre dans lequel les enregistrements sont insérés dans les tables. Dans cet exemple, la logique mise à jour tente d’abord d’insérer un enregistrement dans la table Ord (car ** \<Order>** est le parent), puis tente d’insérer un enregistrement dans la table Cust (car ** \<Customer>** est l’enfant). Toutefois, en raison des informations de clé primaire/clé étrangère contenues dans le schéma de la table de base de données, cette opération d'insertion provoque une violation de clé étrangère dans la base de données et échoue.  
  
 Pour indiquer à la logique mise à jour d’inverser la relation parent-enfant au cours de l’opération de mise à jour, l’annotation **inverse** est spécifiée sur la ** \<relation>** élément. En conséquence, les enregistrements sont d'abord ajoutés dans la table Cust, puis dans la table Ord, et l'opération réussit.  
  
 Le code de mise à jour suivant insère une commande (OrderID=2) dans la table Ord et un client (CustomerID='AAAAA') dans la table Cust à l'aide du schéma XSD spécifié :  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="SampleUpdateSchema.xml" >  
    <updg:before/>  
    <updg:after>  
      <Order OrderID="2" CustomerID="AAAAA" >  
        <Customer CustomerID="AAAAA" CompanyName="AAAAA Company" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Pour tester le code de mise à jour  
  
1.  Créez ces tables dans la base de données **tempdb** :  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust(CustomerID varchar(5) primary key,   
                      CompanyName varchar(20))  
    GO  
    CREATE TABLE Ord (OrderID int primary key,   
                      CustomerID varchar(5) references Cust(CustomerID))  
    GO  
    ```  
  
2.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom SampleUpdateSchema.xml.  
  
3.  Copiez le modèle de code de mise à jour (updategram) ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom SampleUpdategram.xml dans le répertoire où vous avez enregistré le fichier SampleUpdateSchema.xml.  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (SampleUpdateSchema.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\SqlXmlTest\SampleUpdateSchema.xml"  
    ```  
  
4.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur la sécurité mise à jour &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  

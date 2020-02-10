---
title: 'Spécification de relations à l’aide de SQL : Relationship (SQLXML 4,0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREFS relationships [SQLXML]
- parent attribute [SQLXML]
- element relationships [SQLXML]
- multiple element relationships
- attribute relationships [SQLXML]
- sql:relationship
- relationship chains [SQLXML]
- IDREF relationships [SQLXML]
- parent-child relationships [SQLXML]
- relationship annotation
- XSD schemas [SQLXML], relationships
- annotated XSD schemas, relationships
- relationships [SQLXML], specifying
- unnamed relationships
- ID relationships [SQLXML]
- hierarchical relationships [SQLXML]
- named relationships [SQLXML]
ms.assetid: 98820afa-74e1-4e62-b336-6111a3dede4c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f27b47ae8216fa64b537d4c8b22b612c535a1869
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66013673"
---
# <a name="specifying-relationships-using-sqlrelationship-sqlxml-40"></a>Spécification de relations à l'aide de sql:relationship (SQLXML 4.0)
  Les éléments d'un document XML peuvent être liés. Les éléments peuvent être imbriqués hiérarchiquement ; en outre, des relations ID, IDREF ou IDREFS peuvent être spécifiées entre les éléments.  
  
 Par exemple, dans un schéma XSD, un ** \<élément Customer>** contient ** \<l’ordre>** éléments enfants. Lorsque le schéma est mappé à la base de données AdventureWorks, l' ** \<élément Customer>** est mappé à la table Sales. Customer et l' ** \<élément Order>** est mappé à la table Sales. SalesOrderHeader. Ces tables sous-jacentes, Sales.Customer et Sales.SalesOrderHeader, sont liées, car les clients passent des commandes. CustomerID dans la table Sales.SalesOrderHeader est une clé étrangère qui fait référence à la clé primaire CustomerID dans la table Sales.Customer. Vous pouvez établir ces relations entre les éléments de schéma de mappage `sql:relationship` à l’aide de l’annotation.  
  
 Dans le schéma XSD annoté, l'annotation `sql:relationship` est utilisée pour imbriquer hiérarchiquement les éléments du schéma, en fonction des relations de clé primaire et de clé étrangère qui existent entre les tables sous-jacentes auxquelles les éléments sont mappés. En spécifiant l'annotation `sql:relationship`, vous devez identifier ce qui suit :  
  
-   La table parente (Sales.Customer) et la table enfant (Sales.SalesOrderHeader).  
  
-   La ou les colonnes qui composent la relation entre la table parente et la table enfant. Par exemple, la colonne CustomerID, qui apparaît à la fois dans la table parente et la table enfant.  
  
 Ces informations sont utilisées pour générer la hiérarchie appropriée.  
  
 Pour fournir les noms de tables et les informations de jointure nécessaires, les attributs suivants sont spécifiés dans l'annotation `sql:relationship`. Ces attributs sont valides uniquement avec l' ** \<élément SQL : Relationship>** :  
  
 **Nom**  
 Spécifie le nom unique de la relation.  
  
 **Parent**  
 Spécifie la relation parente (table). Il s'agit d'un attribut facultatif ; si l'attribut n'est pas spécifié, le nom de la table parente est obtenu à partir des informations contenues dans la hiérarchie enfant du document. Si le schéma spécifie deux hiérarchies parent-enfant qui utilisent les mêmes ** \<>SQL : Relationship** , mais des éléments parents différents, vous ne spécifiez pas l’attribut parent dans ** \<SQL : Relationship>**. Ces informations sont obtenues à partir de la hiérarchie du schéma.  
  
 **parent-key**  
 Spécifie la clé parente du parent. Si la clé parente est composée de plusieurs colonnes, les valeurs sont spécifiées en étant séparées par un espace. Il existe un mappage de position entre les valeurs spécifiées pour la clé multicolonne et pour la clé enfant correspondante.  
  
 **Enfant**  
 Spécifie la relation enfant (table).  
  
 **child-key**  
 Spécifie la clé enfant de l'enfant faisant référence à la clé parente du parent. Si la clé enfant est composée de plusieurs attributs (colonnes), les valeurs de child-key sont spécifiées en étant séparées par un espace. Il existe un mappage de position entre les valeurs spécifiées pour la clé multicolonne et pour la clé parente correspondante.  
  
 **Inverse**  
 Cet attribut spécifié sur ** \<SQL : Relationship>** est utilisé par codes. Pour plus d’informations, consultez [spécification de l’attribut SQL : inverse sur SQL : Relationship](specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md).  
  
 L' `sql:key-fields` annotation doit être spécifiée dans un élément qui contient un élément enfant, qui a une ** \<>SQL : Relationship** définie entre l’élément et l’enfant, et qui ne fournit pas la clé primaire de la table spécifiée dans l’élément parent. Même si le schéma ne spécifie ** \<pas SQL : Relationship>**, vous devez `sql:key-fields` spécifier pour produire la hiérarchie appropriée. Pour plus d’informations, consultez [identification des colonnes clés à l’aide de SQL : key-fields](identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md).  
  
 Pour produire une imbrication correcte dans le résultat, il est recommandé `sql:key-fields` de spécifier dans tous les schémas.  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l'aide des exemples suivants, vous devez répondre à certaines conditions requises. Pour plus d’informations, consultez [Configuration requise pour l’exécution d’exemples SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlrelationship-annotation-on-an-element"></a>R. Spécification de l'annotation sql:relationship sur un élément  
 Le schéma XSD annoté suivant comprend ** \<les éléments Customer>** et ** \<Order>** . L' ** \<élément Order>** est un élément enfant de l' ** \<élément Customer>** .  
  
 Dans le schéma, l' `sql:relationship` annotation est spécifiée sur la ** \<commande>** élément enfant. La relation elle-même est définie dans l' ** \<élément xsd : appinfo>** .  
  
 L' ** \<élément Relationship>** identifie CustomerID dans la table Sales. SalesOrderHeader comme une clé étrangère qui fait référence à la clé primaire CustomerID dans la table Sales. Customer. Par conséquent, les commandes appartenant à un client apparaissent en tant qu’élément enfant de cet ** \<élément>client** .  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                    sql:relationship="CustOrders" >  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
 Le schéma précédent utilise une relation nommée. Vous pouvez également spécifier une relation sans nom. Les résultats sont identiques.  
  
 Voici le schéma modifié dans lequel une relation sans nom est spécifiée :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer"  type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader">  
           <xsd:annotation>  
            <xsd:appinfo>  
              <sql:relationship   
                parent="Sales.Customer"  
                parent-key="CustomerID"  
                child="Sales.SalesOrderHeader"  
                child-key="CustomerID" />  
            </xsd:appinfo>  
           </xsd:annotation>  
           <xsd:complexType>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
           </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom sql-relationship.xml.  
  
2.  Copiez le modèle suivant ci-dessous et collez-le dans un fichier texte. Enregistrez le fichier sous le nom sql-relationshipT.xml dans le répertoire où vous avez enregistré le fichier sql-relationship.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-relationship.xml">  
            /Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (sql-relationship.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\sql-relationship.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici l'ensemble de résultats obtenu :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer CustomerID="1">   
    <Order OrderID="43860" CustomerID="1" />   
    <Order OrderID="44501" CustomerID="1" />   
    <Order OrderID="45283" CustomerID="1" />   
    <Order OrderID="46042" CustomerID="1" />   
  </Customer>   
</ROOT>  
```  
  
### <a name="b-specifying-a-relationship-chain"></a>B. Spécification d'une chaîne de relation  
 Pour cet exemple, vous souhaitez obtenir le document XML suivant à l'aide des données provenant de la base de données AdventureWorks :  
  
```  
<Order SalesOrderID="43659">  
  <Product Name="Mountain Bike Socks, M"/>   
  <Product Name="Sport-100 Helmet, Blue"/>  
  ...  
</Order>  
...  
```  
  
 Pour chaque commande de la table Sales. SalesOrderHeader, le document XML a une ** \<commande>** élément. Chaque ** \<élément Order>** contient une liste de ** \<produits>** éléments enfants, un pour chaque produit demandé dans la commande.  
  
 Pour spécifier un schéma XSD qui produit cette hiérarchie, vous devez indiquer deux relations : OrderOD et ODProduct. La relation OrderOD spécifie la relation parent-enfant entre les tables Sales.SalesOrderHeader et Sales.SalesOrderDetail. La relation ODProduct spécifie la relation entre les tables Sales.SalesOrderDetail et Production.Product.  
  
 Dans le schéma suivant, l' `msdata:relationship` annotation sur l' ** \<élément Product>** spécifie deux valeurs : OrderOD et ODProduct. L'ordre dans lequel ces valeurs sont spécifiées est important.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <msdata:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  
    <msdata:relationship name="ODProduct"  
          parent="Sales.SalesOrderDetail"  
          parent-key="ProductID"  
          child="Production.Product"  
          child-key="ProductID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Order" msdata:relation="Sales.SalesOrderHeader"   
               msdata:key-fields="SalesOrderID" type="OrderType" />  
   <xsd:complexType name="OrderType" >  
     <xsd:sequence>  
        <xsd:element name="Product" msdata:relation="Production.Product"   
                     msdata:key-fields="ProductID"  
                     msdata:relationship="OrderOD ODProduct">  
          <xsd:complexType>  
             <xsd:attribute name="Name" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="SalesOrderID"   type="xsd:integer" />   
    </xsd:complexType>  
</xsd:schema>  
```  
  
 Au lieu de spécifier une relation nommée, vous pouvez spécifier une relation anonyme. Dans ce cas, le contenu entier du ** \<>d’annotation **... /annotation>, qui décrit les deux relations, s’affiche sous la forme d’un élément enfant du ** \<produit>**. ** \< **  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  
  <xsd:element name="Order" msdata:relation="Sales.SalesOrderHeader"   
               msdata:key-fields="SalesOrderID" type="OrderType" />  
  
   <xsd:complexType name="OrderType" >  
     <xsd:sequence>  
        <xsd:element name="Product" msdata:relation="Production.Product"   
                     msdata:key-fields="ProductID" >  
         <xsd:annotation>  
          <xsd:appinfo>  
           <msdata:relationship   
               parent="Sales.SalesOrderHeader"  
               parent-key="SalesOrderID"  
               child="Sales.SalesOrderDetail"  
               child-key="SalesOrderID" />  
  
           <msdata:relationship   
               parent="Sales.SalesOrderDetail"  
               parent-key="ProductID"  
               child="Production.Product"  
               child-key="ProductID" />  
         </xsd:appinfo>  
       </xsd:annotation>  
       <xsd:complexType>  
          <xsd:attribute name="Name" type="xsd:string" />  
       </xsd:complexType>  
     </xsd:element>  
   </xsd:sequence>  
   <xsd:attribute name="SalesOrderID"   type="xsd:integer" />   
  </xsd:complexType>  
 </xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom relationshipChain.xml.  
  
2.  Copiez le modèle suivant ci-dessous et collez-le dans un fichier texte. Enregistrez le fichier sous le nom relationshipChainT.xml dans le répertoire où vous avez enregistré le fichier relationshipChain.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="relationshipChain.xml">  
            /Order  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (relationshipChain.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\relationshipChain.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici l'ensemble de résultats obtenu :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Order SalesOrderID="43659">  
    <Product Name="Mountain Bike Socks, M" />   
    <Product Name="Sport-100 Helmet, Blue" />   
    <Product Name="AWC Logo Cap" />   
    <Product Name="Long-Sleeve Logo Jersey, M" />   
    <Product Name="Long-Sleeve Logo Jersey, XL" />   
    ...  
  </Order>  
  ...  
</ROOT>  
```  
  
### <a name="c-specifying-the-relationship-annotation-on-an-attribute"></a>C. Spécification de l'annotation de relation sur un attribut  
 Dans cet exemple, le schéma comprend \<un élément customer> \<avec un CustomerID> élément enfant et un attribut attribut OrderIDList de type IDREFS. L' \<élément customer> est mappé à la table Sales. Customer dans la base de données AdventureWorks. Par défaut, l’étendue de ce mappage s’applique à tous les éléments ou attributs enfants `sql:relation` , sauf si est spécifié sur l’élément ou l’attribut enfant, auquel cas la relation de clé primaire/clé étrangère appropriée doit être définie à \<l’aide de la relation> élément. En outre, l'élément ou l'attribut enfant, qui spécifie la table distincte à l'aide de l'annotation `relation`, doit également spécifier l'annotation `relationship`.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
     </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" type="CustomerType" />  
   <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="CustomerID"   type="xsd:string" />   
     </xsd:sequence>  
     <xsd:attribute name="OrderIDList"   
                     type="xsd:IDREFS"   
                     sql:relation="Sales.SalesOrderHeader"   
                     sql:field="SalesOrderID"  
                     sql:relationship="CustOrders" >  
        </xsd:attribute>  
    </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom relationship-on-attribute.xml.  
  
2.  Copiez le modèle suivant et collez-le dans un fichier. Enregistrez le fichier sous le nom relationship-on-attributeT.xml dans le répertoire où vous avez enregistré le fichier relationship-on-attribute.xml. La requête dans le modèle sélectionne un client dont le CustomerID est 1.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="relationship-on-attribute.xml">  
        /Customer[CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (relationship-on-attribute.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\relationship-on-attribute.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici l'ensemble de résultats obtenu :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer OrderIDList="43860 44501 45283 46042">  
    <CustomerID>1</CustomerID>   
  </Customer>  
</ROOT>  
```  
  
### <a name="d-specifying-sqlrelationship-on-multiple-elements"></a>D. Spécification de sql:relationship sur plusieurs éléments  
 Dans cet exemple, le schéma XSD annoté contient les ** \<éléments Customer>**, ** \<Order>** et ** \<OrderDetail>** .  
  
 L' ** \<élément Order>** est un élément enfant de l' ** \<élément Customer>** . ** \<** **SQL : Relationship>est spécifié sur la commande \<**>élément enfant ; par conséquent, les commandes appartenant à un client apparaissent en tant qu’éléments enfants du ** \<>client **.  
  
 L' ** \<élément Order>** comprend l' ** \<élément enfant OrderDetail>** . ** \<** ** \<SQL : Relationship>** est spécifié sur l’élément enfant OrderDetail>, de sorte que les détails de la commande qui se rapportent à une commande apparaissent en tant qu’éléments enfants de cet ** \<ordre>** élément.  
  
```  
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
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"    
              sql:relationship="CustOrders" maxOccurs="unbounded" >  
          <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OrderDetail"   
                             sql:relation="Sales.SalesOrderDetail"   
                             sql:relationship="OrderOrderDetail"   
                             maxOccurs="unbounded" >  
                  <xsd:complexType>  
                    <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                    <xsd:attribute name="ProductID" type="xsd:string" />  
                    <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  </xsd:complexType>  
                </xsd:element>  
              </xsd:sequence>  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="OrderDate" type="xsd:date" />  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom relationship-multiple-elements.xml.  
  
2.  Copiez le modèle suivant et collez-le dans un fichier texte. Enregistrez le fichier sous le nom relationship-multiple-elementsT.xml dans le répertoire où vous avez enregistré le fichier relationship-multiple-elements.xml. La requête du modèle retourne des informations de commande pour un client dont CustomerID a la valeur 1 et SalesOrderID la valeur 43860.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="relationship-multiple-elements.xml">  
        /Customer[@CustomerID=1]/Order[@SalesOrderID=43860]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (relationship-multiple-elements.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\relationship-multiple-elements.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici l'ensemble de résultats obtenu :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1">  
     <OrderDetail SalesOrderID="43860" ProductID="761" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="770" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="758" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="765" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="732" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="762" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="738" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="768" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="753" OrderQty="2" />   
     <OrderDetail SalesOrderID="43860" ProductID="729" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="763" OrderQty="1" />   
     <OrderDetail SalesOrderID="43860" ProductID="756" OrderQty="1" />   
  </Order>  
</ROOT>  
```  
  
### <a name="e-specifying-the-sqlrelationship-without-the-parent-attribute"></a>E. Spécification de \<l'> SQL : Relationship sans l’attribut parent  
 Cet exemple illustre la spécification de l' ** \<>SQL : Relationship** sans l’attribut **parent** . Prenons par exemple les tables d'employés suivantes :  
  
```  
Emp1(SalesPersonID, FirstName, LastName, ReportsTo)  
Emp2(SalesPersonID, FirstName, LastName, ReportsTo)  
```  
  
 La vue XML suivante contient les ** \<éléments Emp1>** et ** \<EMP2>** qui sont mappés aux tables Sales. Emp1 et Sales. EMP2 :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="EmpOrders"  
          parent-key="SalesPersonID"  
          child="Sales.SalesOrderHeader"  
          child-key="SalesPersonID" />  
     </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Emp1" sql:relation="Sales.Emp1" type="EmpType" />  
  <xsd:element name="Emp2" sql:relation="Sales.Emp2" type="EmpType" />  
   <xsd:complexType name="EmpType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"   
                     sql:relationship="EmpOrders" >  
          <xsd:complexType>  
             <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
             <xsd:attribute name="CustomerID" type="xsd:string" />  
          </xsd:complexType>  
        </xsd:element>  
     </xsd:sequence>  
        <xsd:attribute name="SalesPersonID"   type="xsd:integer" />   
        <xsd:attribute name="LastName"   type="xsd:string" />   
    </xsd:complexType>  
  
</xsd:schema>  
```  
  
 Dans le schéma, les `EmpType` ** \<éléments Emp1>** et ** \<EMP2>** sont de type. Le type `EmpType` décrit une ** \<commande>** élément enfant et le ** \<>SQL : Relationship **correspondant. Dans ce cas, il n’existe aucun parent unique qui peut être identifié dans ** \<SQL : Relationship>** à l’aide de l’attribut **parent** . Dans ce cas, vous ne spécifiez pas l’attribut **parent** dans ** \<SQL : Relationship>**; les informations d’attribut **parent** sont obtenues à partir de la hiérarchie dans le schéma.  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Créez ces tables dans la base de données AdventureWorks :  
  
    ```  
    USE AdventureWorks  
    CREATE TABLE Sales.Emp1 (  
           SalesPersonID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    Go  
    CREATE TABLE Sales.Emp2 (  
           SalesPersonID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    Go  
    ```  
  
2.  Ajoutez ces exemples de données dans les tables :  
  
    ```  
    INSERT INTO Sales.Emp1 values (279, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Sales.Emp1 values (282, 'Andrew', 'Fuller',1)  
    INSERT INTO Sales.Emp1 values (276, 'Janet', 'Leverling',1)  
    INSERT INTO Sales.Emp2 values (277, 'Margaret', 'Peacock',3)  
    INSERT INTO Sales.Emp2 values (283, 'Steven', 'Devolio',4)  
    INSERT INTO Sales.Emp2 values (275, 'Nancy', 'Buchanan',5)  
    INSERT INTO Sales.Emp2 values (281, 'Michael', 'Suyama',6)  
    ```  
  
3.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom relationship-noparent.xml.  
  
4.  Copiez le modèle suivant et collez-le dans un fichier texte. Enregistrez le fichier sous le nom relationship-noparentT.xml dans le répertoire où vous avez enregistré le fichier relationship-noparent.xml. La requête dans le modèle sélectionne tous les \<éléments Emp1> (par conséquent, le parent est Emp1).  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="relationship-noparent.xml">  
            /Emp1  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (relationship-noparent.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\relationship-noparent.xml"  
    ```  
  
5.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici un jeu de résultats partiel :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
<Emp1 SalesPersonID="276" LastName="Leverling">  
  <Order SalesOrderID="43663" CustomerID="510" />   
  <Order SalesOrderID="43666" CustomerID="511" />   
  <Order SalesOrderID="43859" CustomerID="259" />  
  ...  
</Emp1>  
```  
  
  

---
title: 'Filtrage des valeurs à l’aide de SQL : limit-champ et SQL : limit-value (SQLXML 4.0) | Microsoft Docs'
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
- annotated XSD schemas, filtering values
- limiting values [SQLXML]
- limit-value annotation
- limit-field annotation
- sql:limit-field
- sql:limit-value
- filtering [SQLXML]
ms.assetid: c0f7ae92-eeec-430e-a66a-f22c3ae64a5e
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d2ae0fe5a6bc85a9c2535b65f1989a8d5cd72904
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37260555"
---
# <a name="filtering-values-using-sqllimit-field-and-sqllimit-value-sqlxml-40"></a>Filtrage de valeurs à l'aide des annotations sql:limit-field et sql:limit-value (SQLXML 4.0)
  Vous pouvez limiter les lignes qui sont retournées à partir d'une requête de base de données et d'après une valeur de limitation. Les annotations `sql:limit-field` et `sql:limit-value` sont utilisées pour identifier la colonne de base de données qui contient les valeurs de limitation et spécifier une valeur de limitation spécifique à utiliser pour filtrer les données retournées.  
  
 L'annotation `sql:limit-field` sert à identifier une colonne qui contient une valeur de limitation ; elle est autorisée dans chaque élément ou attribut mappé.  
  
 L'annotation `sql:limit-value` est utilisée pour spécifier la valeur limitée dans la colonne elle-même spécifiée dans une annotation `sql:limit-field`. L'annotation `sql:limit-value` est facultative. Si `sql:limit-value` n'est pas spécifiée, une valeur NULL est validée.  
  
> [!NOTE]  
>  Lors de l'utilisation d'une annotation `sql:limit-field` où la colonne SQL mappée est de type `real`, SQLXML 4.0 effectue une conversion sur l'annotation `sql:limit-value` comme spécifié dans les schémas XML sous la forme d'une valeur `nvarchar` spécifiée. Pour cela, les valeurs de limite décimales doivent être spécifiées à l'aide de la notation scientifique complète. Pour plus d'informations, consultez l'exemple B ci-dessous.  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l'aide de ces exemples, vous devez avoir installé les composants suivants :  
  
-   Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  
  
-   MDAC 2.6 ou version ultérieure  
  
 Dans ces exemples, les modèles sont utilisés pour spécifier des requêtes XPath par rapport au schéma de mappage XSD.  
  
### <a name="a-limiting-the-customer-addresses-returned-to-a-specific-address-type"></a>A. Limitation des adresses de clients retournées à un type d'adresse spécifique  
 Dans cet exemple, une base de données contient deux tables :  
  
-   Customer (CustomerID, CompanyName)  
  
-   Addresses (CustomerID, AddressType, StreetAddress)  
  
 Un client peut disposer d'une adresse de livraison et/ou d'une adresse de facturation. Les valeurs de la colonne AddressType sont Shipping et Billing.  
  
 Il s’agit du schéma de mappage dans lequel le **ShipTo** attribut de schéma est mappé à la colonne StreetAddress dans la relation Addresses. Les valeurs retournées pour cet attribut sont limitées uniquement aux adresses de livraison en spécifiant les annotations `sql:limit-field` et `sql:limit-value`. De même, le **BillTo** attribut de schéma retourne uniquement l’adresse de facturation d’un client.  
  
 Voici le schéma :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustAddr"  
        parent="Customer"  
        parent-key="CustomerID"  
        child="Addresses"  
        child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Customer" >  
   <xsd:complexType>  
        <xsd:sequence>  
        <xsd:element name="BillTo"   
                       type="xsd:string"   
                       sql:relation="Addresses"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="billing"  
                       sql:relationship="CustAddr" >  
        </xsd:element>  
        <xsd:element name="ShipTo"   
                       type="xsd:string"   
                       sql:relation="Addresses"   
                       sql:field="StreetAddress"  
                       sql:limit-field="AddressType"  
                       sql:limit-value="shipping"  
                       sql:relationship="CustAddr" >  
        </xsd:element>  
        </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:int" />   
        <xsd:attribute name="CompanyName"  type="xsd:string" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Créez deux tables dans le **tempdb** base de données :  
  
    ```  
    USE tempdb  
    CREATE TABLE Customer (CustomerID int primary key,   
                           CompanyName varchar(30))  
    CREATE TABLE Addresses(CustomerID int,   
                           StreetAddress varchar(50),  
                           AddressType varchar(10))  
    ```  
  
2.  Ajoutez les exemples de données :  
  
    ```  
    INSERT INTO Customer values (1, 'Company A')  
    INSERT INTO Customer values (2, 'Company B')  
  
    INSERT INTO Addresses values  
               (1, 'Obere Str. 57 Berlin', 'billing')  
    INSERT INTO Addresses values  
               (1, 'Avda. de la Constitución 2222 México D.F.', 'shipping')  
    INSERT INTO Addresses values  
               (2, '120 Hanover Sq., London', 'billing')  
    INSERT INTO Addresses values  
               (2, 'Forsterstr. 57, Mannheim', 'shipping')  
    ```  
  
3.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom LimitFieldValue.xml.  
  
4.  Créez le modèle suivant (LimitFieldValueT.xml) et enregistrez-le dans le même répertoire où vous avez enregistré le schéma (LimitFieldValue.xml) lors de l'étape précédente :  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="LimitFieldValue.xml">  
            /Customer  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (LimitFieldValue.xml) a trait au répertoire dans lequel le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\LimitFieldValue.xml"  
    ```  
  
5.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [à l’aide d’ADO pour exécuter des requêtes SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le résultat obtenu :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Customer CustomerID="1" CompanyName="Company A">   
     <BillTo>Obere Str. 57 Berlin</BillTo>   
     <ShipTo>Avda. de la Constitución 2222 México D.F.</ShipTo>   
  </Customer>   
  <Customer CustomerID="2" CompanyName="Company B">   
     <BillTo>120 Hanover Sq., London</BillTo>   
     <ShipTo>Forsterstr. 57, Mannheim</ShipTo>   
   </Customer>   
</ROOT>  
```  
  
### <a name="b-limiting-results-based-on-a-discount-value-of-type-real-data"></a>B. Limitation des résultats en fonction d'une valeur de remise de type de données real  
 Dans cet exemple, une base de données contient deux tables :  
  
-   Orders (OrderID)  
  
-   OrderDetails (OrderID, ProductID, UnitPrice, Quantity, Price, Discount)  
  
 Il s’agit du schéma de mappage dans lequel le **OrderID** attribut sur les détails de commande est mappé à la colonne OrderID dans la relation orders. Les valeurs qui sont retournées pour cet attribut sont limitées à celles qui ont une valeur de 2, 0000000e-001 (0,2) que celui spécifié pour le **Discount** attribut à l’aide de la `sql:limit-field` et `sql:limit-value` annotations.  
  
 Voici le schéma :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
   <xsd:appinfo>  
    <sql:relationship name="OrderOrderDetails"  
        parent="Orders"  
        parent-key="OrderID"  
        child="OrderDetails"  
        child-key="OrderID" />  
   </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="root" sql:is-constant="1">  
   <xsd:complexType>  
     <xsd:sequence>  
       <xsd:element name="Order" sql:relation="Orders" >  
          <xsd:complexType>  
             <xsd:sequence>  
                <xsd:element name="orderDetail"   
                       sql:relation="OrderDetails"   
                       sql:limit-field="Discount"                       sql:limit-value="2.0000000e-001"  
                       sql:relationship="OrderOrderDetails">  
                   <xsd:complexType>  
                     <xsd:attribute name="OrderID"   />   
                     <xsd:attribute name="ProductID" />   
                     <xsd:attribute name="Discount"  />   
                     <xsd:attribute name="Quantity"  />   
                     <xsd:attribute name="UnitPrice" />   
                   </xsd:complexType>  
                </xsd:element>  
            </xsd:sequence>  
           <xsd:attribute name="OrderID"/>   
          </xsd:complexType>  
       </xsd:element>  
     </xsd:sequence>  
   </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Créez deux tables dans le **tempdb** base de données :  
  
    ```  
    USE tempdb  
    CREATE TABLE Orders ([OrderID] int NOT NULL ) ON [PRIMARY]  
    ALTER TABLE Orders WITH NOCHECK ADD   
    CONSTRAINT [PK_Orders] PRIMARY KEY  CLUSTERED (  
       [OrderID]  
     )  ON [PRIMARY]   
    CREATE TABLE [OrderDetails] (  
       [OrderID] int NOT NULL ,  
       [ProductID] int NOT NULL ,  
       [UnitPrice] money NULL ,  
       [Quantity] smallint NOT NULL ,  
       [Discount] real NOT NULL   
    ) ON [PRIMARY]  
    ```  
  
2.  Ajoutez les exemples de données :  
  
    ```  
    INSERT INTO Orders ([OrderID]) values (10248)  
    INSERT INTO Orders ([OrderID]) values (10250)  
    INSERT INTO Orders ([OrderID]) values (10251)  
    INSERT INTO Orders ([OrderID]) values (10257)  
    INSERT INTO Orders ([OrderID]) values (10258)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10248,11,14,12,0)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10250,51,42.4,35,0.15)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10251,22,16.8,6,0.05)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10257,77,10.4,15,0)  
    INSERT INTO [OrderDetails] ([OrderID],[ProductID],[UnitPrice],[Quantity],[Discount]) values (10258,2,15.2,50,0.2)  
    ```  
  
3.  Enregistrez le schéma (LimitFieldValue.xml) dans un répertoire.  
  
4.  Créez le script de test suivant (TestQuery.vbs), modifiez MyServer en spécifiant le nom de votre ordinateur SQL Server et enregistrez-le dans le répertoire que vous avez utilisé à l'étape précédente pour enregistrer le schéma :  
  
    ```  
    Set conn = CreateObject("ADODB.Connection")  
    conn.Open "Provider=SQLOLEDB;Data Source=MyServer;Database=tempdb;Integrated Security=SSPI"  
    conn.Properties("SQLXML Version") = "sqlxml.4.0"   
    Set cmd = CreateObject("ADODB.Command")  
    Set stm = CreateObject("ADODB.Stream")  
    Set cmd.ActiveConnection = conn  
    stm.open  
    result ="none"  
    strXPathQuery="/root"  
    DBGUID_XPATH = "{EC2A4293-E898-11D2-B1B7-00C04F680C56}"  
    cmd.Dialect = DBGUID_XPATH  
    cmd.CommandText = strXPathQuery  
    cmd.Properties("Mapping schema") = "LimitFieldReal.xml"  
    cmd.Properties("Output Stream").Value = stm  
    cmd.Properties("Output Encoding") = "utf-8"  
    WScript.Echo "executing for xml query"  
    On Error Resume Next  
    cmd.Execute , ,1024  
    if err then  
    Wscript.Echo err.description  
    Wscript.Echo err.Number  
    Wscript.Echo err.source  
    On Error GoTo 0  
    else  
    stm.Position = 0  
    result  = stm.ReadText  
    end if  
    WScript.Echo result  
    Wscript.Echo "done"  
    ```  
  
5.  Exécutez le fichier TestQuery.vbs en cliquant dessus dans l'Explorateur Windows.  
  
     Voici le résultat obtenu :  
  
    ```  
    <root>  
      <Order OrderID="10248"/>  
      <Order OrderID="10250"/>  
      <Order OrderID="10251"/>  
      <Order OrderID="10257"/>  
      <Order OrderID="10258">  
        <orderDetail OrderID="10258"   
                     ProductID="2"   
                     Discount="0.2"   
                     Quantity="50"/>  
      </Order>  
    </root>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [float et real &#40;Transact-SQL&#41;](/sql/t-sql/data-types/float-and-real-transact-sql)   
 [NCHAR et nvarchar &#40;Transact-SQL&#41;](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)   
 [Installation de SQL Server Native Client](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)   
 [À l’aide de XSD schémas annotés dans les requêtes &#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml/annotated-xsd-schemas/using-annotated-xsd-schemas-in-queries-sqlxml-4-0.md)  
  
  

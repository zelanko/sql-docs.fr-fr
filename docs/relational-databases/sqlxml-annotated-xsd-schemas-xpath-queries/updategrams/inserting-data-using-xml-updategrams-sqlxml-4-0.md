---
title: Insertion de données à l’aide de codes XML (SQLXML)
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- xsi:nil attribute
- unique values
- <after> block
- id attribute
- data insertions [SQLXML]
- nil attribute
- <before> block
- updg:guid attribute
- multiple record insertions
- returnid attribute
- updategrams [SQLXML], inserting data
- updg:at-identity attribute
- invalid characters [SQLXML]
- updg:returnid attribute
- updg:id attribute
- namespaces [SQLXML], updategrams
- IDENTITY-type column
- guid attribute
- record insertion [SQLXML]
- null values [SQLXML]
- at-identity attribute
- xml data type [SQL Server], SQLXML
ms.assetid: 4dc48762-bc12-43fb-b356-ea1b9c1e287e
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: caf6c6bc9e9807b042baf365c3a1efbe9d2b74c5
ms.sourcegitcommit: 792c7548e9a07b5cd166e0007d06f64241a161f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75252498"
---
# <a name="inserting-data-using-xml-updategrams-sqlxml-40"></a>Insertion de données à l'aide de codes de mise à jour (updategrams) XML (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Un mise à jour indique une opération d’insertion lorsqu’une instance d’enregistrement apparaît dans le ** \<bloc after>** , mais pas dans le bloc ** \<Before>** correspondant. Dans ce cas, le mise à jour insère l’enregistrement dans le ** \<bloc after>** dans la base de données.  
  
 Voici le format du code de mise à jour pour une opération d'insertion :  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync [mapping-schema="SampleSchema.xml"]  >  
   [<updg:before>  
   </updg:before>]  
    <updg:after [updg:returnid="x y ...] >  
       <ElementName [updg:id="value"]   
                   [updg:at-identity="x"]   
                   [updg:guid="y"]  
                   attribute="value"   
                   attribute="value"  
                   ...  
       />  
      [<ElementName .../>... ]  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
## <a name="before-block"></a>\<avant le bloc>  
 Le ** \<bloc Before>** peut être omis pour une opération d’insertion. Si l’attribut facultatif **mapping-schema** n’est pas spécifié, le ** \<>ElementName** spécifié dans le mise à jour est mappé à une table de base de données et les éléments ou attributs enfants sont mappés aux colonnes de la table.  
  
## <a name="after-block"></a>\<après> bloc  
 Vous pouvez spécifier un ou plusieurs enregistrements dans le ** \<bloc after>** .  
  
 Si le ** \<bloc after>** ne fournit pas de valeur pour une colonne particulière, mise à jour utilise la valeur par défaut spécifiée dans le schéma annoté (si un schéma a été spécifié). Si le schéma ne spécifie pas de valeur par défaut pour la colonne, mise à jour ne spécifie pas de valeur explicite pour cette colonne et, à la place [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , affecte la valeur par défaut (si elle est spécifiée) à cette colonne. S'il n'y a aucune valeur par défaut [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et que la colonne accepte une valeur NULL, le code de mise à jour attribue la valeur NULL à la colonne. Si la colonne ne possède pas de valeur par défaut et qu'elle n'accepte pas de valeur NULL, la commande échoue et le code de mise à jour retourne une erreur. L’attribut facultatif **attribut updg : returnid** est utilisé pour retourner la valeur d’identité générée par le système lorsqu’un enregistrement est ajouté dans une table avec une colonne de type Identity.  
  
## <a name="updgid-attribute"></a>Attribut updg:id  
 Si le mise à jour n’insère que des enregistrements, mise à jour ne requiert pas l’attribut **attribut updg : ID** . Pour plus d’informations sur **attribut updg : ID**, consultez [mise à jour des données à l’aide de XML codes &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/updating-data-using-xml-updategrams-sqlxml-4-0.md).  
  
## <a name="updgat-identity-attribute"></a>Attribut updg:at-identity  
 Lorsqu’un mise à jour insère un enregistrement dans une table qui a une colonne de type IDENTity, le mise à jour peut capturer la valeur attribuée par le système à l’aide de l’attribut facultatif **attribut updg : at-Identity** . Le code de mise à jour peut utiliser ensuite cette valeur dans les opérations suivantes. Lors de l’exécution de mise à jour, vous pouvez retourner la valeur d’identité générée en spécifiant l’attribut **attribut updg : returnid** .  
  
## <a name="updgguid-attribute"></a>Attribut updg:guid  
 L’attribut **attribut updg : GUID** est un attribut facultatif qui génère un identificateur global unique. Cette valeur reste dans la portée pour l' ** \<** intégralité du bloc de>de synchronisation dans lequel elle est spécifiée. Vous pouvez utiliser cette valeur n’importe où ** \<** dans le bloc de>de synchronisation. L’attribut appelle la fonction **NewGuid ()** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour générer l’identificateur unique.  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l’aide des exemples suivants, vous devez respecter les exigences spécifiées dans la [Configuration requise pour l’exécution d’exemples SQLXML](../../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
 Avant d'utiliser les exemples de code de mise à jour, notez les points suivants :  
  
-   La plupart des exemples utilisent le mappage par défaut (en d'autres termes, aucun schéma de mappage n'est spécifié dans le code de mise à jour (updategram)). Pour obtenir plus d’exemples de codes qui utilisent des schémas de mappage, consultez [spécification d’un schéma de mappage annoté dans un mise à jour &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
-   La plupart des exemples sont basés sur l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)]. Toutes les mises à jour sont appliquées aux tables de cette base de données.  
  
### <a name="a-inserting-a-record-by-using-an-updategram"></a>R. Insertion d'un enregistrement à l'aide d'un code de mise à jour  
 Ce code de mise à jour centré sur les attributs insère un enregistrement dans la table HumanResources.Employee dans la base de données [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)].  
  
 Dans cet exemple, le code de mise à jour ne spécifie pas de schéma de mappage. Par conséquent, le code de mise à jour utilise le mappage par défaut, dans lequel le nom d'élément est mappé à un nom de table et les attributs ou éléments enfants sont mappés aux colonnes dans cette table.  
  
 Le schéma [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] pour la table HumanResources.Department impose une restriction NOT NULL sur toutes les colonnes sauf OrganizationNode et OrganizationLevel. Par conséquent, le code de mise à jour doit inclure des valeurs spécifiées pour toutes les colonnes. DepartmentID est une colonne de type IDENTITY. Par conséquent, aucune valeur n'est spécifiée pour cette colonne.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name="New Product Research"   
            GroupName="Research and Development"   
            ModifiedDate="2010-08-31"/>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de mise à jour ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom MyUpdategram.xml.  
  
2.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Dans un mappage centré sur l'élément, le code de mise à jour ressemble à ceci :  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department>  
            <Name> New Product Research </Name>  
            <GroupName> Research and Development </GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Dans un code de mise à jour en mode mixte (centré sur l'élément et centré sur l'attribut), un élément peut avoir des attributs et des sous-éléments, comme indiqué dans ce code de mise à jour :  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
       <HumanResources.Department   
            Name=" New Product Research "   
            <GroupName>Research and Development</GroupName>  
            <ModifiedDate>2010-08-31</ModifiedDate>  
       </HumanResources.Department>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="b-inserting-multiple-records-by-using-an-updategram"></a>B. Insertion de plusieurs enregistrements à l'aide d'un code de mise à jour  
 Ce code de mise à jour ajoute deux nouveaux enregistrements de décalage à la table HumanResources.Shift. Mise à jour ne spécifie pas le bloc facultatif ** \<Before>** .  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de mise à jour ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom Updategram-AddShifts.xml.  
  
2.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Une autre version de cet exemple est un mise à jour qui utilise deux blocs ** \<after>** séparés au lieu d’un bloc pour insérer les deux employés. Cette opération est valide et peut être encodée comme suit :  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync>  
    <updg:after >  
       <HumanResources.Shift Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
    <updg:before>  
    </updg:before>  
    <updg:after >  
       <HumanResources.Shift Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
### <a name="c-working-with-valid-sql-server-characters-that-are-not-valid-in-xml"></a>C. Utilisation de caractères SQL Server valides qui ne sont pas valides en XML  
 Dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], les noms de table peuvent inclure un espace, comme la table Order Details dans la base de données Northwind. Toutefois, cela n’est pas valide dans les caractères XML qui [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sont des identificateurs valides, mais les identificateurs XML non valides peuvent\_\_être encodés à l’aide de' __xHHHH’comme valeur d’encodage, où HHHH représente le code UCS-2 hexadécimal à quatre chiffres du caractère dans l’ordre binaire le plus significatif.  
  
> [!NOTE]  
>  Cet exemple utilise l'exemple de base de données Northwind. Vous pouvez installer la base de données Northwind à l’aide d’un script SQL disponible en téléchargement à partir de ce [site Web Microsoft](https://www.microsoft.com/download/details.aspx?id=23654).  
  
 Par ailleurs, le nom d'élément doit être mis entre crochets ([ ]). Étant donné que les caractères [et] ne sont pas valides en XML, vous devez\_ les encoder en tant que _x005B et _x005D\_, respectivement. (Si vous utilisez un schéma de mappage, vous pouvez fournir des noms d'élément qui ne contiennent pas de caractères non valides, tels que des espaces blancs. Le schéma de mappage effectue le mappage nécessaire ; par conséquent, il est inutile d'encoder ces caractères).  
  
 Ce code de mise à jour ajoute un enregistrement à la table Order Details dans la base de données Northwind :  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
      <_x005B_Order_x0020_Details_x005D_ OrderID="1"  
            ProductID="11"  
            UnitPrice="$1.0"  
            Quantity="1"  
            Discount="0.0" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 La colonne UnitPrice dans la table Order Details est de type **Money** . Pour appliquer la conversion de type appropriée (d’un type **chaîne** à un type **Money** ), le signe dollar ($) doit être ajouté dans le cadre de la valeur. Si le mise à jour ne spécifie pas de schéma de mappage, le premier caractère de la valeur de **chaîne** est évalué. Si le premier caractère est le signe $, la conversion appropriée est appliquée.  
  
 Si le mise à jour est spécifié par rapport à un schéma de mappage où la colonne est correctement marquée comme **DT : type = "Fixed. 14,4"** ou **SQL : datatype = "Money"**, le signe dollar ($) n’est pas requis et la conversion est gérée par le mappage. Il s'agit de la méthode recommandée pour garantir que la conversion de type appropriée a lieu.  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de mise à jour ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom UpdategramSpacesInTableName.xml.  
  
2.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="d-using-the-at-identity-attribute-to-retrieve-the-value-that-has-been-inserted-in-the-identity-type-column"></a>D. Utilisation de l'attribut at-identity pour récupérer la valeur ayant été insérée dans la colonne de type IDENTITY  
 Le code de mise à jour suivant insère deux enregistrements : un dans la table Sales.SalesOrderHeader et un autre dans la table Sales.SalesOrderDetail.  
  
 En premier lieu, le code de mise à jour ajoute un enregistrement à la table Sales.SalesOrderHeader. Dans cette table, la colonne SalesOrderID est une colonne de type IDENTITY. Par conséquent, lorsque vous ajoutez cet enregistrement à la table, mise à jour utilise l’attribut **at-Identity** pour capturer la valeur SalesOrderID assignée en tant que « x » (une valeur d’espace réservé). Le code spécifie ensuite cette variable **at-Identity** comme valeur de l’attribut SalesOrderID \<dans l’élément Sales. SalesOrderDetail>.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync >  
  <updg:before>  
  </updg:before>  
  <updg:after>  
   <Sales.SalesOrderHeader updg:at-identity="x"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00001111-2222-3333-4444-556677889900"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
      <Sales.SalesOrderDetail SalesOrderID="x"  
                LineNumber="1"  
                OrderQty="1"  
                ProductID="776"  
                SpecialOfferID="1"  
                UnitPrice="2429.9928"  
                UnitPriceDiscount="0.00"  
                rowguid="aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee"  
                ModifiedDate="2001-07-01 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Si vous souhaitez retourner la valeur d’identité générée par l’attribut **attribut updg : at-Identity** , vous pouvez utiliser l’attribut **attribut updg : returnid** . Le code de mise à jour modifié suivant retourne cette valeur d'identité. (Ce code de mise à jour ajoute deux enregistrements de commande et deux enregistrements de détail de commande pour rendre l'exemple un peu plus complexe.)  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
 <updg:sync>  
  <updg:before>  
  </updg:before>  
  <updg:after updg:returnid="x y" >  
       <HumanResources.Shift updg:at-identity="x" Name="Day-Evening"  
                        StartTime="1900-01-01 11:00:00.000"  
                        EndTime="1900-01-01 19:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
       <HumanResources.Shift updg:at-identity="y" Name="Evening-Night"  
                        StartTime="1900-01-01 19:00:00.000"  
                        EndTime="1900-01-01 03:00:00.000"  
                        ModifiedDate="2004-01-01 00:00:00.000" />  
  </updg:after>  
 </updg:sync>  
</ROOT>  
```  
  
 Lorsque le code de mise à jour est exécuté, il retourne des résultats semblables aux suivants, qui comprennent notamment la valeur d'identité (valeur générée de la colonne ShiftID utilisée pour l'identité de table) ayant été générée :  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">   
  <returnid>   
    <x>4</x>   
    <y>5</y>   
  </returnid>   
</ROOT>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de mise à jour ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom Updategram-returnId.xml.  
  
2.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="e-using-the-updgguid-attribute-to-generate-a-unique-value"></a>E. Utilisation de l'attribut updg:guid pour générer une valeur unique  
 Dans cet exemple, le code de mise à jour insère un enregistrement dans les tables Cust et CustOrder. En outre, mise à jour génère une valeur unique pour l’attribut CustomerID à l’aide de l’attribut **attribut updg : GUID** .  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after updg:returnid="x" >  
      <Cust updg:guid="x" >  
         <CustID>x</CustID>  
         <LastName>Fuller</LastName>  
      </Cust>  
      <CustOrder>  
         <CustID>x</CustID>  
         <OrderID>1</OrderID>  
      </CustOrder>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Mise à jour spécifie l’attribut **returnid** . En conséquence, le GUID généré est retourné :  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <returnid>  
    <x>7111BD1A-7F0B-4CEE-B411-260DADFEFA2A</x>   
  </returnid>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>Pour tester le code de mise à jour  
  
1.  Copiez le code de mise à jour ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom Updategram-GenerateGuid.xml.  
  
2.  Créez les tables suivantes :  
  
    ```  
    USE tempdb  
    CREATE TABLE Cust (CustID uniqueidentifier, LastName varchar(20))  
    CREATE TABLE CustOrder (CustID uniqueidentifier, OrderID int)  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="f-specifying-a-schema-in-an-updategram"></a>F. Spécification d'un schéma dans un code de mise à jour  
 Le code de mise à jour dans cet exemple insère un enregistrement dans la table suivante :  
  
```  
CustOrder(OrderID, EmployeeID, OrderType)  
```  
  
 Un schéma XSD est spécifié dans ce code de mise à jour (autrement dit, il n'y a aucun mappage par défaut des éléments et des attributs du code de mise à jour). Le schéma fournit le mappage nécessaire des éléments et des attributs aux tables et aux colonnes de base de données.  
  
 Le schéma suivant (CustOrderSchema. Xml) décrit un ** \<élément CustOrder>** qui se compose des attributs **OrderID** et **EmployeeID** . Pour rendre le schéma plus intéressant, une valeur par défaut est assignée à l’attribut **EmployeeID** . Un code de mise à jour utilise uniquement la valeur par défaut d'un attribut pour les opérations d'insertion, puis uniquement si le code de mise à jour ne spécifie pas cet attribut.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="CustOrder" >  
   <xsd:complexType>  
        <xsd:attribute name="OrderID"     type="xsd:integer" />   
        <xsd:attribute name="EmployeeID"  type="xsd:integer" />  
        <xsd:attribute name="OrderType  " type="xsd:integer" default="1"/>  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Ce code de mise à jour insère un enregistrement dans la table CustOrder. Le code de mise à jour spécifie uniquement les valeurs des attributs OrderID et EmployeeID. Il ne spécifie pas la valeur de l'attribut OrderType. Par conséquent, le code de mise à jour utilise la valeur par défaut de l'attribut EmployeeID spécifié dans le schéma précédent.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
             xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync mapping-schema='CustOrderSchema.xml'>  
<updg:after>  
       <CustOrder OrderID="98000" EmployeeID="1" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 Pour obtenir plus d’exemples de codes qui spécifient un schéma de mappage, consultez [spécification d’un schéma de mappage annoté dans un mise à jour &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/updategrams/specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).  
  
##### <a name="to-test-the-updategram"></a>Pour tester le code de mise à jour  
  
1.  Créez cette table dans la base de données **tempdb** :  
  
    ```  
    USE tempdb  
    CREATE TABLE CustOrder(  
                     OrderID int,   
                     EmployeeID int,   
                     OrderType int)  
    ```  
  
2.  Copiez le schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom CustOrderSchema.xml.  
  
3.  Copiez le code de mise à jour ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom CustOrderUpdategram.xml dans le même dossier qu'à l'étape précédente.  
  
4.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le code de mise à jour (updategram).  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le schéma XDR équivalent :  
  
```  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
 <ElementType name="CustOrder" >  
    <AttributeType name="OrderID" />  
    <AttributeType name="EmployeeID" />  
    <AttributeType name="OrderType" default="1" />  
    <attribute type="OrderID"  />  
    <attribute type="EmployeeID" />  
    <attribute type="OrderType" />  
  </ElementType>  
</Schema>  
```  
  
### <a name="g-using-the-xsinil-attribute-to-insert-null-values-in-a-column"></a>G. Utilisation de l'attribut xsi:nil pour insérer des valeurs Null dans une colonne  
 Si vous souhaitez insérer une valeur null dans la colonne correspondante de la table, vous pouvez spécifier l’attribut **xsi : Nil** sur un élément dans un mise à jour. Dans le schéma XSD correspondant, l’attribut XSD **nillable** doit également être spécifié.  
  
 Considérons par exemple ce schéma XSD :  
  
```  
<?xml version="1.0"?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:element name="Student" sql:relation="Students">  
  <xsd:complexType>  
    <xsd:all>  
      <xsd:element name="fname" sql:field="first_name"   
                                type="xsd:string"   
                                 nillable="true"/>  
    </xsd:all>  
    <xsd:attribute name="SID"   
                        sql:field="StudentID"  
                        type="xsd:ID"/>      
    <xsd:attribute name="lname"       
                        sql:field="last_name"  
                        type="xsd:string"/>  
    <xsd:attribute name="minitial"    
                        sql:field="middle_initial"   
                        type="xsd:string"/>  
    <xsd:attribute name="years"       
                         sql:field="no_of_years"  
                         type="xsd:integer"/>  
  </xsd:complexType>  
 </xsd:element>  
</xsd:schema>  
```  
  
 Le schéma XSD spécifie **nillable = "true"** pour l' ** \<élément>fname** . Le code de mise à jour suivant utilise ce schéma :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql"  
      xmlns:updg="urn:schemas-microsoft-com:xml-updategram"  
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  
<updg:sync mapping-schema='StudentSchema.xml'>  
  <updg:before/>  
  <updg:after>  
    <Student SID="S00004" lname="Elmaci" minitial="" years="2">  
      <fname xsi:nil="true">  
    </fname>  
    </Student>  
  </updg:after>  
</updg:sync>  
  
</ROOT>  
```  
  
 Mise à jour spécifie **xsi : Nil** pour l' ** \<élément>fname** dans le ** \<bloc after>** . Par conséquent, lorsque ce code de mise à jour est exécuté, une valeur NULL est insérée pour la colonne first_name dans la table.  
  
##### <a name="to-test-the-updategram"></a>Pour tester le code de mise à jour  
  
1.  Créez la table suivante dans la base de données **tempdb** :  
  
    ```  
    USE tempdb  
    CREATE TABLE Students (  
       StudentID char(6)NOT NULL ,  
       first_name varchar(50),  
       last_name varchar(50),  
       middle_initial char(1),  
       no_of_years int NULL)  
    GO  
    ```  
  
2.  Copiez le schéma ci-dessus et collez-le dans un fichier texte. Enregistrez ce fichier sous le nom StudentSchema.xml.  
  
3.  Copiez le code de mise à jour ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom StudentUpdategram.xml dans le même dossier qu'à l'étape précédente pour enregistrer StudentSchema.xml.  
  
4.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le code de mise à jour (updategram).  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="h-specifying-namespaces-in-an-updategram"></a>H. Spécification d'espaces de noms dans un code de mise à jour  
 Dans un code de mise à jour, vous pouvez avoir des éléments qui appartiennent à un espace de noms déclaré dans le même élément dans le code de mise à jour. Dans ce cas, le schéma correspondant doit également déclarer le même espace de noms et l'élément doit appartenir à cet espace de noms cible.  
  
 Par exemple, dans l’mise à jour suivant (updategram-ElementHavingNamespace. Xml), l' ** \<élément Order>** appartient à un espace de noms déclaré dans l’élément.  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema='XSD-ElementHavingNameSpace.xml'>  
    <updg:after>  
       <x:Order  xmlns:x="https://server/xyz/schemas/"  
             updg:at-identity="SalesOrderID"   
             RevisionNumber="1"  
             OrderDate="2001-07-01 00:00:00.000"  
             DueDate="2001-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             CustomerID="676"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="00009999-8888-7777-6666-554433221100"  
             ModifiedDate="2001-07-08 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Dans ce cas, le schéma doit également déclarer l'espace de noms comme montré dans ce schéma :  
  
 Le schéma suivant (XSD-ElementHavingNamespace.xml) montre comment l'élément et les attributs correspondants doivent être déclarés.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
     xmlns:dt="urn:schemas-microsoft-com:datatypes"   
     xmlns:sql="urn:schemas-microsoft-com:mapping-schema"    
     xmlns:x="https://server/xyz/schemas/"   
     targetNamespace="https://server/xyz/schemas/" >  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader" type="x:Order_type"/>  
  <xsd:complexType name="Order_type">  
    <xsd:attribute name="SalesOrderID"  type="xsd:ID"/>  
    <xsd:attribute name="RevisionNumber" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OrderDate" type="xsd:dateTime"/>  
    <xsd:attribute name="DueDate" type="xsd:dateTime"/>  
    <xsd:attribute name="ShipDate" type="xsd:dateTime"/>  
    <xsd:attribute name="Status" type="xsd:unsignedByte"/>  
    <xsd:attribute name="OnlineOrderFlag" type="xsd:boolean"/>  
    <xsd:attribute name="SalesOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="PurchaseOrderNumber" type="xsd:string"/>  
    <xsd:attribute name="AccountNumber" type="xsd:string"/>  
    <xsd:attribute name="CustomerID" type="xsd:int"/>  
    <xsd:attribute name="ContactID" type="xsd:int"/>  
    <xsd:attribute name="SalesPersonID" type="xsd:int"/>  
    <xsd:attribute name="TerritoryID" type="xsd:int"/>  
    <xsd:attribute name="BillToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipToAddressID" type="xsd:int"/>  
    <xsd:attribute name="ShipMethodID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardID" type="xsd:int"/>  
    <xsd:attribute name="CreditCardApprovalCode" type="xsd:string"/>  
    <xsd:attribute name="CurrencyRateID" type="xsd:int"/>  
    <xsd:attribute name="SubTotal" type="xsd:decimal"/>  
    <xsd:attribute name="TaxAmt" type="xsd:decimal"/>  
    <xsd:attribute name="Freight" type="xsd:decimal"/>  
    <xsd:attribute name="TotalDue" type="xsd:decimal"/>  
    <xsd:attribute name="Comment" type="xsd:string"/>  
    <xsd:attribute name="rowguid" type="xsd:string"/>  
    <xsd:attribute name="ModifiedDate" type="xsd:dateTime"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a>Pour tester le code de mise à jour  
  
1.  Copiez le schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom XSD-ElementHavingNamespace.xml.  
  
2.  Copiez le code de mise à jour ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom Updategram-ElementHavingNamespace.xml dans le même dossier que celui utilisé pour enregistrer XSD-ElementHavingnamespace.xml.  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le code de mise à jour (updategram).  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
### <a name="i-inserting-data-into-an-xml-data-type-column"></a>I. Insertion de données dans une colonne de type de données XML  
 Le type de données **XML** a été [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]introduit dans. Vous pouvez utiliser codes pour insérer et mettre à jour des données stockées dans des colonnes de type de données **XML** avec les dispositions suivantes :  
  
-   La colonne **XML** ne peut pas être utilisée pour identifier une ligne existante. Par conséquent, il ne peut pas être inclus dans la section **attribut updg : Before** d’un mise à jour.  
  
-   Les espaces de noms qui sont dans la portée du fragment XML inséré dans la colonne **XML** sont conservés et leurs déclarations d’espace de noms sont ajoutées à l’élément supérieur du fragment inséré.  
  
 Par exemple, dans l’mise à jour suivant (SampleUpdateGram. Xml), l' ** \<élément DESC>** met à jour la colonne ProductDescription dans la table production>ProductModel de l' [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] exemple de base de données. Le résultat de cette mise à jour est que le contenu XML de la colonne ProductDescription est mis à jour avec le contenu XML de l' ** \<élément DESC>** .  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
    <updg:sync mapping-schema="SampleSchema.xml" >  
       <updg:before>  
<ProductModel ProductModelID="19">  
   <Name>Mountain-100</Name>  
</ProductModel>  
    </updg:before>  
    <updg:after>  
 <ProductModel>  
    <Name>Mountain-100</Name>  
    <Desc><?xml-stylesheet href="ProductDescription.xsl" type="text/xsl"?>  
        <p1:ProductDescription xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
              xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"   
              xmlns:wf="https://www.adventure-works.com/schemas/OtherFeatures"   
              xmlns:html="http://www.w3.org/1999/xhtml"   
              xmlns="">  
  <p1:Summary>  
     <html:p>Insert Example</html:p>  
  </p1:Summary>  
  <p1:Manufacturer>  
    <p1:Name>AdventureWorks</p1:Name>  
    <p1:Copyright>2002</p1:Copyright>  
    <p1:ProductURL>HTTP://www.Adventure-works.com</p1:ProductURL>  
  </p1:Manufacturer>  
  <p1:Features>These are the product highlights.   
    <wm:Warranty>  
       <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
       <wm:Description>parts and labor</wm:Description>  
    </wm:Warranty>  
    <wm:Maintenance>  
       <wm:NoOfYears>10 years</wm:NoOfYears>  
       <wm:Description>maintenance contract available through your dealer or any AdventureWorks retail store.</wm:Description>  
    </wm:Maintenance>  
    <wf:wheel>High performance wheels.</wf:wheel>  
    <wf:saddle>  
      <html:i>Anatomic design</html:i> and made from durable leather for a full-day of riding in comfort.</wf:saddle>  
    <wf:pedal>  
       <html:b>Top-of-the-line</html:b> clipless pedals with adjustable tension.</wf:pedal>  
    <wf:BikeFrame>Each frame is hand-crafted in our Bothell facility to the optimum diameter and wall-thickness required of a premium mountain frame. The heat-treated welded aluminum frame has a larger diameter tube that absorbs the bumps.</wf:BikeFrame>  
    <wf:crankset> Triple crankset; alumunim crank arm; flawless shifting. </wf:crankset>  
   </p1:Features>  
   <p1:Picture>  
      <p1:Angle>front</p1:Angle>  
      <p1:Size>small</p1:Size>  
      <p1:ProductPhotoID>118</p1:ProductPhotoID>  
   </p1:Picture>  
   <p1:Specifications> These are the product specifications.  
     <Material>Almuminum Alloy</Material>  
     <Color>Available in most colors</Color>  
     <ProductLine>Mountain bike</ProductLine>  
     <Style>Unisex</Style>  
     <RiderExperience>Advanced to Professional riders</RiderExperience>  
   </p1:Specifications>  
  </p1:ProductDescription>  
 </Desc>  
      </ProductModel>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 Le code de mise à jour fait référence au schéma XSD annoté suivant (SampleSchema.xml).  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
           xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
           xmlns="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">   
  <xsd:element name="ProductModel"  sql:relation="Production.ProductModel" >  
     <xsd:complexType>  
       <xsd:sequence>  
          <xsd:element name="Name" type="xsd:string"></xsd:element>  
          <xsd:element name="Desc" sql:field="CatalogDescription" sql:datatype="xml">  
           <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="ProductDescription">  
                 <xsd:complexType>  
                   <xsd:sequence>  
                     <xsd:element name="Summary" type="xsd:anyType">  
                     </xsd:element>  
                   </xsd:sequence>  
                 </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>   
       </xsd:sequence>  
       <xsd:attribute name="ProductModelID" sql:field="ProductModelID"/>  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-the-updategram"></a>Pour tester le code de mise à jour  
  
1.  Copiez le schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom XSD-SampleSchema.xml.  
  
    > [!NOTE]  
    >  Étant donné que codes prend en charge le mappage par défaut, il n’existe aucun moyen d’identifier le début et la fin du type de données **XML** . Cela signifie qu’un schéma de mappage est requis lors de l’insertion ou de la mise à jour de tables avec des colonnes de type de données **XML** . Lorsqu'un schéma n'est pas fourni, SQLXML retourne une erreur indiquant que l'une des colonnes est absente de la table.  
  
2.  Copiez le code de mise à jour ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom SampleUpdategram.xml dans le même dossier que celui utilisé pour enregistrer SampleSchema.xml.  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le code de mise à jour (updategram).  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations sur la sécurité mise à jour &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/updategram-security-considerations-sqlxml-4-0.md)  
  
  

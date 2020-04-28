---
title: 'Convertir des types de données avec SQL : DataType (SQLXML)'
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- type attribute
- sql:datatype
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- xsd:type
- datatype annotation
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XSD schemas [SQLXML], mapping data types
ms.assetid: db192105-e8aa-4392-b812-9d727918c005
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 98f2ee047bccf7cd3843fe34aaf8f5caec0dc11a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "75257470"
---
# <a name="data-type-conversions-and-the-sqldatatype-annotation-sqlxml-40"></a>Conversions de types de données et annotation sql : DataType (SQLXML 4,0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Dans un schéma XSD, l’attribut **xsd : type** spécifie le type de données XSD d’un élément ou d’un attribut. Lorsqu'un schéma XSD est utilisé pour extraire des données de la base de données, le type de données spécifié est utilisé pour formater les données.  
  
 Outre la spécification d’un type XSD dans un schéma, vous pouvez également spécifier un type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de données Microsoft à l’aide de l’annotation **SQL : DataType** . Les attributs **xsd : type** et **SQL : DataType** contrôlent le mappage entre les types de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] données XSD et les types de données.  
  
## <a name="xsdtype-attribute"></a>Attribut xsd:type  
 Vous pouvez utiliser l’attribut **xsd : type** pour spécifier le type de données XML d’un attribut ou d’un élément qui est mappé à une colonne. Le **type xsd :** affecte le document renvoyé à partir du serveur, ainsi que la requête XPath exécutée. Lorsqu’une requête XPath est exécutée sur un schéma de mappage qui contient **xsd : type**, XPath utilise le type de données spécifié lors du traitement de la requête. Pour plus d’informations sur la façon dont XPath utilise **xsd : type**, consultez [mappage de types de données XSD à des types de données XPath &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/mapping-xsd-data-types-to-xpath-data-types-sqlxml-4-0.md).  
  
 Dans un document retourné, tous les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont convertis en représentations sous forme de chaîne. Certains types de données requièrent des conversions supplémentaires. Le tableau suivant répertorie les conversions utilisées pour différentes valeurs **xsd : type** .  
  
|Type de données XSD|Conversion SQL Server|  
|-------------------|---------------------------|  
|Boolean|CONVERT(bit, COLUMN)|  
|Date|LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)|  
|Décimal|CONVERT(money, COLUMN)|  
|id/idref/idrefs|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|nmtoken/nmtokens|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|Heure|SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)|  
|Tous les autres|Aucune conversion supplémentaire|  
  
> [!NOTE]  
>  Certaines des valeurs retournées [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par peuvent ne pas être compatibles avec les types de données XML spécifiés à l’aide de **xsd : type**, soit parce que la conversion n’est pas possible (par exemple, en convertissant « XYZ » en type de données **décimal** ), soit parce que la valeur dépasse la plage de ce type de données (par exemple,-100000 converti en type XSD **unsignedShort** ). Les conversions de type incompatibles peuvent générer des documents XML non valides ou des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="mapping-from-sql-server-data-types-to-xsd-data-types"></a>Mappage des types de données SQL Server en types de données XSD  
 Le tableau ci-dessous montre un mappage évident de types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en types de données XSD. Si vous connaissez le type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ce tableau fournit le type XSD correspondant que vous pouvez spécifier dans le schéma XSD.  
  
|Type de données SQL Server|Type de données XSD|  
|--------------------------|-------------------|  
|**bigint**|**long**|  
|**binary**|**base64Binary**|  
|**bit**|**boolean**|  
|**char**|**string**|  
|**datetime**|**dateTime**|  
|**decimal**|**decimal**|  
|**float**|**double**|  
|**image**|**base64Binary**|  
|**int**|**int**|  
|**money**|**decimal**|  
|**nchar**|**string**|  
|**ntext**|**string**|  
|**nvarchar**|**string**|  
|**numeric**|**decimal**|  
|**real**|**float**|  
|**smalldatetime**|**dateTime**|  
|**smallint**|**short**|  
|**smallmoney**|**decimal**|  
|**sql_variant**|**string**|  
|**sysname**|**string**|  
|**text**|**string**|  
|**timestamp**|**dateTime**|  
|**tinyint**|**unsignedByte**|  
|**varbinary**|**base64Binary**|  
|**varchar**|**string**|  
|**uniqueidentifier**|**string**|  
  
## <a name="sqldatatype-annotation"></a>Annotation sql:datatype  
 L’annotation **SQL : DataType** est utilisée pour spécifier le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données ; cette annotation doit être spécifiée dans les cas suivants :  
  
-   Vous effectuez un chargement en masse dans une colonne **DateTime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d’un type de date/heure **xsd,** de **Date**ou d' **heure** . Dans ce cas, vous devez identifier le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données de la colonne à l’aide de **SQL : datatype = "DateTime"**. Cette règle s'applique également aux codes de mise à jour.  
  
-   Vous effectuez un chargement en masse dans une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] colonne de type **uniqueidentifier** et la valeur xsd est un GUID qui comprend des accolades ({et}). Lorsque vous spécifiez **SQL : datatype = "uniqueidentifier"**, les accolades sont supprimées de la valeur avant d’être insérées dans la colonne. Si **SQL : DataType** n’est pas spécifié, la valeur est envoyée avec les accolades, et l’insertion ou la mise à jour échoue.  
  
-   Le type de données **XML base64Binary** est mappé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à différents types de données (**Binary**, **image**ou **varbinary**). Pour mapper le type de données XML **base64Binary** à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données spécifique, utilisez l’annotation **SQL : DataType** . Cette annotation spécifie le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] explicite de la colonne à laquelle l'attribut est mappé. Ceci est utile lorsque les données sont stockées dans les bases de données. En spécifiant l’annotation **SQL : DataType** , vous pouvez identifier le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données explicite.  
  
 Il est généralement recommandé de spécifier **SQL : DataType** dans le schéma.  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l'aide des exemples suivants, vous devez répondre à certaines conditions requises. Pour plus d’informations, consultez [Configuration requise pour l’exécution d’exemples SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-xsdtype"></a>A. Spécification de xsd:type  
 Cet exemple montre comment un type de **Date** XSD qui est spécifié à l’aide de l’attribut **xsd : type** dans le schéma affecte le document XML obtenu. Le schéma fournit une vue XML de la table Sales.SalesOrderHeader dans la base de données AdventureWorks.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader">  
     <xsd:complexType>  
       <xsd:attribute name="SalesOrderID" type="xsd:string" />   
       <xsd:attribute name="CustomerID"   type="xsd:string" />   
       <xsd:attribute name="OrderDate"    type="xsd:date" />   
       <xsd:attribute name="DueDate"  />   
       <xsd:attribute name="ShipDate"  type="xsd:time" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Dans ce schéma XSD, trois attributs retournent une valeur de date à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Lorsque le schéma :  
  
-   Spécifie **xsd : type = date** sur l’attribut **OrderDate** , la partie Date de la valeur retournée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour l’attribut **OrderDate** est affichée.  
  
-   Spécifie **xsd : type = Time** sur l’attribut **ShipDate** , la partie heure de la valeur retournée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour l’attribut **ShipDate** est affichée.  
  
-   Ne spécifie pas **xsd : type** sur l’attribut **DueDate** , la même valeur que celle retournée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est affichée.  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom xsdType.xml.  
  
2.  Copiez le modèle suivant et collez-le dans un fichier texte. Enregistrez le fichier sous le nom xsdTypeT.xml dans le répertoire où vous avez enregistré xsdType.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="xsdType.xml">  
        /Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (xsdType.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\SqlXmlTest\xsdType.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  

     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le jeu de résultats partiel :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43659"   
         CustomerID="676"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
  <Order SalesOrderID="43660"   
         CustomerID="117"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
 ...  
</ROOT>  
```  
  
 Voici le schéma XDR équivalent :  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader">  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="CustomerID"  />  
    <AttributeType name="OrderDate" dt:type="date" />  
    <AttributeType name="DueDate" />  
    <AttributeType name="ShipDate" dt:type="time" />  
  
    <attribute type="SalesOrderID" sql:field="OrderID" />  
    <attribute type="CustomerID" sql:field="CustomerID" />  
    <attribute type="OrderDate" sql:field="OrderDate" />  
    <attribute type="DueDate" sql:field="DueDate" />  
    <attribute type="ShipDate" sql:field="ShipDate" />  
</ElementType>  
</Schema>  
```  
  
### <a name="b-specifying-sql-data-type-using-sqldatatype"></a>B. Spécification du type de données SQL à l'aide de sql:datatype  
 Pour obtenir un exemple fonctionnel, consultez l’exemple G dans les [exemples de chargement en masse XML &#40;SQLXML 4,0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md). Dans cet exemple, une valeur GUID qui inclut "{" et "}" fait l'objet d'un chargement en masse. Le schéma de cet exemple spécifie **SQL : DataType** pour identifier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le type de données comme **uniqueidentifier**. Cet exemple montre comment **SQL : DataType** doit être spécifié dans le schéma.  
  
  

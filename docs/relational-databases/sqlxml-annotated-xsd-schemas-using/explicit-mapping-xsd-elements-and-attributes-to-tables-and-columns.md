---
title: Mappages XSD personnalisés aux tables/colonnes (SQLXML)
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit schema mapping [SQLXML]
- XPath queries [SQLXML], annotated XSD schemas in queries
- sql:field
- row mapping [SQLXML]
- attribute mapping [SQLXML], explicit mapping
- field annotation
- XSD schemas [SQLXML], mapping attributes and elements
- names [SQLXML]
- relation annotation
- table/view mapping [SQLXML], explicit mapping
- sql:relation
- mapping schema [SQLXML], explicit mapping
- annotated XSD schemas, mapping attributes and elements
- column mapping [SQLXML]
- element mapping [SQLXML], explicit mapping
- table mapping [SQLXML], explicit mapping
- element/attribute mapping [SQLXML]
ms.assetid: 7a5ebeb6-7322-4141-a307-ebcf95976146
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5fafcd918dda0001c316fd68cae3b19e6cd805a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75257434"
---
# <a name="custom-xsd-mappings-to-tablescolumns-sqlxml"></a>Mappages XSD personnalisés aux tables/colonnes (SQLXML)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Lors de l'utilisation d'un schéma XSD pour fournir une vue XML de la base de données relationnelle, les éléments et les attributs du schéma doivent être mappés avec les tables et les colonnes de la base de données. Les lignes de la table/vue de la base de données seront mappées avec les éléments du document XML. Les valeurs des colonnes de la base de données sont mappées avec les attributs ou les éléments.  
  
 Lorsque les requêtes XPath sont spécifiées par rapport au schéma XSD annoté, les données des éléments et des attributs du schéma sont extraites des tables et des colonnes avec lesquelles elles sont mappées. Pour obtenir une valeur unique de la base de données, le mappage spécifié dans le schéma XSD doit posséder les spécifications de relation et de champ. Si le nom d’un élément ou d’un attribut n’est pas le même que celui de la table ou de la vue ou du nom de la colonne à laquelle il est mappé, les annotations **SQL : relation** et **SQL : Field** sont utilisées pour spécifier le mappage entre un élément ou un attribut dans un document XML et la table (vue) ou la colonne dans une base de données.  
  
## <a name="sql-relation"></a>sql-relation  
 L’annotation **SQL : relation** est ajoutée pour mapper un nœud XML du schéma XSD à une table de base de données. Le nom d’une table (vue) est spécifié en tant que valeur de l’annotation **SQL : relation** .  
  
 Quand **SQL : relation** est spécifié sur un élément, la portée de cette annotation s’applique à tous les attributs et éléments enfants décrits dans la définition de type complexe de cet élément, ce qui fournit un raccourci pour écrire des annotations.  
  
 L’annotation **SQL : relation** est également utile lorsque les identificateurs qui sont valides dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sont pas valides dans XML. Par exemple, « Détails des commandes » est un nom de table valide dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais non en XML. Dans ce cas, l’annotation **SQL : relation** peut être utilisée pour spécifier le mappage, par exemple :  
  
```  
<xsd:element name="OD" sql:relation="[Order Details]">  
```  
  
## <a name="sql-field"></a>sql-field  
 L’annotation **SQL-Field** mappe un élément ou un attribut à une colonne de base de données. L’annotation **SQL : Field** est ajoutée pour mapper un nœud XML du schéma à une colonne de base de données. Vous ne pouvez pas spécifier **SQL : Field** sur un élément de contenu vide.  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l'aide des exemples suivants, vous devez répondre à certaines conditions requises. Pour plus d’informations, consultez [Configuration requise pour l’exécution d’exemples SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlrelation-and-sqlfield-annotations"></a>R. Spécification des annotations sql:relation et sql:field  
 Dans cet exemple, le schéma XSD se compose d’un élément ** \<contact>** d’un type complexe avec ** \<fname>** et ** \<lname>** éléments enfants et l’attribut **ContactID** .  
  
 L’annotation **SQL : relation** mappe l' ** \<élément Contact>** à la table Person. contact de la base de données AdventureWorks. L’annotation **SQL : Field** mappe l' ** \<élément>fname** à la colonne FirstName et à l’élément ** \<lname>** à la colonne LastName.  
  
 Aucune annotation n’est spécifiée pour l’attribut **ContactID** . Il s'ensuit un mappage par défaut de l'attribut avec la colonne du même nom.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Contact" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"  
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
        <xsd:attribute name="ContactID"   
                       type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom MySchema-annotated.xml.  
  
2.  Copiez le modèle suivant ci-dessous et collez-le dans un fichier texte. Enregistrez le fichier sous le nom MySchema-annotatedT.xml dans le même répertoire que celui où vous avez enregistré MySchema-annotated.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="MySchema-annotated.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (MySchema-annotated.xml) varie en fonction du répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\SqlXmlTest\MySchema-annotated.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le jeu de résultats partiel :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
 <Contact ContactID="1">   
    <FName>Gustavo</FName>   
    <LName>Achong</LName>   
 </Contact>   
  .....  
</ROOT>  
```  
  
  

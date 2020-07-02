---
title: Spécifier un espace de noms cible avec targetNamespace (SQLXML)
description: Découvrez comment spécifier un espace de noms cible dans un schéma XSD à l’aide de l’attribut targetNamespace dans SQLXML 4,0.
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- namespaces [SQLXML], annotated XSD schemas
- targetNamespace attribute
- XSD schemas [SQLXML], target namespaces
- annotated XSD schemas, target namespaces
- xsd:targetNamespace
- attributeFormDefault attribute
- elementFormDefault attribute
- target namespaces [SQLXML]
ms.assetid: f3df9877-6672-4444-8245-2670063c9310
author: MightyPen
ms.author: genemi
ms.reviewer: ''
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: bfa6234aae5e2744a88c4fcfb158575cb07000f5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764894"
---
# <a name="specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-40"></a>Spécification d'un espace de noms cible à l'aide de l'attribut targetNamespace (SQLXML 4.0)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Dans l’écriture de schémas XSD, vous pouvez utiliser l’attribut XSD **targetNamespace** pour spécifier un espace de noms cible. Cette rubrique décrit le fonctionnement des attributs XSD **targetNamespace**, **elementFormDefault**et **attributeFormDefault** , comment ils affectent l’instance XML générée et comment les requêtes XPath sont spécifiées avec des espaces de noms.  
  
 Vous pouvez utiliser l’attribut **xsd : targetNamespace** pour placer des éléments et des attributs de l’espace de noms par défaut dans un espace de noms différent. Vous pouvez également spécifier si les éléments et attributs du schéma déclarés localement doivent apparaître qualifiés par un espace de noms, soit explicitement en utilisant un préfixe, soit implicitement par défaut. Vous pouvez utiliser les attributs **elementFormDefault** et **attributeFormDefault** sur l' **\<xsd:schema>** élément pour spécifier globalement la qualification des éléments et attributs locaux, ou vous pouvez utiliser l’attribut **Form** pour spécifier séparément des éléments et des attributs individuels.  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l'aide des exemples suivants, vous devez répondre à certaines conditions requises. Pour plus d’informations, consultez [Configuration requise pour l’exécution d’exemples SQLXML](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-a-target-namespace"></a>A. Spécification d'un espace de noms cible  
 Le schéma XSD suivant spécifie un espace de noms cible à l’aide de l’attribut **xsd : targetNamespace** . Le schéma définit également les valeurs des attributs **elementFormDefault** et **attributeFormDefault** sur **« Unqualified »** (valeur par défaut pour ces attributs). Il s’agit d’une déclaration globale qui affecte tous les éléments locaux ( **\<Order>** dans le schéma) et les attributs (**CustomerID**, **ContactName**et **OrderID** dans le schéma).  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema"  
            xmlns:CO="urn:MyNamespace"   
            targetNamespace="urn:MyNamespace" >  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustOrders"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer"   
               sql:relation="Sales.Customer"   
               type="CO:CustomerType" />  
  
  <xsd:complexType name="CustomerType" >  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustOrders"  
                     type="CO:OrderType" />  
     </xsd:sequence>  
        <xsd:attribute name="CustomerID"   type="xsd:string" />   
        <xsd:attribute name="SalesPersonID"  type="xsd:string" />  
  </xsd:complexType>  
  <xsd:complexType name="OrderType" >  
     <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
     <xsd:attribute name="CustomerID" type="xsd:string" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 Dans le schéma :  
  
-   Les déclarations de type **CustomerType** et **OrderType** sont globales et, par conséquent, sont incluses dans l’espace de noms cible du schéma. Par conséquent, lorsque ces types sont référencés dans la déclaration de l' **\<Customer>** élément et de son **\<Order>** élément enfant, un préfixe est spécifié et est associé à l’espace de noms cible.  
  
-   L' **\<Customer>** élément est également inclus dans l’espace de noms cible du schéma, car il s’agit d’un élément global dans le schéma.  
  
 Exécutez la requête XPath suivante sur le schéma :  
  
```  
(/CO:Customer[@CustomerID=1)   
```  
  
 La requête XPath génère ce document d'instance (seules quelques commandes sont affichées) :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <y0:Customer xmlns:y0="urn:MyNamespace"   
      CustomerID="ALFKI" ContactName="Maria Anders">  
        <Order CustomerID="ALFKI" OrderID="10643" />   
        <Order CustomerID="ALFKI" OrderID="10692" />   
        ...  
  </y0:Customer>  
  </ROOT>  
```  
  
 Ce document d’instance définit l’espace de noms urn : MyNamespace et associe un préfixe (Y0) à celui-ci. Le préfixe est appliqué uniquement à l' **\<Customer>** élément global. (L’élément est global parce qu’il est déclaré en tant qu’enfant de **\<xsd:schema>** l’élément dans le schéma.)  
  
 Le préfixe n’est pas appliqué aux éléments et attributs locaux, car la valeur des attributs **elementFormDefault** et **attributeFormDefault** est définie sur **« Unqualified »** dans le schéma. Notez que l' **\<Order>** élément est local, car sa déclaration apparaît en tant qu’enfant de l' **\<complexType>** élément qui définit l' **\<CustomerType>** élément. De même, les attributs (**CustomerID**, **OrderID**et **ContactName**) sont locaux, et non globaux.  
  
##### <a name="to-create-a-working-sample-of-this-schema"></a>Pour créer un exemple fonctionnel de ce schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom targetNameSpace.xml.  
  
2.  Copiez le modèle suivant et collez-le dans un fichier texte. Enregistrez ce fichier sous le nom targetNameSpaceT.xml dans le répertoire où vous avez enregistré le fichier targetNameSpace.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="targetNamespace.xml"  
                       xmlns:CO="urn:MyNamespace" >  
        /CO:Customer[@CustomerID=1]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     La requête XPath dans le modèle retourne l' **\<Customer>** élément pour le client dont le CustomerID est 1. Notez que la requête XPath spécifie le préfixe d'espace de noms pour l'élément dans la requête et pas pour l'attribut. (Les attributs locaux ne sont pas qualifiés, comme spécifié dans le schéma.)  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (targetNameSpace.xml) est relatif au répertoire dans lequel le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\targetNamepsace.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Si le schéma spécifie des attributs **elementFormDefault** et **attributeFormDefault** avec la valeur **« Qualified »**, le document d’instance aura tous les éléments et attributs locaux qualifiés. Vous pouvez modifier le schéma précédent pour inclure ces attributs dans l' **\<xsd:schema>** élément et réexécuter le modèle. Dans la mesure où les attributs sont désormais également qualifiés dans l'instance, la requête XPath sera modifiée pour inclure le préfixe d'espace de noms.  
  
 La requête XPath modifiée est présentée ci-dessous :  
  
```  
/CO:Customer[@CO:CustomerID=1]  
```  
  
 Le document XML renvoyé est présenté ci-dessous :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
   <y0:Customer xmlns:y0="urn:MyNamespace" CustomerID="1" SalesPersonID="280">  
      <Order SalesOrderID="43860" CustomerID="1" />   
      <Order SalesOrderID="44501" CustomerID="1" />   
      <Order SalesOrderID="45283" CustomerID="1" />   
      <Order SalesOrderID="46042" CustomerID="1" />   
   </y0:Customer>  
</ROOT>  
```  
  
  

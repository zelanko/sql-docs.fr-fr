---
title: 'Création d’éléments constants à l’aide de sql : est-constant (SQLXML 4.0) | Documents Microsoft'
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
- element does not map [SQLXML]
- sql:is-constant
- XSD schemas [SQLXML], constant elements
- element mapping [SQLXML], constant elements
- is-constant annotation
- constant elements [SQLXML]
- annotated XSD schemas, constant elements
ms.assetid: 940eea1b-54f5-445f-b844-c894d9f3941b
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1b275f695057480bb2833d5b05e0cbef354a33ae
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042424"
---
# <a name="creating-constant-elements-using-sqlis-constant-sqlxml-40"></a>Création d'éléments constants à l'aide de sql:is-constant (SQLXML 4.0)
  Pour spécifier un élément constant, c'est-à-dire un élément du schéma XSD qui n'est mappé à aucune table ou colonne de base de données, vous pouvez utiliser l'annotation `sql:is-constant`. Cette annotation accepte une valeur booléenne (0 = false, 1 = true). Les valeurs acceptables sont 0, 1, true et false. L'annotation `sql:is-constant` peut être spécifiée sur un élément qui n'a pas d'attributs. Si elle est spécifiée sur un élément qui a la valeur true (ou 1), cet élément n'est pas mappé à la base de données mais apparaît néanmoins dans le document XML.  
  
 L'annotation `sql:is-constant` peut être utilisée pour :  
  
-   ajouter un élément de niveau supérieur au document XML. Le code XML requiert un seul élément de niveau supérieur (élément racine) pour le document ;  
  
-   Création d’éléments de conteneur, comme un  **\<commandes >** élément qui encapsule toutes les commandes.  
  
 Le `sql:is-constant` annotation peut être ajoutée à un  **\<complexType >** élément.  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l'aide des exemples suivants, vous devez répondre à certaines conditions requises. Pour plus d’informations, consultez [configuration requise pour exécuter les exemples de SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-sqlis-constant-to-add-a-container-element"></a>A. Spécification de sql:is-constant pour ajouter un élément conteneur  
 Ce schéma XSD, annotés  **\<CustomerOrders >** est défini comme un élément constant en spécifiant le `sql:is-constant` attribut avec une valeur de 1. Par conséquent,  **\<CustomerOrders >** n’est pas mappé à aucune table de base de données ou de la colonne. Cet élément constant se compose de la  **\<ordre >** des éléments enfants.  
  
 Bien que  **\<CustomerOrders >** ne correspond pas à une table de base de données ou une colonne, il apparaît toujours dans le XML résultant comme un élément conteneur qui contient le  **\<ordre >** éléments enfants.  
  
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
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="CustomerOrders" sql:is-constant="1" >  
          <xsd:complexType>  
            <xsd:sequence>  
              <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader"  
                           sql:relationship="CustOrders"   
                           maxOccurs="unbounded" >  
                <xsd:complexType>  
                   <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                   <xsd:attribute name="OrderDate" type="xsd:date" />  
                   <xsd:attribute name="CustomerID" type="xsd:string" />  
                </xsd:complexType>  
              </xsd:element>  
            </xsd:sequence>  
           </xsd:complexType>  
          </xsd:element>  
         </xsd:sequence>  
          <xsd:attribute name="CustomerID" type="xsd:string" />  
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom isConstant.xml.  
  
2.  Copiez le modèle suivant et collez-le dans un fichier texte. Enregistrez le fichier sous le nom isConstantT.xml dans le répertoire où vous avez enregistré le fichier isConstant.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="isConstant.xml">  
            Customer[@CustomerID=1]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (isConstant.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\isConstant.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [à l’aide d’ADO pour exécuter des requêtes SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le jeu de résultats partiel :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
<Customer CustomerID="1">   
  <CustomerOrders>   
    <Order SalesOrderID="43860" OrderDate="2001-08-01" CustomerID="1" />   
    <Order SalesOrderID="44501" OrderDate="2001-11-01" CustomerID="1" />   
    <Order SalesOrderID="45283" OrderDate="2002-02-01" CustomerID="1" />   
    <Order SalesOrderID="46042" OrderDate="2002-05-01" CustomerID="1" />   
    ...  
  </CustomerOrders>   
</Customer>   
</ROOT>  
```  
  
  
---
title: 'Exclusion d’éléments de schéma du Document XML résultant avec sql : mapped (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- annotated XSD schemas, excluding schema elements
- mapped annotation
- table mapping [SQLXML], excluding schema elements
- sql:mapped
- excluding schema elements
- element mapping [SQLXML], excluding schema elements
- column mapping [SQLXML]
- XSD schemas [SQLXML], excluding schema elements
- attribute mapping [SQLXML], excluding schema elements
- table/view mapping [SQLXML], excluding schema elements
ms.assetid: 7d2649dd-0038-4a2c-b16d-f80f7c306966
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 50ec2b9a4c35fdf16b8d7f696b9d227eb63ff7cb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63228465"
---
# <a name="excluding-schema-elements-from-the-resulting-xml-document-using-sqlmapped-sqlxml-40"></a>Exclusion d'éléments du schéma du document XML obtenu à l'aide de sql:mapped (SQLXML 4.0)
  Chaque élément et chaque attribut du schéma XSD sont mappés à une vue/table et à une colonne de base de données en raison du mappage par défaut. Si vous souhaitez créer un élément dans le schéma XSD qui n'est mappé à aucune table (vue) ou colonne de base de données et qui n'apparaît pas dans le XML, vous pouvez spécifier l'annotation `sql:mapped`.  
  
 L'annotation `sql:mapped` est particulièrement utile si le schéma ne peut pas être modifié ou si le schéma est utilisé pour valider le code XML d'autres sources et qu'il contient cependant des données qui ne sont pas stockées dans votre base de données. L'annotation `sql:mapped` diffère de `sql:is-constant` en ce que les éléments et les attributs non mappés n'apparaissent pas dans le document XML.  
  
 L'annotation `sql:mapped` prend une valeur booléenne (0 = faux, 1 = vrai). Les valeurs acceptables sont 0, 1, true et false.  
  
## <a name="examples"></a>Exemples  
 Pour créer des exemples fonctionnels à l'aide des exemples suivants, vous devez répondre à certaines conditions requises. Pour plus d’informations, consultez [configuration requise pour exécuter les exemples de SQLXML](../sqlxml/requirements-for-running-sqlxml-examples.md).  
  
### <a name="a-specifying-the-sqlmapped-annotation"></a>A. Spécification de l'annotation sql:mapped  
 Supposons que vous ayez un schéma XSD provenant d'une autre source. Ce schéma XSD se compose d’un  **\<Person.Contact >** élément avec **ContactID**, **FirstName**, **LastName**, et **HomeAddress** attributs.  
  
 Lors du mappage de ce schéma XSD pour la table Person.Contact dans la base de données AdventureWorks, `sql:mapped` est spécifié sur le **HomeAddress** attribut, car la table Employees ne stocke pas les adresses personnelles des employés. En conséquence, cet attribut n'est pas mappé avec la base de données et n'est pas retourné dans le document XML obtenu lorsqu'une requête XPath est spécifiée sur le schéma de mappage.  
  
 Le mappage par défaut a lieu pour le reste du schéma. Le  **\<Person.Contact >** élément est mappé à la table Person.Contact et tous les attributs sont mappés aux colonnes portant le même nom dans la table Person.Contact.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:attribute name="ContactID"   type="xsd:string"/>  
      <xsd:attribute name="FirstName"    type="xsd:string" />  
      <xsd:attribute name="LastName"     type="xsd:string" />  
      <xsd:attribute name="HomeAddress" type="xsd:string"   
                     sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier sous le nom sql-mapped.xml.  
  
2.  Copiez le modèle suivant et collez-le dans un fichier texte. Enregistrez le fichier sous le nom sql-mappedT.xml dans le même répertoire que celui où vous avez enregistré sql-mapped.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-mapped.xml">  
            /Person.Contact[@ContactID < 10]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (MySchema.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\sql-mapped.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [à l’aide d’ADO pour exécuter des requêtes SQLXML](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 L'ensemble de résultats est le suivant :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel" />   
  <Person.Contact ContactID="3" FirstName="Kim" LastName="Abercrombie" />   
  <Person.Contact ContactID="4" FirstName="Humberto" LastName="Acevedo" />   
  <Person.Contact ContactID="5" FirstName="Pilar" LastName="Ackerman" />   
  <Person.Contact ContactID="6" FirstName="Frances" LastName="Adams" />   
  <Person.Contact ContactID="7" FirstName="Margaret" LastName="Smith" />   
  <Person.Contact ContactID="8" FirstName="Carla" LastName="Adams" />   
  <Person.Contact ContactID="9" FirstName="Jay" LastName="Adams" />   
</ROOT>  
```  
  
 Notez que ContactID, FirstName et LastName sont présents, mais que HomeAddress ne l'est pas parce que le schéma de mappage a spécifié 0 pour l'attribut `sql:mapped`.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappage par défaut d’éléments XSD et d’attributs aux Tables et colonnes &#40;SQLXML 4.0&#41;](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
  

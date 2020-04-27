---
title: 'Spécification de la profondeur dans les relations récursives à l’aide de SQL : max-depth | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- max-depth annotation
- XPath queries [SQLXML], recursive relationships
- depth in recursive relationships [SQLXML]
- annotated XSD schemas, recursive relationships
- relationships [SQLXML], recursive relationships
- self joins
- recursive relationships [SQLXML]
- recursion [SQLXML]
- sql:max-depth
- recursive joins [SQLXML]
ms.assetid: 0ffdd57d-dc30-44d9-a8a0-f21cadedb327
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4b247efb895f037965620c7430a3dc41c33fe550
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66013656"
---
# <a name="specifying-depth-in-recursive-relationships-by-using-sqlmax-depth"></a>Spécification de la profondeur dans les relations récursives à l'aide de sql:max-depth
  Dans les bases de données relationnelles, lorsqu'une table est impliquée dans une relation avec elle-même, on utilise le terme de relation récursive. Par exemple, dans une relation responsable-subalterne, une table qui stocke des enregistrements d'employés est impliquée dans une relation avec elle-même. Dans ce cas, la table d'employés joue un rôle de responsable d'un côté de la relation, et la même table joue un rôle de subalterne de l'autre côté.  
  
 Les schémas de mappage peuvent inclure des relations récursives dans lesquelles un élément et son ancêtre sont du même type.  
  
## <a name="example-a"></a>Exemple A  
 Considérez la table ci-dessous :  
  
```  
Emp (EmployeeID, FirstName, LastName, ReportsTo)  
```  
  
 Dans cette table, la colonne ReportsTo stocke l'ID employé du responsable.  
  
 Supposez que vous souhaitez générer une hiérarchie XML des employés, dans laquelle l'employé responsable est en haut de la hiérarchie et les employés subalternes apparaissent dans la hiérarchie correspondante comme illustré dans le fragment d'exemple XML suivant. Ce fragment montre l' *arborescence récursive* pour l’employé 1.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
     <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
     <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
        <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
          <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
...  
...  
</root>  
```  
  
 Dans ce fragment, l'employé 5 est le subalterne de l'employé 4, l'employé 4 est le subalterne de l'employé 3 et les employés 3 et 2 sont les subalternes de l'employé 1.  
  
 Pour produire ce résultat, vous pouvez utiliser le schéma XSD suivant et spécifier une requête XPath contre lui. Le schéma décrit un ** \<élément emp>** de type EmployeeType, constitué d’un ** \<élément enfant EMP>** du même type, EmployeeType. Il s'agit d'une relation récursive (l'élément et son ancêtre sont du même type). En outre, le schéma utilise une ** \<>SQL : Relationship** pour décrire la relation parent-enfant entre le superviseur et le superviseur. Notez que dans ce ** \<SQL : Relationship>**, EMP est à la fois le parent et la table enfant.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="6" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 La relation étant récursive, vous devez trouver un moyen de spécifier la profondeur de récursivité dans le schéma. Sinon, le résultat sera une récursivité sans fin (employé subalterne à employé subalterne à employé, et ainsi de suite). L'annotation `sql:max-depth` vous permet de spécifier la profondeur de récursivité. Dans cet exemple particulier, pour spécifier une valeur pour `sql:max-depth`, vous devez connaître la profondeur de la hiérarchie de direction dans la société.  
  
> [!NOTE]  
>  Le schéma spécifie l'annotation `sql:limit-field`, mais ne spécifie pas l'annotation `sql:limit-value`. Cela limite le nœud supérieur dans la hiérarchie résultante uniquement aux employés qui ne sont subalternes de personne. (Rendez-vous NULL.) Si `sql:limit-field` vous spécifiez `sql:limit-value` et ne spécifiez pas (dont la valeur par défaut est null), l’annotation effectue cette. Si vous souhaitez que le XML résultant inclue chaque arborescence de direction possible (l'arborescence de direction pour chaque employé dans la table), supprimez l'annotation `sql:limit-field` du schéma.  
  
> [!NOTE]  
>  La procédure suivante utilise la base de données tempdb.  
  
#### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>Pour tester un exemple de requête XPath sur le schéma  
  
1.  Créez un exemple de table nommé Emp dans la base de données tempdb vers laquelle la racine virtuelle pointe.  
  
    ```  
    USE tempdb  
    CREATE TABLE Emp (  
           EmployeeID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    ```  
  
2.  Ajoutez les exemples de données suivants :  
  
    ```  
    INSERT INTO Emp values (1, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Emp values (2, 'Andrew', 'Fuller',1)  
    INSERT INTO Emp values (3, 'Janet', 'Leverling',1)  
    INSERT INTO Emp values (4, 'Margaret', 'Peacock',3)  
    INSERT INTO Emp values (5, 'Steven', 'Devolio',4)  
    INSERT INTO Emp values (6, 'Nancy', 'Buchanan',5)  
    INSERT INTO Emp values (7, 'Michael', 'Suyama',6)  
    ```  
  
3.  Copiez le code de schéma ci-dessus et collez-le dans un fichier texte. Enregistrez le fichier en tant que maxDepth.xml.  
  
4.  Copiez le modèle suivant et collez-le dans un fichier texte. Enregistrez le fichier en tant que maxDepthT.xml dans le même répertoire où vous avez enregistré maxDepth.xml. La requête dans le modèle retourne tous les employés de la table Emp.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="maxDepth.xml">  
        /Emp  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (maxDepth.xml) est relatif au répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\maxDepth.xml"  
    ```  
  
5.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle. Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le résultat obtenu :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
    <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
      <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
        <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
          <Emp FirstName="Nancy" EmployeeID="6" LastName="Buchanan">  
            <Emp FirstName="Michael" EmployeeID="7" LastName="Suyama" />   
          </Emp>  
        </Emp>  
      </Emp>  
    </Emp>  
  </Emp>  
</root>  
```  
  
> [!NOTE]  
>  Pour produire différentes profondeurs de hiérarchies dans le résultat, modifiez la valeur de l'annotation `sql:max-depth` dans le schéma et réexécutez le modèle après chaque modification.  
  
 Dans le schéma précédent, tous les éléments ** \<EMP>** avaient exactement le même jeu d’attributs (**EmployeeID**, **FirstName**et **LastName**). Le schéma suivant a été légèrement modifié pour retourner un attribut de **rendez** -vous supplémentaire pour tous les ** \<éléments EMP>** qui sont en rapport avec un responsable.  
  
 Par exemple, ce fragment XML affiche les subalternes de l'employé 1 :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
<Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2"   
       ReportsTo="1" LastName="Fuller" />   
  <Emp FirstName="Janet" EmployeeID="3"   
       ReportsTo="1" LastName="Leverling">  
...  
...  
```  
  
 Voici le schéma modifié :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:documentation>  
      Customer-Order-Order Details Schema  
      Copyright 2000 Microsoft. All rights reserved.  
    </xsd:documentation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"  
                  parent-key="EmployeeID"  
                  child="Emp"  
                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
                   type="EmpType"   
                   sql:relation="Emp"   
                   sql:key-fields="EmployeeID"   
                   sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmpType">  
    <xsd:sequence>  
       <xsd:element name="Emp"   
                    type="EmpType"   
                    sql:relation="Emp"   
                    sql:key-fields="EmployeeID"  
                    sql:relationship="SupervisorSupervisee"  
                    sql:max-depth="6"/>  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:int" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
    <xsd:attribute name="ReportsTo" type="xsd:int" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
## <a name="sqlmax-depth-annotation"></a>Annotation sql:max-depth  
 Dans un schéma constitué de relations récursives, la profondeur de récursivité doit être spécifiée explicitement dans le schéma. Cela est nécessaire afin de produire avec succès la requête FOR XML EXPLICIT correspondante qui retourne les résultats demandés.  
  
 Utilisez l'annotation `sql:max-depth` dans le schéma pour spécifier la profondeur de récursivité dans une relation récursive décrite dans le schéma. La valeur de l'annotation `sql:max-depth` est un entier positif (1 à 50) qui indique le nombre de récursivités : une valeur de 1 arrête la récursivité à l'élément pour lequel l'annotation `sql:max-depth` est spécifiée ; une valeur de 2 arrête la récursivité au niveau suivant l'élément auquel `sql:max-depth` est spécifié ; et ainsi de suite.  
  
> [!NOTE]  
>  Dans l'implémentation sous-jacente, une requête XPath spécifiée contre un schéma de mappage est convertie en requête SELECT ... FOR XML EXPLICIT. Cette requête nécessite que vous spécifiiez une profondeur de récursivité finie. Plus la valeur que vous spécifiez pour `sql:max-depth` est élevée, plus la requête FOR XML EXPLICIT générée est grande. Cela risque d'allonger la durée de récupération.  
  
> [!NOTE]  
>  Les codes de mise à jour (updategrams) et chargements en masse XML ignorent l'annotation max-depth. Cela signifie que les insertions ou mises à jour récursives ont lieu indépendamment de la valeur que vous spécifiez pour max-depth.  
  
## <a name="specifying-sqlmax-depth-on-complex-elements"></a>Spécification de sql:max-depth sur des éléments complexes  
 L'annotation `sql:max-depth` peut être spécifiée sur tout élément de contenu complexe.  
  
### <a name="recursive-elements"></a>Éléments récursifs  
 Si `sql:max-depth` est spécifié sur l'élément parent et sur l'élément enfant dans une relation récursive, l'annotation `sql:max-depth` spécifiée sur le parent est prioritaire. Par exemple, dans le schéma suivant, l'annotation `sql:max-depth` est spécifiée à la fois sur les éléments employés parents et enfants. Dans ce cas, `sql:max-depth=4`, spécifié sur l' ** \<élément emp>** parent (jouent un rôle de superviseur), est prioritaire. La `sql:max-depth` spécifiée sur l’élément ** \<EMP>** enfant (qui jouent un rôle de superviseur) est ignorée.  
  
#### <a name="example-b"></a>Exemple B  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo"   
                          sql:max-depth="3" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="2" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 Pour tester ce schéma, suivez les étapes fournies pour l’exemple A, plus haut dans cette rubrique.  
  
### <a name="nonrecursive-elements"></a>Éléments non récursifs  
 Si l'annotation `sql:max-depth` est spécifiée sur un élément dans le schéma qui ne provoque pas de récursivité, elle est ignorée. Dans le schéma suivant, un ** \<élément emp>** se compose d’une ** \<constante>** élément enfant qui, à son tour, possède un ** \<élément enfant>EMP** .  
  
 Dans ce schéma, l' `sql:max-depth` annotation spécifiée sur la ** \<constante>** élément est ignorée, car il n’y a pas de récursivité entre le ** \<parent EMP>** et la ** \<constante>** élément enfant. Toutefois, il existe une récurrence entre ** \<EMP>** ancêtre et ** \<EMP>** Child. Le schéma spécifie l'annotation `sql:max-depth` sur les deux. Par conséquent, `sql:max-depth` l’annotation spécifiée sur l’ancêtre (**\<EMP>** dans le rôle superviseur) est prioritaire.  
  
#### <a name="example-c"></a>Exemple C  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"   
                  child="Emp"   
                  parent-key="EmployeeID"   
                  child-key="ReportsTo"/>  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
               sql:relation="Emp"   
               type="EmpType"  
               sql:limit-field="ReportsTo"  
               sql:max-depth="1" />  
    <xsd:complexType name="EmpType" >  
      <xsd:sequence>  
       <xsd:element name="Constant"   
                    sql:is-constant="1"   
                    sql:max-depth="20" >  
         <xsd:complexType >  
           <xsd:sequence>  
            <xsd:element name="Emp"   
                         sql:relation="Emp" type="EmpType"  
                         sql:relationship="SupervisorSupervisee"   
                         sql:max-depth="3" />  
         </xsd:sequence>  
         </xsd:complexType>  
         </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="EmployeeID" type="xsd:int" />  
    </xsd:complexType>  
</xsd:schema>  
```  
  
 Pour tester ce schéma, suivez les étapes fournies pour l'Exemple A, plus haut dans cette rubrique.  
  
## <a name="complex-types-derived-by-restriction"></a>Types complexes dérivés par restriction  
 Si vous avez une dérivation de type complexe par ** \<restriction>**, les éléments du type complexe de base correspondant ne `sql:max-depth` peuvent pas spécifier l’annotation. Dans ces cas-là, l'annotation `sql:max-depth` peut être ajoutée à l'élément du type dérivé.  
  
 En revanche, si vous avez une dérivation de type complexe par ** \<extension>**, les éléments du type complexe de base correspondant peuvent spécifier l' `sql:max-depth` annotation.  
  
 Par exemple, le schéma XSD suivant génère une erreur car l'annotation `sql:max-depth` est spécifiée sur le type de base. Cette annotation n’est pas prise en charge sur un type dérivé par ** \<une restriction>** à partir d’un autre type. Pour résoudre ce problème, vous devez modifier le schéma et spécifier l'annotation `sql:max-depth` sur l'élément dans le type dérivé.  
  
#### <a name="example-d"></a>Exemple D  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:complexType name="CustomerBaseType">   
    <xsd:sequence>  
       <xsd:element name="CID" msdata:field="CustomerID" />  
       <xsd:element name="CompanyName"/>  
       <xsd:element name="Customers" msdata:max-depth="3">  
         <xsd:annotation>  
           <xsd:appinfo>  
             <msdata:relationship  
                     parent="Customers"  
                     parent-key="CustomerID"  
                     child-key="CustomerID"  
                     child="Customers" />  
           </xsd:appinfo>  
         </xsd:annotation>  
       </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
  <xsd:element name="Customers" type="CustomerType"/>  
  <xsd:complexType name="CustomerType">  
    <xsd:complexContent>  
       <xsd:restriction base="CustomerBaseType">  
          <xsd:sequence>  
            <xsd:element name="CID"   
                         type="xsd:string"/>  
            <xsd:element name="CompanyName"   
                         type="xsd:string"  
                         msdata:field="CName" />  
            <xsd:element name="Customers"   
                         type="CustomerType" />  
          </xsd:sequence>  
       </xsd:restriction>  
    </xsd:complexContent>  
  </xsd:complexType>  
</xsd:schema>   
```  
  
 Dans le schéma, `sql:max-depth` est spécifié sur un type complexe `CustomerBaseType`. Le schéma spécifie également un `CustomerType` `CustomerBaseType` ** \<élément Customer>** de type, dérivé de. Une requête XPath spécifiée sur un tel schéma génère une erreur car `sql:max-depth` n'est pas pris en charge sur un élément défini dans un type de base de restriction.  
  
## <a name="schemas-with-a-deep-hierarchy"></a>Schémas avec une hiérarchie profonde  
 Vous pouvez avoir un schéma qui inclut une hiérarchie profonde dans laquelle un élément contient un élément enfant, qui à son tour contient un autre élément enfant, et ainsi de suite. Si l'annotation `sql:max-depth` spécifiée dans un tel schéma génère un document XML qui inclut une hiérarchie de plus de 500 niveaux (avec l'élément de niveau supérieur au niveau 1, son enfant au niveau 2, et ainsi de suite), une erreur est retournée.  
  
  

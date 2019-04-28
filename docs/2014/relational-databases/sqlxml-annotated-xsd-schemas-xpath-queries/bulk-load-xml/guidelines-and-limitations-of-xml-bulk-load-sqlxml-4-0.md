---
title: Instructions et Limitations de XML en bloc charge (SQLXML 4.0) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
ms.assetid: c5885d14-c7c1-47b3-a389-455e99a7ece1
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b7a569bbc5672b0fc5996507e37ed250721bd2fe
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62717976"
---
# <a name="guidelines-and-limitations-of-xml-bulk-load-sqlxml-40"></a>Règles et limitations du chargement en masse XML (SQLXML 4.0)
  Lorsque vous utilisez le chargement en masse XML, vous devez connaître les indications et les limitations suivantes :  
  
-   Les schémas insérés ne sont pas pris en charge.  
  
     Si vous possédez un schéma inséré dans le document XML source, le chargement en masse XML ignore ce schéma. Vous spécifiez le schéma de mappage pour le chargement en masse XML externe aux données XML. Vous ne pouvez pas spécifier le schéma de mappage sur un nœud à l’aide de la **xmlns = « x : schema »** attribut.  
  
-   Le système vérifie qu'un document XML est correct, mais ne le valide pas.  
  
     Chargement en masse XML vérifie le document XML pour déterminer s’il s’agit bien-formées-que, pour vous assurer que le code XML est conforme aux exigences en matière de syntaxe de recommandation de XML 1.0 du World Wide Web Consortium. Si le document n'est pas correct, le chargement en masse XML annule le traitement et retourne une erreur. La seule exception à ceci est lorsque le document est un fragment (par exemple, le document n'a aucun élément racine unique), auquel cas le chargement en masse XML chargera le document.  
  
     Le chargement en masse XML ne valide pas le document par rapport à tout schéma de données XML ou DTD qui est défini ou référencé dans le fichier de données XML. De plus, le chargement en masse XML ne valide pas le fichier de données XML par rapport au schéma de mappage fourni.  
  
-   Toutes informations de prologue XML sont ignorées.  
  
     Chargement en masse XML ignore toutes les informations avant et après le \<racine > élément dans le document XML. Par exemple, le chargement en masse XML ignore toutes les déclarations XML, les définitions DTD internes, les références DTD externes, les commentaires, etc.  
  
-   Si vous possédez un schéma de mappage qui définit une relation clé primaire/clé étrangère entre deux tables (par exemple, entre Customer et CustOrder), la table avec la clé primaire doit être décrite en premier dans le schéma. La table avec la colonne de clé étrangère doit apparaître ultérieurement dans le schéma. La raison à cela est que l’ordre dans lequel les tables sont identifiées dans le schéma est l’ordre qui est utilisé pour les charger dans la base de données. Par exemple, le schéma XDR suivant produira une erreur lorsqu’il est utilisé dans le chargement en masse XML, car le  **\<ordre >** élément est décrit avant le  **\<client >** élément. La colonne CustomerID dans CustOrder est une colonne de clé étrangère qui fait référence à la colonne de clé primaire CustomerID dans la table Cust.  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
        <ElementType name="Order" sql:relation="CustOrder" >  
          <AttributeType name="OrderID" />  
          <AttributeType name="CustomerID" />  
          <attribute type="OrderID" />  
          <attribute type="CustomerID" />  
        </ElementType>  
  
       <ElementType name="CustomerID" dt:type="int" />  
       <ElementType name="CompanyName" dt:type="string" />  
       <ElementType name="City" dt:type="string" />  
  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
       <ElementType name="Customers" sql:relation="Cust"   
                         sql:overflow-field="OverflowColumn"  >  
          <element type="CustomerID" sql:field="CustomerID" />  
          <element type="CompanyName" sql:field="CompanyName" />  
          <element type="City" sql:field="City" />  
          <element type="Order" >   
               <sql:relationship  
                   key-relation="Cust"  
                    key="CustomerID"  
                    foreign-key="CustomerID"  
                    foreign-relation="CustOrder" />  
          </element>  
       </ElementType>  
    </Schema>  
    ```  
  
-   Si le schéma ne spécifie pas de colonnes de dépassement à l'aide de l'annotation `sql:overflow-field`, le chargement en masse XML ignore toutes les données qui sont présentes dans le document XML, mais qui ne sont pas décrites dans le schéma de mappage.  
  
     Le chargement en masse XML applique le schéma de mappage que vous avez spécifié toutes les fois qu'il rencontre des balises connues dans le flux de données XML. Il ignore les données qui sont présentes dans le document XML mais qui ne sont pas décrites dans le schéma. Par exemple, supposons que vous avez un schéma de mappage qui décrit un  **\<client >** élément. Le fichier de données XML a une  **\<AllCustomers >** racine de balise (qui n’est pas décrite dans le schéma) qui englobe tous les  **\<client >** éléments :  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
      <Customer>...</Customer>  
       ...  
    </AllCustomers>  
    ```  
  
     Dans ce cas, le chargement en masse XML ignore les  **\<AllCustomers >** élément et commence le mappage à la  **\<client >** élément. Le chargement en masse XML ignore les éléments qui ne sont pas décrits dans le schéma mais qui sont présents dans le document XML.  
  
     Envisagez un autre fichier de données source XML contienne  **\<ordre >** éléments. Ces éléments ne sont pas décrits dans le schéma de mappage :  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      ...  
    </AllCustomers>  
    ```  
  
     Chargement en masse XML ignore ces  **\<ordre >** éléments. Mais si vous utilisez le `sql:overflow-field`annotation dans le schéma pour identifier une colonne comme une colonne de dépassement, le chargement en masse XML stocke toutes les données non consommées dans cette colonne.  
  
-   Les sections CDATA et les références d'entité sont traduites en chaînes équivalentes avant d'être stockées dans la base de données.  
  
     Dans cet exemple, une section CDATA encapsule la valeur de la  **\<ville >** élément. Chargement en masse XML extrait la valeur de chaîne (« NY ») avant d’insérer le  **\<ville >** élément dans la base de données.  
  
    ```  
    <City><![CDATA[NY]]> </City>  
    ```  
  
     Le chargement en masse XML ne conserve pas les références d'entité.  
  
-   Si le schéma de mappage spécifie la valeur par défaut pour un attribut et que les données de source XML ne contiennent pas cet attribut, le chargement en masse XML utilise la valeur par défaut.  
  
     L’exemple de schéma XDR suivant assigne une valeur par défaut pour le **HireDate** attribut :  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
  
       <ElementType name="Customers" sql:relation="Cust3" >  
          <AttributeType name="CustomerID" dt:type="int"  />  
          <AttributeType name="HireDate"  default="2000-01-01" />  
          <AttributeType name="Salary"   />  
  
          <attribute type="CustomerID" sql:field="CustomerID" />  
          <attribute type="HireDate"   sql:field="HireDate"  />  
          <attribute type="Salary"     sql:field="Salary"    />  
       </ElementType>  
    </Schema>  
    ```  
  
     Dans ces données XML, le **HireDate** attribut est absent de la seconde  **\<clients >** élément. Lorsque le chargement en masse XML insère la seconde  **\<clients >** élément dans la base de données, il utilise la valeur par défaut qui est spécifiée dans le schéma.  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1" HireDate="1999-01-01" Salary="10000" />  
      <Customers CustomerID="2" Salary="10000" />  
    </ROOT>  
    ```  
  
-   L'annotation `sql:url-encode` n'est pas prise en charge :  
  
     Vous ne pouvez pas spécifier une URL dans l'entrée de données XML et vous attendre à ce que le chargement en masse lise les données à cet emplacement.  
  
     Les tables qui sont identifiées dans le schéma de mappage sont créées (la base de données doit exister). Si un ou plusieurs des tables existe déjà dans la base de données, la sgdroptables, propriété détermine si ces tables préexistantes doivent être supprimées et recréées.  
  
-   Si vous spécifiez la propriété SchemaGen (par exemple, SchemaGen = true), les tables sont identifiées dans le schéma de mappage sont créées. Mais SchemaGen ne crée pas de toutes les contraintes (telles que les contraintes PRIMARY KEY/FOREIGN KEY) sur ces tables à une exception près : Si les nœuds XML qui constituent la clé primaire dans une relation sont définies comme ayant un type XML de l’ID (autrement dit, `type="xsd:ID"` pour XSD) et la sguseid, propriété est définie sur True pour SchemaGen, non seulement les clés primaires sont créées à partir de l’ID typées des nœuds , mais les relations clé primaire/étrangère clées sont créées à partir de relations de schéma de mappage.  
  
-   SchemaGen n’utilise pas les facettes du schéma XSD et les extensions pour générer les données relationnelles [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] schéma.  
  
-   Si vous spécifiez la propriété SchemaGen (par exemple, SchemaGen = true) sur le chargement en masse, uniquement les tables (et pas les vues de nom partagé) spécifiées sont mises à jour.  
  
-   SchemaGen fournit uniquement les fonctionnalités de base pour générer le schéma relationnel à partir de XSD annoté. L'utilisateur doit modifier manuellement les tables générées, si nécessaire.  
  
-   Où plus qu’une relation existe entre les tables, SchemaGen tente de créer une relation unique qui inclut toutes les clés impliquées entre les deux tables. Cette limitation peut être à l'origine d'une erreur [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
-   Lorsque vous chargez en masse des données XML dans une base de données, il doit y avoir au moins un attribut ou élément enfant dans le schéma de mappage qui est mappé à une colonne de base de données.  
  
-   Si vous insérez des valeurs de date à l'aide du chargement en masse XML, les valeurs doivent être spécifiées au format (-)SSAA-MM-JJ((+-)TZ). Ceci est le format XSD standard pour la date.  
  
-   Certains indicateurs de propriété ne sont pas compatibles avec d'autres indicateurs de propriété. Par exemple, le chargement en masse ne prend pas en charge `Ignoreduplicatekeys=true` avec `Keepidentity=false`. Lorsque `Keepidentity=false`, le chargement en masse attend que le serveur génère les valeurs de clés. Les tables doivent avoir une contrainte `IDENTITY` sur la clé. Le serveur ne générera pas de clés dupliquées, ce qui signifie qu'il est inutile d'affecter la valeur `Ignoreduplicatekeys` à `true`. `Ignoreduplicatekeys` ne doit avoir la valeur `true` que lors du téléchargement des valeurs de clés primaires à partir du flux de données entrant dans une table qui comporte des lignes et qu'il existe un risque potentiel de conflit des valeurs de clés primaires.  
  
  

---
title: Spécification de variables XPath dans les requêtes XPath (SQLXML)
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], XPath variables
- XPath variables [SQLXML]
ms.assetid: c11ab816-11b8-4131-8b77-c03fe500fa10
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f73bb6880fb19f3e49387d9d3d0bb57100ffdf42
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "75252540"
---
# <a name="specifying-xpath-variables-in-xpath-queries-sqlxml-40"></a>Spécification de variables XPath dans les requêtes XPath (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Les exemples suivants expliquent comment des variables XPath sont passées dans des requêtes XPath. Les requêtes XPath de ces exemples sont spécifiées par rapport au schéma de mappage contenu dans SampleSchema1.xml. Pour plus d’informations sur cet exemple de schéma, consultez [exemple de schéma XSD annoté pour les exemples XPath &#40;SQLXML 4,0&#41;](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-use-the-xpath-variables"></a>R. Utilisation des variables XPath  
 Un exemple de modèle se compose de deux requêtes XPath. Chacune des requêtes XPath accepte un paramètre. Le modèle spécifie également les valeurs par défaut de ces paramètres. Les valeurs par défaut sont utilisées si les valeurs des paramètres ne sont pas spécifiées. Deux paramètres avec des valeurs par défaut sont spécifiés dans ** \<SQL : header>**.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:header>  
     <sql:param name='CustomerID'>1</sql:param>  
     <sql:param name='ContactID'>1</sql:param>   
  </sql:header>  
  <sql:xpath-query mapping-schema="SampleSchema1.xml">  
    Customer[@CustomerID=$CustomerID]   
  </sql:xpath-query >  
  <sql:xpath-query mapping-schema="SampleSchema1.xml">  
   Contact[@ContactID=$ContactID]   
  </sql:xpath-query>  
</ROOT>  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Pour tester la requête XPath par rapport au schéma de mappage  
  
1.  Copiez l' [exemple de code de schéma](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/samples/sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) et collez-le dans un fichier texte. Enregistrez ce fichier sous le nom SampleSchema1.xml.  
  
2.  Créez le modèle suivant (XPathVariables.xml) et enregistrez-le dans le répertoire où :  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:header>  
         <sql:param name='CustomerID'>1</sql:param>  
         <sql:param name='ContactID'>1</sql:param>   
      </sql:header>  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Customer[@CustomerID=$CustomerID]   
      </sql:xpath-query >  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
       Contact[@ContactID=$ContactID]   
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (SampleSchema1.xml) varie en fonction du répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle. Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
> [!NOTE]  
>  Dans cet exemple, aucun paramètre n'est passé. Ce sont donc les valeurs de paramètre par défaut qui sont utilisées.  
  
  

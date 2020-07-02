---
title: Exécution de requêtes XPath (fournisseur SQLXMLOLEDB)
description: Découvrez comment utiliser des propriétés spécifiques au fournisseur SQLXMLOLEDB lors de l’exécution de requêtes XPath.
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing XPath queries
- queries [SQLXML], SQLXMLOLEDB Provider
- Base Path property
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- Mapping Schema property
ms.assetid: 19063222-dc9c-48ae-a55f-778103674a9e
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d5a337408ef4cf1a2e4b72cbb20f9c64681efd0c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85650319"
---
# <a name="executing-xpath-queries-sqlxmloledb-provider"></a>Exécution de requêtes XPath (fournisseur SQLXMLOLEDB)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Cet exemple illustre l'utilisation des propriétés suivantes spécifiques au fournisseur SQLXMLOLEDB :  
  
-   **ClientSideXML**  
  
-   **Chemin de base**  
  
-   **Schéma de mappage**  
  
 Dans cet exemple d'application ADO, une requête XPath (root) est spécifiée contre un schéma de mappage XSD (MySchema.xml). Le schéma a un **\<Contacts>** élément avec les attributs **ContactID**, **FirstName**et **LastName** . Dans le schéma, le mappage par défaut a lieu : un nom d'élément mappe à la table avec le même nom et les attributs de type simple mappent aux colonnes avec les mêmes noms.  
  
```  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
   xmlns:sql='urn:schemas-microsoft-com:mapping-schema'>  
 <xsd:element name= 'root' sql:is-constant='1'>   
    <xsd:complexType>  
       <xsd:sequence>  
         <xsd:element ref = 'Contacts'/>  
       </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
  <xsd:element name='Contacts' sql:relation='Person.Contact'>   
     <xsd:complexType>  
          <xsd:attribute name='ContactID' type='xsd:integer' />  
          <xsd:attribute name='FirstName' type='xsd:string'/>   
          <xsd:attribute name='LastName' type='xsd:string' />   
     </xsd:complexType>  
   </xsd:element>  
</xsd:schema>  
```  
  
 La propriété schéma de mappage fournit le schéma de mappage par rapport auquel la requête XPath est exécutée. Le schéma de mappage peut être un schéma XSD ou XDR. La propriété chemin d’accès de base fournit le chemin d’accès du fichier au schéma de mappage.  
  
 La propriété ClientSideXML a la valeur true. Par conséquent, le document XML est généré sur le client.  
  
 Dans l'application, une requête XPath est spécifiée directement. Par conséquent, le dialecte XPath {ec2a4293-e898-11d2-b1b7-00c04f680c56} doit être inclus.  
  
> [!NOTE]  
>  Dans le code, vous devez fournir le nom de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans la chaîne de connexion. En outre, cet exemple spécifie l’utilisation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) pour le fournisseur de données qui requiert l’installation d’un logiciel client réseau supplémentaire. Pour plus d’informations, consultez [Configuration système requise pour SQL Server Native Client](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md).  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security= SSPI;"  
  
oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
  
oTestCommand.CommandText = "root"  
oTestStream.Open  
oTestCommand.Dialect = "{ec2a4293-e898-11d2-b1b7-00c04f680c56}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\XPathDirect\"  
oTestCommand.Properties("Mapping Schema").Value = "mySchema.xml"  
oTestCommand.Properties("Output Encoding") = "utf-8"  
oTestCommand.Execute , , adExecuteStream  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
  

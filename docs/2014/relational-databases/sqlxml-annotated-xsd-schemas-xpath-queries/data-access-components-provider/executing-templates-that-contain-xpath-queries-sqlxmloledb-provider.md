---
title: Exécution de modèles contenant des requêtes XPath (fournisseur SQLXMLOLEDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, executing template files
- Base Path property
- templates [SQLXML], XPath queries
- XPath queries [SQLXML], templates
- XPath queries [SQLXML], SQLXMLOLEDB Provider
- Mapping Schema property
- XML templates [SQLXML]
ms.assetid: 7368c188-607e-459e-8254-8f23352dfa01
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9c4b5d51597f41b5355acd4995aaf7f988ed53a5
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66013089"
---
# <a name="executing-templates-that-contain-xpath-queries-sqlxmloledb-provider"></a>Exécution de modèles contenant des requêtes XPath (fournisseur SQLXMLOLEDB)
  Cet exemple indique comment utiliser les propriétés suivantes spécifiques au fournisseur SQLXMLOLEDB :  
  
-   ClientSideXML  
  
-   Chemin de base  
  
-   Schéma de mappage  
  
 Dans cet exemple d’application ADO, un modèle XML qui se compose d’une requête XPath (racine) est spécifié par rapport au schéma de mappage XSD (MySchema. Xml) décrit dans [exécution de requêtes xpath &#40;&#41;fournisseur SQLXMLOLEDB ](executing-xpath-queries-sqlxmloledb-provider.md).  
  
 La propriété schéma de mappage fournit le schéma de mappage XSD sur lequel la requête XPath est exécutée. La propriété chemin d’accès de base fournit le chemin d’accès du fichier au schéma de mappage.  
  
 La propriété ClientSideXML a la valeur true. Par conséquent, le document XML est généré sur le client.  
  
 Dans l'application, une requête XPath est spécifiée directement. Par conséquent, le dialecte {5d531cb2-e6ed-11d2-b252-00c04f681b71} doit être inclus.  
  
> [!NOTE]  
>  Dans le code, vous devez fournir le nom de l'instance de Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans la chaîne de connexion. En outre, cet exemple spécifie l’utilisation [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de Native Client (SQLNCLI11) pour le fournisseur de données qui requiert l’installation d’un logiciel client réseau supplémentaire. Pour plus d’informations, consultez [Configuration système requise pour SQL Server Native Client](../../native-client/system-requirements-for-sql-server-native-client.md).  
  
```  
Option Explicit  
Sub Main()  
  
   Dim oTestStream As New ADODB.Stream  
   Dim oTestConnection As New ADODB.Connection  
   Dim oTestCommand As New ADODB.Command  
  
   oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI;"  
  
   oTestCommand.ActiveConnection = oTestConnection  
   oTestCommand.Properties("ClientSideXML") = "False"  
  
   oTestCommand.CommandText = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'> " & _  
        " <sql:xpath-query mapping-schema='mySchema.xml' > " & _  
        "   root " & _  
        "   </sql:xpath-query> " & _  
        " </ROOT> "  
   oTestStream.Open  
   ' You need the dialect if you are executing a template.  
   oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
   oTestCommand.Properties("Output Stream").Value = oTestStream  
   oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\TemplateWithXPath\"  
   oTestCommand.Properties("Mapping Schema").Value = "mySchema.xml"  
   oTestCommand.Properties("Output Encoding") = "utf-8"  
   oTestCommand.Execute , , adExecuteStream  
   oTestStream.Position = 0  
   oTestStream.Charset = "utf-8"  
   Debug.Print oTestStream.ReadText(adReadAll)  
  
End Sub  
  
Sub Form_Load()  
   Main  
End Sub  
```  
  
 Voici le schéma :  
  
```  
<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'  
   xmlns:sql='urn:schemas-microsoft-com:mapping-schema'>  
 <xsd:element name= 'root' sql:is-constant='1'>   
    <xsd:complexType>  
       <xsd:sequence>  
         <xsd:element ref = 'Contact'/>  
       </xsd:sequence>  
    </xsd:complexType>  
  </xsd:element>  
  
  <xsd:element name='Contact' sql:relation='Person.Contact'>  
     <xsd:complexType>  
          <xsd:attribute name='ContactID' type='xsd:integer' />  
          <xsd:attribute name='FirstName' type='xsd:string'/>   
          <xsd:attribute name='LastName' type='xsd:string' />   
     </xsd:complexType>  
   </xsd:element>  
</xsd:schema>  
```  
  
  

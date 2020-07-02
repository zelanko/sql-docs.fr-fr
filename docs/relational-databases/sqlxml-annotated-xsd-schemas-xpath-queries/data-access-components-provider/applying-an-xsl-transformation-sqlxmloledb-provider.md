---
title: Appliquer une transformation XSL (SQLXMLOLEDB)
description: Découvrez comment appliquer une transformation XSL dans une application ADO à l’aide des propriétés ClientSideXML et xsl du fournisseur SQLXMLOLEDB.
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXMLOLEDB Provider, applying XSL transformations
- applying XSL transformations [SQLXML]
- xsl property
- Base Path property
- XSL Transformations [SQLXML]
ms.assetid: cb5e41ab-dd20-4873-af20-f417bd1bbf6d
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 567eb423d4def73169fc8d06828af1c34e536136
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85650414"
---
# <a name="applying-an-xsl-transformation-sqlxmloledb-provider"></a>Application d'une transformation XSL (fournisseur SQLXMLOLEDB)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Dans cet exemple d'application ADO, une requête SQL est exécutée et le langage XSLT est appliqué au résultat. L’affectation de la valeur true à la propriété ClientSideXML applique le traitement de l’ensemble de lignes côté client. Le dialecte de commande a pour valeur {5d531cb2-e6ed-11d2-b252-00c04f681b71} car la requête SQL est spécifiée dans un modèle et que ce dialecte doit être spécifié lors de l'exécution d'un modèle. La propriété XSL spécifie le fichier XSL à utiliser pour appliquer la transformation. La valeur de la propriété chemin de base est utilisée pour rechercher le fichier XSL. Si vous spécifiez un chemin d’accès dans la valeur de la propriété XSL, le chemin d’accès est relatif au chemin d’accès spécifié dans la propriété chemin d’accès de base.  
  
 Cet exemple indique comment utiliser les propriétés suivantes spécifiques au fournisseur SQLXMLOLEDB :  
  
-   ClientSideXML  
  
-   xsl  
  
 Dans cet exemple d'application ADO côté client, un modèle XML contenant une requête SQL est exécuté sur le serveur.  
  
 Étant donné que la propriété ClientSideXML a la valeur true, l’instruction SELECT sans la clause FOR XML est envoyée au serveur. Le serveur exécute la requête et retourne un ensemble de lignes au client. Le client applique ensuite la transformation FOR XML à l'ensemble de lignes et génère le document XML.  
  
 La propriété XSL est spécifiée dans l’application ; par conséquent, la transformation XSL est appliquée au document XML généré sur le client, et le résultat est une table à deux colonnes.  
  
 Pour exécuter la commande de modèle, vous devez spécifier le dialecte de modèle XML-{5d531cb2-e6ed-11d2-b252-00c04f681b71}.  
  
> [!NOTE]  
>  Dans le code, vous devez fournir le nom de l'instance de Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans la chaîne de connexion. En outre, cet exemple spécifie l'utilisation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client comme fournisseur de données, ce qui requiert l'installation d'un logiciel client réseau supplémentaire. Pour plus d’informations, consultez [Configuration système requise pour SQL Server Native Client](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md).  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI;"  
Set oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = _  
        "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql' >" & _  
       " <sql:query> " & _  
        "   SELECT TOP 25 FirstName, LastName FROM Person.Contact FOR XML AUTO " & _  
        "   </sql:query> " & _  
        " </ROOT> "  
oTestStream.Open  
' You need the dialect if you are executing a template.  
oTestCommand.Dialect = "{5d531cb2-e6ed-11d2-b252-00c04f681b71}"  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("Base Path").Value = "c:\Schemas\SQLXML4\ExecuteTemplateWithXSL\"  
oTestCommand.Properties("xsl").Value = "myxsl.xsl"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
 Le modèle XSL suit. Le résultat de l'application de ce modèle XSL est une table à deux colonnes.  
  
```  
<?xml version='1.0' encoding='UTF-8'?>            
 <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">   
  
    <xsl:template match = 'Person.Contact'>  
       <TR>  
         <TD><xsl:value-of select = '@FirstName' /></TD>  
         <TD><B><xsl:value-of select = '@LastName' /></B></TD>  
       </TR>  
    </xsl:template>  
    <xsl:template match = '/'>  
      <HTML>  
        <HEAD>  
           <STYLE>th { background-color: #CCCCCC }</STYLE>  
        </HEAD>  
        <BODY>  
         <TABLE border='1' style='width:300;'>  
           <TR><TH colspan='2'>Contacts</TH></TR>  
           <TR>  
              <TH >First name</TH>  
              <TH>Last name</TH>  
           </TR>  
           <xsl:apply-templates select = 'ROOT' />  
         </TABLE>  
        </BODY>  
      </HTML>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
  

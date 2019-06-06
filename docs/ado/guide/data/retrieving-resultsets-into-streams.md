---
title: Récupération des jeux de résultats dans des flux | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/20/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- streams [ADO], retrieving query results
- query results into stream [ADO]
- retrieving results into stream [ADO]
ms.assetid: 996c1321-c926-4f57-8297-85c8c20de974
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b784553302bf9df30750f239291ca179ecf6cf74
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66701875"
---
# <a name="retrieving-resultsets-into-streams"></a>Récupération de jeux de résultats dans les flux
Au lieu de recevoir les résultats dans le traditionnel **Recordset** de l’objet, ADO peut récupérer à la place les résultats de la requête dans un flux de données. ADO **Stream** objet (ou d’autres objets qui prennent en charge le modèle COM **IStream** interface, tels que l’ASP **demande** et **réponse** objets ) peuvent être utilisées pour contenir ces résultats. Une utilisation de cette fonctionnalité consiste à récupérer les résultats au format XML. Avec SQL Server, par exemple, les résultats XML peuvent être retournées de plusieurs façons, par exemple à l’aide de la clause FOR XML avec une requête SQL SELECT ou une requête XPath.  
  
 Pour recevoir les résultats de la requête au format de flux de données plutôt que dans un **Recordset**, vous devez spécifier le **adExecuteStream** constante à partir de **ExecuteOptionEnum** en tant que paramètre de la **Execute** méthode d’un **commande** objet. Si votre fournisseur prend en charge cette fonctionnalité, les résultats sont retournés dans un flux lors de l’exécution. Il se peut que vous pouvez être amené à spécifier des propriétés supplémentaires spécifiques au fournisseur avant que le code s’exécute. Par exemple, avec le fournisseur Microsoft OLE DB pour SQL Server, propriétés, telles que **sortie Stream** dans le **propriétés** collection de la **commande** objet doit être spécifié. Pour plus d’informations sur les propriétés dynamiques spécifiques à SQL Server associé à cette fonctionnalité, consultez propriétés XML-Related dans la documentation en ligne de SQL Server.  
  
## <a name="for-xml-query-example"></a>PAR exemple de requête XML  
 L’exemple suivant est écrit en VBScript dans la base de données Northwind :  
  
```html
<!-- BeginRecordAndStreamVBS -->  
<%@ LANGUAGE = VBScript %>  
<%  Option Explicit      %>  
  
<HTML>  
<HEAD>  
<META NAME="GENERATOR" Content="Microsoft Developer Studio"/>  
<META HTTP-EQUIV="Content-Type" content="text/html"; charset="iso-8859-1">  
<TITLE>FOR XML Query Example</TITLE>  
  
<STYLE>  
   BODY  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
  
   H3  
   {  
      FONT-FAMILY: Tahoma;  
      FONT-SIZE: 8pt;  
      OVERFLOW: auto  
   }  
</STYLE>  
  
<!-- #include file="adovbs.inc" -->  
<%  
   Response.Write "<H3>Server-side processing</H3>"  
  
   Response.Write "Page Generated @ " & Now() & "<BR/>"  
  
   Dim adoConn  
   Set adoConn = Server.CreateObject("ADODB.Connection")  
  
   Dim sConn  
   sConn = "Provider=SQLOLEDB;Data Source=" & _  
      Request.ServerVariables("SERVER_NAME") & ";" & _  
      Initial Catalog=Northwind;Integrated Security=SSPI;"  
  
   Response.write "Connect String = " & sConn & "<BR/>"  
  
   adoConn.ConnectionString = sConn  
   adoConn.CursorLocation = adUseClient  
  
   adoConn.Open  
  
   Response.write "ADO Version = " & adoConn.Version & "<BR/>"  
   Response.write "adoConn.State = " & adoConn.State & "<BR/>"  
  
   Dim adoCmd  
   Set adoCmd = Server.CreateObject("ADODB.Command")  
   Set adoCmd.ActiveConnection = adoConn  
  
   Dim sQuery  
   sQuery = "<ROOT xmlns:sql='urn:schemas-microsoft-com:xml-sql'><sql:query>SELECT * FROM PRODUCTS WHERE ProductName='Gumbr Gummibrchen' FOR XML AUTO</sql:query></ROOT>"  
  
   Response.write "Query String = " & sQuery & "<BR/>"  
  
   Dim adoStreamQuery  
   Set adoStreamQuery = Server.CreateObject("ADODB.Stream")  
   adoStreamQuery.Open  
   adoStreamQuery.WriteText sQuery, adWriteChar  
   adoStreamQuery.Position = 0  
  
   adoCmd.CommandStream = adoStreamQuery  
   adoCmd.Dialect = "{5D531CB2-E6Ed-11D2-B252-00C04F681B71}"  
  
   Response.write "Pushing XML to client for processing "  & "<BR/>"  
  
   adoCmd.Properties("Output Stream") = Response  
   Response.write "<XML ID='MyDataIsle'>"  
   adoCmd.Execute , , 1024  
   Response.write "</XML>"  
  
%>  
  
<SCRIPT language="VBScript" For="window" Event="onload">  
   Dim xmlDoc  
   Set xmlDoc = MyDataIsle.XMLDocument  
   xmlDoc.resolveExternals=false  
   xmlDoc.async=false  
  
   If xmlDoc.parseError.Reason <> "" then  
      Msgbox "parseError.Reason = " & xmlDoc.parseError.Reason  
   End If  
  
   Dim root, child  
   Set root = xmlDoc.documentElement  
   For each child in root.childNodes  
      dim OutputXML  
      OutputXML = document.all("log").innerHTML  
      document.all("log").innerHTML = OutputXML & "<LI>" & child.getAttribute("ProductName") & "</LI>"  
   Next  
</SCRIPT>  
  
</HEAD>  
  
<BODY>  
  
   <H3>Client-side processing of XML Document MyDataIsle</H3>  
   <UL id=log>  
   </UL>  
  
</BODY>  
</HTML>  
<!-- EndRecordAndStreamVBS -->  
  
```  
  
 La clause FOR XML demande à SQL Server pour retourner des données sous la forme d’un document XML.  
  
### <a name="for-xml-syntax"></a>POUR la syntaxe XML  
  
```syntax
FOR XML [RAW|AUTO|EXPLICIT]  
```  
  
 POUR XML RAW génère des éléments de ligne génériques qui ont des valeurs de colonne en tant qu’attributs. FOR XML AUTO utilise l’heuristique pour générer une arborescence hiérarchique avec des noms d’éléments en fonction des noms de table. FOR XML EXPLICIT génère une table universelle avec les relations décrites en détail par les métadonnées.  
  
 Voici un exemple instruction SQL SELECT FOR XML :  
  
```sql
SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO  
```  
  
 La commande peut être spécifiée dans une chaîne, comme indiqué précédemment, attribué à **CommandText**, ou sous la forme d’une requête de modèle XML affectée à **CommandStream**. Pour plus d’informations sur les requêtes de modèle XML, consultez [commande flux](../../../ado/guide/data/command-streams.md) dans ADO ou à l’aide de flux de données pour l’entrée de commande dans la documentation en ligne de SQL Server.  
  
 En tant qu’une requête de modèle XML, la requête FOR XML se présente comme suit :  
  
```xml
<sql:query> SELECT * FROM PRODUCTS ORDER BY PRODUCTNAME FOR XML AUTO </sql:query>  
```  
  
 Cet exemple spécifie l’ASP **réponse** de l’objet pour le **sortie Stream** propriété :  
  
```vb
adoCmd.Properties("Output Stream") = Response  
```  
  
 Ensuite, spécifiez **adExecuteStream** paramètre de **Execute**. Cet exemple encapsule le flux dans les balises XML pour créer un îlot de données XML :  
  
```vb
Response.write "<XML ID=MyDataIsle>"  
adoCmd.Execute , , adExecuteStream  
Response.write "</XML>"  
```  
  
### <a name="remarks"></a>Notes  
 À ce stade, XML a été transmis au navigateur client et il est prêt à être affiché. Cela permet à l’aide de code VBScript côté client pour lier le document XML à une instance de DOM et une boucle dans chaque nœud enfant pour générer une liste de produits au format HTML.

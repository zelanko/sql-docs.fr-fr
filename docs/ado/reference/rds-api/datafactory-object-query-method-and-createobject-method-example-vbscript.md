---
title: Créer l’objet RDSServer.DataFactory à l’aide de CreateObject (VBScript) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- DataFactory object [ADO], VBScript example
- CreateObject method [ADO], VBScript example
- Query method [ADO], VBScript example
ms.assetid: b4e2844a-120a-4513-860b-f1b6e4b5dda4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 22abaf8785b1509b0e992d99e5e0f57adb6a1e00
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66707757"
---
# <a name="datafactory-object-query-method-and-createobject-method-example-vbscript"></a>DataFactory (exemple d’objet), Query (exemple de méthode) et CreateObject (exemple de méthode) (VBScript)
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Cet exemple crée un [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) à l’aide de l’objet le [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) méthode de la [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) objet. Pour tester cet exemple, coupez et collez ce code entre les \<corps > et \</corps > balises dans un HTML normal de document et nommez-le **DataFactoryVBS.asp**. Le script ASP identifie votre serveur.  
  
```  
<!-- BeginDataFactoryVBS -->  
<HTML>  
<HEAD>  
<!--use the following META tag instead of adovbs.inc-->  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
<META name="VI60_DefaultClientScript" Content="VBScript">  
  
<META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0">  
<TITLE>DataFactory Object, Query Method, and   
CreateObject Method Example (VBScript)</TITLE>  
<style>  
<!--  
body {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</HEAD>  
<BODY>  
<h1>DataFactory Object, Query Method, and   
CreateObject Method Example (VBScript)</h1>  
<H2>RDS API Code Examples</H2>  
<HR>  
<H3>Using Query Method of RDSServer.DataFactory</H3>  
  
<!-- RDS.DataSpace  ID RDS1-->  
<OBJECT ID="RDS1" WIDTH=1 HEIGHT=1  
CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36">  
</OBJECT>  
  
<!-- RDS.DataControl with parameters   
set at run time -->  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=RDS WIDTH=1 HEIGHT=1>  
</OBJECT>  
  
<TABLE DATASRC=#RDS>  
<TBODY>  
  <TR>  
    <TD><SPAN DATAFLD="FirstName"></SPAN></TD>  
    <TD><SPAN DATAFLD="LastName"></SPAN></TD>  
  </TR>  
</TBODY>      
</TABLE>  
  
<HR>  
<INPUT TYPE=BUTTON NAME="Run" VALUE="Run">  
<BR>  
<H4>Click Run -    
The <i>CreateObject</i> Method of the RDS.DataSpace Object Creates   
an instance of the RDSServer.DataFactory;   
The <i>Query</i> Method of the RDSServer.DataFactory is used  
to bring back a Recordset. </H4>  
  
<Script Language="VBScript">  
  
    Dim rdsDF  
    Dim strServer  
    Dim strCnxn  
    Dim strSQL  
  
    strServer = "https://<%=Request.ServerVariables("SERVER_NAME")%>"  
    strCnxn = "Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind';"  
    strSQL = "Select FirstName, LastName from Employees"  
  
    Sub Run_OnClick()  
  
        ' Create RDSServer.DataFactory Object  
        Dim rs  
        ' Get Recordset  
        Set DF = RDS1.CreateObject("RDSServer.DataFactory", strServer)  
        Set rs = DF.Query(strCnxn, strSQL)  
        ' Set parameters of RDS.DataControl at Run Time  
        RDS.Server = strServer  
        RDS.SQL = strSQL  
        RDS.Connect = strCnxn  
        RDS.Refresh  
  
    End Sub  
</Script>  
  
</BODY>  
</HTML>  
<!-- EndDataFactoryVBS -->  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CreateObject, méthode (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md)   
 [DataFactory, objet (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [DataSpace, objet (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)   
 [Query, méthode (RDS)](../../../ado/reference/rds-api/query-method-rds.md)



---
title: À l’aide d’un objet de connexion | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 4b34f971-5699-43e7-9b15-137d334fa66e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d7726cb0aeeade66870b1b3d175a9489a93bad09
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606169"
---
# <a name="using-a-connection-object"></a>Utilisation d’un objet Connection
Avant d’ouvrir un **connexion** de l’objet, vous devez définir certaines informations sur la source de données et le type de connexion. La plupart de ces informations est détenue par le *ConnectionString* paramètre de la [Open, méthode](../../../ado/reference/ado-api/open-method-ado-connection.md) sur le **connexion** objet, ou par le [ConnectionString propriété](../../../ado/reference/ado-api/connectionstring-property-ado.md) sur le **connexion** objet. Une chaîne de connexion se compose d’une liste de paires argument/valeur séparées par des points-virgules, avec les valeurs encadrées de guillemets simples. Exemple :  
  
```  
Dim sConn As String  
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Initial Catalog='Northwind';Integrated Security='SSPI';"  
```  
  
> [!NOTE]
>  Vous pouvez également spécifier un nom de Source de données (DSN) ODBC ou un fichier UDL (Data Link) dans une chaîne de connexion. Pour plus d’informations sur les sources de données, consultez [la gestion des Sources de données](../../../odbc/admin/managing-data-sources.md) dans la référence du programmeur ODBC. Pour plus d’informations sur l’UDL, consultez [Data Link API Overview](https://msdn.microsoft.com/95c180ea-bd4f-4dca-b95a-576afd135bbc) dans la référence du programmeur OLE DB.  
  
 En règle générale, vous établissez une connexion en appelant le **Connection.Open** méthode avec un bon un *chaîne de connexion* en tant que paramètre. Un exemple est illustré dans l’extrait de code Visual Basic suivant :  
  
```  
Dim oConn As ADODB.Connection  
Dim oRs As ADODB.Recordset  
Dim sConn As String  
Dim sSQL as String  
  
' Open a connection.  
Set oConn = New ADODB.Connection  
.Open   
  
' Make a query over the connection.  
sSQL = "SELECT ProductID, ProductName, CategoryID, UnitPrice " & _  
             "FROM Products"  
Set oRs = New ADODB.Recordset  
oRs.Open sSQL, , adOpenStatic, adLockBatchOptimistic, adCmdText  
  
MsgBox oRs.RecordCount  
  
' Close the connection.  
oConn.Close  
Set oConn = Nothing  
  
```  
  
 Ici **oRs.Open** prend un **connexion** objet (*oConn*) variable comme valeur de son *ActiveConnection* paramètre. En outre, le **Connection.CursorLocation** propriété suppose que la valeur par défaut **adUseServer**. Comparez cela au [HelloData](../../../ado/guide/data/hellodata-a-simple-ado-application.md) exemple dans la section précédente. L’instruction suivante entraînerait des erreurs d’exécution.  
  
```  
oRs.MarshalOptions = adMarshalModifiedOnly  
' Disconnect the Recordset.  
Set oRs.ActiveConnection = Nothing  
```

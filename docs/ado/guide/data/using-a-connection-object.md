---
title: Utilisation d’un objet de connexion | Microsoft Docs
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
ms.openlocfilehash: 4f1b867e1870b81641c7cea09d9a8fb3accfcc01
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923644"
---
# <a name="using-a-connection-object"></a>Utilisation d’un objet Connection
Avant d’ouvrir un objet de **connexion** , vous devez définir certaines informations sur la source de données et le type de connexion. La plupart de ces informations sont détenues par le paramètre *ConnectionString* de la [méthode Open](../../../ado/reference/ado-api/open-method-ado-connection.md) sur l’objet **Connection** , ou par la [propriété ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) de l’objet **Connection** . Une chaîne de connexion se compose d’une liste de paires argument/valeur séparées par des points-virgules, les valeurs étant placées entre guillemets simples. Par exemple :  
  
```  
Dim sConn As String  
sConn = "Provider='SQLOLEDB';Data Source='MySqlServer';" & _  
             "Initial Catalog='Northwind';Integrated Security='SSPI';"  
```  
  
> [!NOTE]
>  Vous pouvez également spécifier un nom de source de données (DSN) ODBC ou un fichier UDL (Data Link) dans une chaîne de connexion. Pour plus d’informations sur les noms de source de données, consultez [gestion des sources de données](../../../odbc/admin/managing-data-sources.md) dans le Guide de référence du programmeur ODBC. Pour plus d’informations sur UDL, consultez [vue d’ensemble](https://msdn.microsoft.com/95c180ea-bd4f-4dca-b95a-576afd135bbc) de l’API de liaison de données dans le Guide de référence du programmeur OLE DB.  
  
 En général, vous établissez une connexion en appelant la méthode **Connection. Open** avec une *chaîne de connexion* appropriée comme paramètre. Un exemple est illustré dans l’extrait de code Visual Basic suivant :  
  
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
  
 Ici **ors. Open** accepte une variable d’objet de **connexion** (*oConn*) comme valeur de son paramètre *ActiveConnection* . En outre, la propriété **Connection. CursorLocation** prend la valeur par défaut **adUseServer**. Comparez ceci à l’exemple [HelloData](../../../ado/guide/data/hellodata-a-simple-ado-application.md) dans la section précédente. L’instruction suivante entraînerait des erreurs d’exécution.  
  
```  
oRs.MarshalOptions = adMarshalModifiedOnly  
' Disconnect the Recordset.  
Set oRs.ActiveConnection = Nothing  
```

---
title: Modification des données | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO, editing data
- AdUseClient [ADO]
- editing data [ADO]
ms.assetid: ef514f85-c446-4f05-824e-c9313b2ffae1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8e8fd90849b8e046a7f4fe5d158d4594e612c91f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925491"
---
# <a name="editing-data"></a>Modification des données
Nous avons expliqué comment utiliser ADO pour se connecter à une source de données, exécuter une commande, obtenir les résultats dans un objet **Recordset** et naviguer dans le **Recordset**. Cette section se concentre sur l’opération ADO fondamentale suivante : modification des données.  
  
 Cette section continue à utiliser l’exemple **d’ensemble d’enregistrements** présenté lors de l' [examen des données](../../../ado/guide/data/examining-data.md), avec une modification importante. Le code suivant permet d’ouvrir le **jeu d’enregistrements**:  
  
```  
'BeginEditIntro  
    Dim strSQL As String  
    Dim objRs1 As ADODB.Recordset  
  
    strSQL = "SELECT * FROM Shippers"  
  
    Set objRs1 = New ADODB.Recordset  
  
    objRs1.Open strSQL, GetNewConnection, adOpenStatic, _  
                adLockBatchOptimistic, adCmdText  
  
    ' Disconnect the Recordset from the Connection object.  
    Set objRs1.ActiveConnection = Nothing  
'EndEditIntro  
```  
  
 La modification importante du code implique la définition de la propriété **CursorLocation** de l’objet de **connexion** égal à **adUseClient** dans la fonction *GetNewConnection* (illustrée dans l’exemple suivant), qui indique l’utilisation d’un curseur client. Pour plus d’informations sur les différences entre les curseurs côté client et côté serveur, consultez [Présentation des curseurs et des verrous](../../../ado/guide/data/understanding-cursors-and-locks.md).  
  
 Le paramètre **adUseClient** de la propriété **CursorLocation** déplace l’emplacement du curseur à partir de la source de données (dans ce cas, le SQL Server) vers l’emplacement du code client (la station de travail). Ce paramètre force ADO à appeler le moteur de curseur client pour OLE DB sur le client afin de créer et de gérer le curseur.  
  
 Vous avez peut-être également remarqué que le paramètre **LockType** de la méthode **Open** est passé à **adLockBatchOptimistic**. Cela ouvre le curseur en mode batch. (Le fournisseur met en cache plusieurs modifications et les écrit dans la source de données sous-jacente uniquement lorsque vous appelez la méthode **UpdateBatch** .) Les modifications apportées au **jeu d’enregistrements** ne seront pas mises à jour dans la base de données jusqu’à ce que la méthode **UpdateBatch** soit appelée.  
  
 Enfin, le code de cette section utilise une version modifiée de la fonction GetNewConnection. Cette version de la fonction retourne maintenant un curseur côté client. La fonction se présente comme suit :  
  
```  
'BeginNewConnection  
Public Function GetNewConnection() As ADODB.Connection  
    On Error GoTo ErrHandler:  
  
    Dim objConn As New ADODB.Connection  
    Dim strConnStr As String  
  
    strConnStr = "Provider='SQLOLEDB';Initial Catalog='Northwind';" & _  
                 "Data Source='MySqlServer';Integrated Security='SSPI';"  
  
    objConn.ConnectionString = strConnStr  
    objConn.CursorLocation = adUseClient  
    objConn.Open  
  
    Set GetNewConnection = objConn  
  
    Exit Function  
  
ErrHandler:  
    Set objConn = Nothing  
    Set GetNewConnection = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Function  
'EndNewConnection  
```  
  
 Cette section contient les rubriques suivantes :  
  
-   [Modification d’enregistrements existants](../../../ado/guide/data/editing-existing-records.md)  
  
-   [Ajout d’enregistrements](../../../ado/guide/data/adding-records.md)  
  
-   [Détermination de ce qui est pris en charge](../../../ado/guide/data/determining-what-is-supported.md)  
  
-   [Suppression d’enregistrements avec la méthode Delete](../../../ado/guide/data/deleting-records-using-the-delete-method.md)  
  
-   [Alternatives : utilisation d’instructions SQL](../../../ado/guide/data/alternatives-using-sql-statements.md)

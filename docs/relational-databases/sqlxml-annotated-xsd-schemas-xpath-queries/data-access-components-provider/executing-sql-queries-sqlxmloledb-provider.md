---
title: Exécution de requêtes SQL (fournisseur SQLXMLOLEDB)
description: Découvrez comment utiliser les propriétés racine ClientSideXML et XML du fournisseur SQLXMLOLEDB lors de l’exécution d’une requête SQL côté client.
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- queries [SQLXML], SQLXMLOLEDB Provider
- xml root property [SQLXML]
- SQLXMLOLEDB Provider, executing SQL queries
- SQL queries [SQLXML]
ms.assetid: 50334cf5-9c87-4c00-9beb-e08577c4fa82
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a54a5cc0612a1740be9c6884bcc65c25b16b3fa3
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97467160"
---
# <a name="executing-sql-queries-sqlxmloledb-provider"></a>Exécution de requêtes SQL (fournisseur SQLXMLOLEDB)
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]
  Cet exemple illustre l'utilisation des propriétés suivantes spécifiques au fournisseur SQLXMLOLEDB :  
  
-   ClientSideXML  
  
-   xml root  
  
 Dans cet exemple d'application ADO côté client, une requête SQL simple est exécutée sur le client. Étant donné que la propriété ClientSideXML a la valeur true, l’instruction SELECT sans la clause FOR XML est envoyée au serveur. Le serveur exécute la requête et retourne un ensemble de lignes au client. Le client applique ensuite la transformation FOR XML à l'ensemble de lignes et génère un document XML.  
  
 La propriété racine XML fournit l’élément racine de niveau supérieur unique pour le document XML généré.  
  
> [!NOTE]  
>  Dans le code, vous devez fournir le nom de l'instance de Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans la chaîne de connexion. En outre, cet exemple spécifie l'utilisation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client (SQLNCLI11) comme fournisseur de données, ce qui requiert l'installation d'un logiciel client réseau supplémentaire. Pour plus d’informations, consultez [Configuration système requise pour SQL Server Native Client](../../../relational-databases/native-client/system-requirements-for-sql-server-native-client.md).  
  
```  
Option Explicit  
Sub main()  
Dim oTestStream As New ADODB.Stream  
Dim oTestConnection As New ADODB.Connection  
Dim oTestCommand As New ADODB.Command  
  
oTestConnection.Open "provider=SQLXMLOLEDB.4.0;data provider=SQLNCLI11;data source=SqlServerName;initial catalog=AdventureWorks;Integrated Security=SSPI ;"  
oTestCommand.ActiveConnection = oTestConnection  
oTestCommand.Properties("ClientSideXML") = True  
oTestCommand.CommandText = "SELECT TOP 10 FirstName, LastName FROM Person.Contact FOR XML AUTO"  
oTestStream.Open  
oTestCommand.Properties("Output Stream").Value = oTestStream  
oTestCommand.Properties("xml root") = "root"  
oTestCommand.Execute , , adExecuteStream  
  
oTestStream.Position = 0  
oTestStream.Charset = "utf-8"  
Debug.Print oTestStream.ReadText(adReadAll)  
End Sub  
Sub Form_Load()  
 main  
End Sub  
```  
  
  

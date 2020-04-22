---
title: Utilisation d’ADO avec OLE DB Driver
description: Découvrez comment utiliser ADO avec le pilote OLE DB, y compris les nouvelles fonctionnalités comme les jeux MARS (Multiple Active Result Set), les notifications de requête, les types définis par l’utilisateur ou le type de données XML.
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, ADO
- data access [OLE DB Driver for SQL Server], ADO
- ADO [OLE DB Driver for SQL Server]
- MSOLEDBSQL, ADO
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 72d82433e04ead61ec71eecd3c8771cbe744b751
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81633889"
---
# <a name="using-ado-with-ole-db-driver-for-sql-server"></a>Utilisation d’ADO avec OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Pour tirer parti des nouvelles fonctionnalités introduites dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], telles que MARS (Multiple Active Result Sets), les notifications de requête, les types définis par l’utilisateur (UDT) ou le nouveau type de données **xml**, les applications existantes qui utilisent ADO (ActiveX Data Objects) doivent utiliser OLE DB Driver pour SQL Server comme fournisseur d’accès aux données.  
  
 Pour permettre à ADO d’utiliser les nouvelles fonctionnalités des récentes versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], certaines améliorations ont été apportées à OLE DB Driver pour SQL Server afin d’étendre les fonctionnalités principales d’OLE DB. Ces améliorations permettent aux applications ADO d’utiliser les fonctionnalités [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les plus récentes et de consommer deux types de données introduits dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] : **xml** et **udt**. Ces améliorations exploitent également des optimisations apportées aux types de données **varchar**, **nvarchar** et **varbinary**. OLE DB Driver pour SQL Server ajoute la propriété d’initialisation SSPROP_INIT_DATATYPECOMPATIBILITY au jeu de propriétés DBPROPSET_SQLSERVERDBINIT pour une utilisation par les applications ADO afin que les nouveaux types de données soient exposés d’une manière compatible avec ADO. De plus, OLE DB Driver pour SQL Server définit un nouveau mot clé de chaîne de connexion nommé **DataTypeCompatibility**, qui est défini dans la chaîne de connexion.  

> [!NOTE]  
>  Les applications ADO existantes peuvent accéder et mettre à jour des valeurs de champ binaire et texte XML, UDT et de grande valeur à l'aide du fournisseur SQLOLEDB. Les nouveaux types de données plus grands **varchar(max)** , **nvarchar(max)** et **varbinary(max)** sont retournés respectivement en tant que types ADO **adLongVarChar**, **adLongVarWChar** et **adLongVarBinary**. Les colonnes XML sont retournées comme **adLongVarChar** et les colonnes UDT sont retournées comme **adVarBinary**. Toutefois, si vous utilisez OLE DB Driver pour SQL Server (MSOLEDBSQL) au lieu de SQLOLEDB, vous devez vous assurer d'affecter la valeur « 80 » au mot clé **DataTypeCompatibility** afin que les nouveaux types de données mappent correctement aux types de données ADO.  

## <a name="enabling-ole-db-driver-for-sql-server-from-ado"></a>Activation d’OLE DB Driver pour SQL Server depuis ADO  
 Pour activer l’utilisation d’OLE DB Driver pour SQL Server, les applications ADO doivent implémenter les mots clés suivants dans leurs chaînes de connexion :  

-   `Provider=MSOLEDBSQL`  

-   `DataTypeCompatibility=80`  

 Pour plus d’informations sur les mots clés de chaîne de connexion ADO pris en charge dans le pilote OLE DB pour SQL Server, voir [Utiliser des mots clés de chaîne de connexion avec le pilote OLE DB pour SQL Server](using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  

 Voici un exemple d’établissement d’une chaîne de connexion ADO entièrement compatible avec OLE DB Driver pour SQL Server, dont l’activation de la fonctionnalité MARS :  

```  
Dim con As New ADODB.Connection  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
```  

## <a name="examples"></a>Exemples  
 Les sections suivantes fournissent des exemples illustrant la manière dont vous pouvez utiliser ADO avec OLE DB Driver pour SQL Server.  

### <a name="retrieving-xml-column-data"></a>Extraction de données de colonnes XML  
 Dans cet exemple, un recordset est utilisé pour récupérer et afficher les données d’une colonne XML dans l’exemple de base de données **AdventureWorks** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  

```  
Dim con As New ADODB.Connection  
Dim rst As New ADODB.Recordset  
Dim sXMLResult As String  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _   
         & "DataTypeCompatibility=80;"  

con.Open  

' Get the xml data as a recordset.  
Set rst.ActiveConnection = con  
rst.Source = "SELECT AdditionalContactInfo FROM Person.Contact " _  
   & "WHERE AdditionalContactInfo IS NOT NULL"  
rst.Open  

' Display the data in the recordset.  
While (Not rst.EOF)  
   sXMLResult = rst.Fields("AdditionalContactInfo").Value  
   Debug.Print (sXMLResult)  
   rst.MoveNext  
End While  

con.Close  
Set con = Nothing  
```  

> [!NOTE]  
>  Le filtrage de jeu d'enregistrements n'est pas pris en charge avec les colonnes XML. S'il est utilisé, une erreur est retournée.  

### <a name="retrieving-udt-column-data"></a>Extraction de données de colonnes UDT  
 Dans cet exemple, un objet **Command** est utilisé pour exécuter une requête SQL qui retourne un type défini par l’utilisateur (UDT), les données UDT sont mises à jour, puis les nouvelles données sont réinsérées dans la base de données. Cet exemple suppose que le type défini par l’utilisateur **Point** a déjà été inscrit dans la base de données.  

```  
Dim con As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
Dim strOldUDT As String  
Dim strNewUDT As String  
Dim aryTempUDT() As String  
Dim strTempID As String  
Dim i As Integer  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;"  

con.Open  

' Get the UDT value.  
Set cmd.ActiveConnection = con  
cmd.CommandText = "SELECT ID, Pnt FROM dbo.Points.ToString()"  
Set rst = cmd.Execute  
strTempID = rst.Fields(0).Value  
strOldUDT = rst.Fields(1).Value  

' Do something with the UDT by adding i to each point.  
arytempUDT = Split(strOldUDT, ",")  
i = 3  
strNewUDT = LTrim(Str(Int(aryTempUDT(0)) + i)) + "," + _  
   LTrim(Str(Int(aryTempUDT(1)) + i))  

' Insert the new value back into the database.  
cmd.CommandText = "UPDATE dbo.Points SET Pnt = '" + strNewUDT + _  
   "' WHERE ID = '" + strTempID + "'"  
cmd.Execute  

con.Close  
Set con = Nothing  
```  

### <a name="enabling-and-using-mars"></a>Activation et utilisation de MARS  
 Dans cet exemple, la chaîne de connexion est construite de façon à activer MARS par le biais d’OLE DB Driver pour SQL Server, puis deux objets recordset sont créés pour une exécution avec la même connexion.  

```  
Dim con As New ADODB.Connection  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  

Dim recordset1 As New ADODB.Recordset  
Dim recordset2 As New ADODB.Recordset  

Dim recordsaffected As Integer  
Set recordset1 =  con.Execute("SELECT * FROM Table1", recordsaffected, adCmdText)  
Set recordset2 =  con.Execute("SELECT * FROM Table2", recordsaffected, adCmdText)  

con.Close  
Set con = Nothing  
```  

 Dans les versions antérieures du fournisseur OLE DB, ce code provoquait la création d'une connexion implicite lors de la deuxième exécution car un seul jeu de résultats actif par connexion pouvait être ouvert. La connexion implicite n'étant pas mise dans le pool de connexions OLE DB, cela provoquait une charge supplémentaire. Avec la fonctionnalité MARS exposée par OLE DB Driver pour SQL Server, vous obtenez des résultats actifs multiples sur une connexion unique.  

## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec OLE DB Driver pour SQL Server](building-applications-with-oledb-driver-for-sql-server.md)  

---
title: Utilisation d’ADO avec SQL Server Native Client (fr) Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, ADO
- data access [SQL Server Native Client], ADO
- ADO [SQL Server Native Client]
- SQLNCLI, ADO
ms.assetid: 118a7cac-4c0d-44fd-b63e-3d542932d239
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 81f7ff71643776eb3116dab0157a4f2cd32b788a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302462"
---
# <a name="using-ado-with-sql-server-native-client"></a>Utilisation d'ADO avec SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Afin de tirer parti des [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] nouvelles fonctionnalités introduites dans des ensembles de résultats actifs multiples (MARS), des notifications de requête, des types définis par l’utilisateur (UDT) ou le nouveau type de données **xml,** les applications existantes qui utilisent ActiveX Data Objects (ADO) devraient utiliser le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur de DB OLE du client autochtone comme fournisseur d’accès aux données.  
  
 Si vous n'avez pas besoin d'utiliser ces nouvelles fonctionnalités introduites dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], il n'est pas nécessaire d'utiliser le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ; vous pouvez continuer à utiliser votre fournisseur d'accès aux données actuel, qui est en général SQLOLEDB. Si vous améliorez une application existante et que vous devez utiliser les nouvelles fonctionnalités introduites dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], vous devez utiliser le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
> [!NOTE]  
>  Si vous développez une nouvelle application, il est recommandé d'envisager l'utilisation d'ADO.NET et du fournisseur de données .NET Framework pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] au lieu de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client afin d'accéder à toutes les nouvelles fonctionnalités des versions récentes de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour plus d'informations sur le fournisseur de données .NET Framework pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consultez la documentation du kit de développement logiciel SDK .NET Framework pour ADO.NET.  
  
 Pour permettre à ADO d'utiliser les nouvelles fonctionnalités des récentes versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], certaines améliorations ont été apportées au fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client afin d'étendre les fonctionnalités principales d'OLE DB. Ces améliorations permettent aux applications ADO d’utiliser les fonctionnalités [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les plus récentes et de consommer deux types de données introduits dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] : **xml** et **udt**. Ces améliorations exploitent également des optimisations apportées aux types de données **varchar**, **nvarchar** et **varbinary**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ajoute la propriété SSPROP_INIT_DATATYPECOMPATIBILITY de initialisation à la propriété DBPROPSET_SQLSERVERDBINIT destinée aux applications ADO afin que les nouveaux types de données soient exposés d’une manière compatible avec ADO. De plus, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le fournisseur native OLE DB définit également un nouveau mot clé de connexion nommé **DataTypeCompatibility** qui est défini dans la chaîne de connexion.  
  
> [!NOTE]  
>  Les applications ADO existantes peuvent accéder et mettre à jour des valeurs de champ binaire et texte XML, UDT et de grande valeur à l'aide du fournisseur SQLOLEDB. Les nouveaux types de données plus grands **varchar(max)**, **nvarchar(max)** et **varbinary(max)** sont retournés respectivement en tant que types ADO **adLongVarChar**, **adLongVarWChar** et **adLongVarBinary**. Les colonnes XML sont retournées comme **adLongVarChar** et les colonnes UDT sont retournées comme **adVarBinary**. Toutefois, si vous [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] utilisez le fournisseur de DB OLE De client autochtone (SQLNCLI11) au lieu de SQLOLEDB, vous devez vous assurer de définir le mot clé **DataTypeCompatibility** à « 80 » afin que les nouveaux types de données soient cartographiés correctement aux types de données ADO.  
  
## <a name="enabling-sql-server-native-client-from-ado"></a>Activation de SQL Server Native Client à partir d'ADO  
 Pour permettre l’utilisation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, les applications ADO devront implémenter les mots clés suivants dans leurs chaînes de connexion :  
  
-   `Provider=SQLNCLI11`  
  
-   `DataTypeCompatibility=80`  
  
 Pour plus d’informations sur les mots [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] clés de chaîne de connexions ADO pris en charge dans Native Client, voir [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Voici un exemple d’établissement d’une chaîne de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ADO entièrement activée pour travailler avec Native Client, y compris l’activation de la fonction MARS :  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
```  
  
## <a name="examples"></a>Exemples  
 Les sections suivantes fournissent des exemples de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] la façon dont vous pouvez utiliser ADO avec le fournisseur de DB OLE de client autochtone.  
  
### <a name="retrieving-xml-column-data"></a>Extraction de données de colonnes XML  
 Dans cet exemple, un recordset est utilisé pour récupérer et afficher les données d’une colonne XML dans l’exemple de base de données  **AdventureWorks**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
```  
Dim con As New ADODB.Connection  
Dim rst As New ADODB.Recordset  
Dim sXMLResult As String  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
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
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
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
 Dans cet exemple, la chaîne de connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est construite pour activer MARS par l’intermédiaire du fournisseur native OLE DB, puis deux objets de type d’enregistrement sont créés pour exécuter en utilisant la même connexion.  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
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
  
 Dans les versions antérieures du fournisseur OLE DB, ce code provoquait la création d'une connexion implicite lors de la deuxième exécution car un seul jeu de résultats actif par connexion pouvait être ouvert. La connexion implicite n'étant pas mise dans le pool de connexions OLE DB, cela provoquait une charge supplémentaire. Avec la fonction MARS [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] exposée par le fournisseur native Client OLE DB, vous obtenez plusieurs résultats actifs sur la seule connexion.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d'applications avec SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  

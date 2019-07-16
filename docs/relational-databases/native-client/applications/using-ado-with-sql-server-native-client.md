---
title: Utilisation d’ADO avec SQL Server Native Client | Microsoft Docs
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3e52ecc471255db772fddc46585f635fbc6cb182
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67987553"
---
# <a name="using-ado-with-sql-server-native-client"></a>Utilisation d'ADO avec SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  Pour tirer parti des nouvelles fonctionnalités introduites dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] tels que des jeux de résultats actifs multiples (MARS), les notifications de requête, les types définis par l’utilisateur (UDT) ou au nouveau **xml** type de données, les applications existantes qui utilisent les contrôles ActiveX Data Objects (ADO) doit utiliser le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client en tant que leur fournisseur d’accès aux données.  
  
 Si vous n'avez pas besoin d'utiliser ces nouvelles fonctionnalités introduites dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], il n'est pas nécessaire d'utiliser le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ; vous pouvez continuer à utiliser votre fournisseur d'accès aux données actuel, qui est en général SQLOLEDB. Si vous améliorez une application existante et que vous devez utiliser les nouvelles fonctionnalités introduites dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], vous devez utiliser le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
> [!NOTE]  
>  Si vous développez une nouvelle application, il est recommandé d'envisager l'utilisation d'ADO.NET et du fournisseur de données .NET Framework pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] au lieu de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client afin d'accéder à toutes les nouvelles fonctionnalités des versions récentes de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour plus d'informations sur le fournisseur de données .NET Framework pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consultez la documentation du kit de développement logiciel SDK .NET Framework pour ADO.NET.  
  
 Pour permettre à ADO d'utiliser les nouvelles fonctionnalités des récentes versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], certaines améliorations ont été apportées au fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client afin d'étendre les fonctionnalités principales d'OLE DB. Ces améliorations permettent aux applications ADO d’utiliser les fonctionnalités [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les plus récentes et de consommer deux types de données introduits dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] : **xml** et **udt**. Ces améliorations exploitent également des optimisations apportées aux types de données **varchar**, **nvarchar** et **varbinary**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ajoute la propriété d’initialisation SSPROP_INIT_DATATYPECOMPATIBILITY à la propriété DBPROPSET_SQLSERVERDBINIT définie pour une utilisation par les applications ADO afin que les nouveaux types de données soient exposés d’une manière compatible avec ADO. En outre, le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client définit également un mot-clé de chaîne de connexion nommé **DataTypeCompatibility** qui est définie dans la chaîne de connexion.  
  
> [!NOTE]  
>  Les applications ADO existantes peuvent accéder et mettre à jour des valeurs de champ binaire et texte XML, UDT et de grande valeur à l'aide du fournisseur SQLOLEDB. Les nouveaux types de données plus grands **varchar(max)** , **nvarchar(max)** et **varbinary(max)** sont retournés respectivement en tant que types ADO **adLongVarChar**, **adLongVarWChar** et **adLongVarBinary**. Les colonnes XML sont retournées comme **adLongVarChar** et les colonnes UDT sont retournées comme **adVarBinary**. Toutefois, si vous utilisez le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le fournisseur OLE DB Native Client (SQLNCLI11) au lieu de SQLOLEDB, vous devez vous assurer d’affecter le **DataTypeCompatibility** mot clé « 80 » afin que les nouveaux types de données mappent correctement aux données ADO types.  
  
## <a name="enabling-sql-server-native-client-from-ado"></a>Activation de SQL Server Native Client à partir d'ADO  
 Pour activer l’utilisation de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, les applications ADO doivent implémenter les mots clés suivants dans leurs chaînes de connexion :  
  
-   `Provider=SQLNCLI11`  
  
-   `DataTypeCompatibility=80`  
  
 Pour plus d’informations sur le ADO de chaîne de connexion mots clés pris en charge dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, consultez [Using Connection String Keywords with SQL Server Native Client](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Voici un exemple d’établissement d’une chaîne de connexion ADO est entièrement compatible avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, y compris l’activation de la fonctionnalité MARS :  
  
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
 Les sections suivantes fournissent des exemples d’utilisation d’ADO avec le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif.  
  
### <a name="retrieving-xml-column-data"></a>Extraction de données de colonnes XML  
 Dans cet exemple, un recordset est utilisé pour récupérer et afficher les données d’une colonne XML dans l’exemple de base de données **AdventureWorks** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
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
 Dans cet exemple, la chaîne de connexion est construite pour activer MARS par le biais du [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif et puis deux objets recordset sont créés pour l’exécuter à l’aide de la même connexion.  
  
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
  
 Dans les versions antérieures du fournisseur OLE DB, ce code provoquait la création d'une connexion implicite lors de la deuxième exécution car un seul jeu de résultats actif par connexion pouvait être ouvert. La connexion implicite n'étant pas mise dans le pool de connexions OLE DB, cela provoquait une charge supplémentaire. Avec la fonctionnalité MARS exposée par le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client, vous obtenez des résultats actifs multiples sur une connexion unique.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  

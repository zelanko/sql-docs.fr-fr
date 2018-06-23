---
title: Utiliser des données XML dans les applications | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameters [XML in SQL Server]
- XML [SQL Server], ADO
- columns [XML in SQL Server], ADO.NET
- ADO [XML in SQL Server]
- columns [XML in SQL Server], SQL Server Native Client
- xml data type [SQL Server], ADO
- SQLNCLI, XML
- xml data type [SQL Server], SQL Server Native Client
- SQL Server Native Client, XML
- ADO.NET [XML in SQL Server]
- XML [SQL Server], ADO.NET
- columns [XML in SQL Server], ADO
- xml data type [SQL Server], ADO.NET
- XML [SQL Server], SQL Server Native Client
ms.assetid: 5dabf7e0-c6df-451d-a070-4661f84607fd
caps.latest.revision: 26
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: c4dbf8007297478af88784b183089db9d4774c7e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140767"
---
# <a name="use-xml-data-in-applications"></a>Utiliser des données XML dans les applications
  Cette rubrique décrit les options qui sont disponibles pour l’utilisation de la `xml` type de données dans votre application. Cette rubrique inclut des informations sur les thèmes suivants :  
  
-   Gestion de XML à partir d'une colonne de type `xml` à l'aide d'ADO et de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  
  
-   Gestion de XML à partir d’un `xml` colonne de type à l’aide d’ADO.NET  
  
-   Gestion du type `xml` dans les paramètres à l'aide d'ADO.NET  
  
## <a name="handling-xml-from-an-xml-type-column-by-using-ado-and-sql-server-native-client"></a>Gestion de XML à partir d'une colonne de type XML à l'aide d'ADO et de SQL Server Native Client  
 Pour utiliser des composants MDAC pour accéder aux types et aux fonctionnalités introduits dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], vous devez définir la propriété d’initialisation DataTypeCompatibility dans la chaîne de connexion ADO.  
  
 Par exemple, l’exemple Visual Basic Scripting Edition (VBScript) suivant montre les résultats de l’interrogation une `xml` colonne de type `Demographics`, dans le `Sales.Store` table de la `AdventureWorks2012` base de données exemple. La requête recherche plus particulièrement la valeur de l'instance de cette colonne pour la ligne dans laquelle `CustomerID` est égal à `3`.  
  
```  
Const DS = "MyServer"  
Const DB = "AdventureWorks2012"  
  
Set objConn = CreateObject("ADODB.Connection")  
Set objRs = CreateObject("ADODB.Recordset")  
  
CommandText = "SELECT Demographics" & _  
              " FROM Sales.Store" & _  
              " INNER JOIN Sales.Customer" & _  
              " ON Sales.Store.BusinessEntityID = sales.customer.StoreID" & _  
              " WHERE Sales.Customer.CustomerID = 3" & _  
              " OR Sales.Customer.CustomerID = 4"  
  
ConnectionString = "Provider=SQLNCLI11" & _  
                   ";Data Source=" & DS & _  
                   ";Initial Catalog=" & DB & _  
                   ";Integrated Security=SSPI;" & _  
                   "DataTypeCompatibility=80"  
  
'Connect to the data source.  
objConn.Open ConnectionString  
  
'Execute command through the connection and display  
Set objRs = objConn.Execute(CommandText)  
  
Dim rowcount  
rowcount = 0  
Do While Not objRs.EOF  
   rowcount = rowcount + 1  
   MsgBox "Row " & rowcount & _  
           vbCrLf & vbCrLf & objRs(0)  
   objRs.MoveNext  
Loop  
  
'Clean up.  
objRs.Close  
objConn.Close  
Set objRs = Nothing  
Set objConn = Nothing  
```  
  
 Cet exemple montre comment définir la propriété de compatibilité du type de données. Par défaut, elle a la valeur 0 lorsque vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Si vous affectez la valeur 80, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur Native Client fera `xml` et les colonnes de type défini par l’utilisateur apparaissent comme [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] des types de données. Il s'agit respectivement de BTYPE_WSTR et de DBTYPE_BYTES.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client doit également être installé sur l'ordinateur client et la chaîne de connexion doit le désigner comme fournisseur de données avec «`Provider=SQLNCLI11;...`».  
  
#### <a name="to-test-this-example"></a>Pour tester cet exemple  
  
1.  Vérifiez que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est installé et que MDAC version 2.6.0 ou ultérieure est disponible sur l'ordinateur client.  
  
     Pour plus d’informations, consultez [Programmation de SQL Server Native Client](../native-client/sql-server-native-client-programming.md).  
  
2.  Vérifiez que l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé.  
  
     Cet exemple requiert l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
3.  Copiez le code préalablement présenté dans cette rubrique et collez-le dans votre éditeur de texte ou de code. Enregistrez le fichier sous HandlingXmlDataType.vbs.  
  
4.  Modifiez le script comme le requiert votre installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et enregistrez vos modifications.  
  
     Par exemple, à l'endroit où `MyServer` est spécifié, vous devez le remplacer par `(local)` ou par le nom réel du serveur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est installé.  
  
5.  Exécutez HandlingXmlDataType.vbs et exécutez le script.  
  
 Les résultats doivent être semblables à l'exemple suivant :  
  
```  
Row 1  
  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>1500000</AnnualSales>  
  <AnnualRevenue>150000</AnnualRevenue>  
  <BankName>Primary International</BankName>  
  <BusinessType>OS</BusinessType>  
  <YearOpened>1974</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>38000</SquareFeet>  
  <Brands>3</Brands>  
  <Internet>DSL</Internet>  
  <NumberEmployees>40</NumberEmployees>  
</StoreSurvey>  
  
Row 2  
  
<StoreSurvey xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/StoreSurvey">  
  <AnnualSales>300000</AnnualSales>  
  <AnnualRevenue>30000</AnnualRevenue>  
  <BankName>United Security</BankName>  
  <BusinessType>BM</BusinessType>  
  <YearOpened>1976</YearOpened>  
  <Specialty>Road</Specialty>  
  <SquareFeet>6000</SquareFeet>  
  <Brands>2</Brands>  
  <Internet>DSL</Internet>  
  <NumberEmployees>5</NumberEmployees>  
</StoreSurvey>  
```  
  
## <a name="handling-xml-from-an-xml-type-column-by-using-adonet"></a>Gestion de XML à partir d'une colonne de type XML à l'aide d'ADO.NET  
 Pour gérer XML à partir d’un `xml` colonne de type de données à l’aide d’ADO.NET et la [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] vous pouvez utiliser le comportement standard de la `SqlCommand` classe. Par exemple, un `xml` données colonne de type et ses valeurs peuvent être récupérées comme toute colonne SQL est récupéré à l’aide un `SqlDataReader`. Toutefois, si vous souhaitez utiliser le contenu d’un `xml` colonne de type de données au format XML, vous devez d’abord affecter le contenu à un `XmlReader` type.  
  
 Pour plus d'informations et d'exemples de code, consultez la rubrique relative aux valeurs de colonne XML dans un lecteur de données dans la documentation du Kit de développement logiciel de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] .  
  
## <a name="handling-an-xml-type-column-in-parameters-by-using-adonet"></a>Gestion d'une colonne de type XML dans les paramètres à l'aide d'ADO.NET  
 Pour gérer un type de données XML passé en tant que paramètre dans ADO.NET et le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], vous pouvez fournir la valeur sous la forme d'une instance du type de données `SqlXml`. Aucune gestion spéciale n’est requise, car `xml` dans les colonnes de type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut accepter des valeurs de paramètre de la même façon que d’autres colonnes et les types de données, tels que `string` ou `integer`.  
  
 Pour plus d'informations et d'exemples de code, consultez la rubrique relative aux valeurs XML en tant que paramètres de commande dans la documentation du Kit de développement logiciel de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnlong](../../includes/dnprdnlong-md.md)] .  
  
## <a name="see-also"></a>Voir aussi  
 [Données XML &#40;SQL Server&#41;](xml-data-sql-server.md)  
  
  
---
title: Vue d’ensemble d’attributs personnalisés de l’intégration de CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- custom attributes [CLR integration]
- attributes [CLR integration]
- common language runtime [SQL Server], attributes
- database objects [CLR integration], custom attributes
- building database objects [CLR integration], custom attributes
ms.assetid: ecf5c097-0972-48e2-a9c0-b695b7dd2820
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8df7881dd5f38935628cb6653d57763a8846e60f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62781104"
---
# <a name="overview-of-clr-integration-custom-attributes"></a>Vue d'ensemble des attributs personnalisés de l'intégration du CLR
  Le CLR (Common Language Runtime) du [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] autorise l'utilisation de mots clés descriptifs, appelés attributs. Ces attributs fournissent des informations supplémentaires sur de nombreux éléments, comme les méthodes et les classes. Ils sont enregistrés dans l'assembly avec les métadonnées de l'objet et peuvent être utilisés pour décrire votre code à d'autres outils de développement ou pour affecter le comportement au moment de l'exécution au sein de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Lorsque vous enregistrez une routine CLR avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ce dernier dérive un jeu de propriétés relatives à la routine. Ces propriétés déterminent les fonctionnalités de la routine, notamment sa capacité d'indexation. Par exemple, l'affectation de la valeur `DataAccess` à la propriété `DataAccessKind.Read` vous permet d'accéder aux données des tables utilisateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] au sein d'une fonction CLR. L’exemple suivant illustre un cas simple dans lequel le `DataAccess` propriété est définie pour faciliter l’accès aux données à partir d’une table utilisateur **table1**.  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
  
public partial class UserDefinedFunctions  
{  
    [SqlFunction(DataAccess = DataAccessKind.Read)]  
    public static string func1()  
    {  
        // Open a connection and create a command  
        SqlConnection conn = new SqlConnection("context connection = true");  
        conn.Open();  
        SqlCommand cmd = conn.CreateCommand();  
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10";  
        // where table1 is a user table  
        // Execute this command   
        SqlDataReader rd = cmd.ExecuteReader();  
        // Set string ret_val to str_val returned from the query  
        string ret_val = rd.GetValue(0).ToString();  
        rd.Close();  
        return ret_val;  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Public partial Class UserDefinedFunctions  
    <SqlFunction(DataAccess = DataAccessKind.Read)> _   
    Public Shared Function func1() As String  
        ' Open a connection and create a command  
        Dim conn As SqlConnection = New SqlConnection("context connection = true")   
        conn.Open()  
        Dim cmd As SqlCommand =  conn.CreateCommand()   
        cmd.CommandText = "SELECT str_val FROM table1 WHERE int_val = 10"  
        ' where table1 is a user table  
        ' Execute this command   
        Dim rd As SqlDataReader =  cmd.ExecuteReader()   
        ' Set string ret_val to str_val returned from the query  
        Dim ret_val As String =  rd.GetValue(0).ToString()   
        rd.Close()  
        Return ret_val  
    End Function  
End Class  
```  
  
 Pour les routines [!INCLUDE[tsql](../../includes/tsql-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dérive directement leurs propriétés de leur définition. Pour les routines CLR, le serveur n'analyse pas le corps de la routine pour dériver ces propriétés. À la place, vous pouvez utiliser des attributs personnalisés pour les classes et les membres des classes implémentés dans un langage du [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
 Les attributs personnalisés nécessaires pour les routines CLR, les types définis par l'utilisateur et les agrégats sont définis dans l'espace de noms `Microsoft.SqlServer.Server`.  
  
## <a name="see-also"></a>Voir aussi  
 [Attributs personnalisés pour les routines CLR](../../relational-databases/clr-integration/database-objects/clr-integration-custom-attributes-for-clr-routines.md)  
  
  

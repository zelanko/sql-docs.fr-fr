---
title: Création, modification et suppression de fonctions définies par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- user-defined functions [SMO]
ms.assetid: 0ebebd3b-0775-41c2-989d-aa4cf81af12a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: edde17b3339a6a78f81ddf92da95afb2f8ba851c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "72782347"
---
# <a name="creating-altering-and-removing-user-defined-functions"></a>Création, modification et suppression de fonctions définies par l'utilisateur
  L' <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> objet fournit des fonctionnalités qui permettent aux utilisateurs de gérer par programme des fonctions définies [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]par l’utilisateur dans. Les fonctions définies par l'utilisateur prennent en charge les paramètres d'entrée et de sortie, ainsi que les références directes aux colonnes de table.  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] requiert l'enregistrement d'assemblys dans une base de données pour que ceux-ci puissent être utilisés dans des procédures stockées, des fonctions définies par l'utilisateur, des déclencheurs et des types de données définis par l'utilisateur. SMO prend en charge cette fonctionnalité avec l'objet <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly>.  
  
 L'objet <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> référence l'assembly .NET avec les propriétés <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.AssemblyName%2A>, <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.ClassName%2A> et <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction.MethodName%2A>.  
  
 Lorsque l'objet <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction> référence un assembly .NET, vous devez enregistrer l'assembly en créant un objet <xref:Microsoft.SqlServer.Management.Smo.SqlAssembly> et en l'ajoutant à l'objet <xref:Microsoft.SqlServer.Management.Smo.SqlAssemblyCollection>, qui fait partie de l'objet <xref:Microsoft.SqlServer.Management.Smo.Database>.  
  
## <a name="example"></a>Exemple  
 Pour utiliser un exemple de code qui est fourni, vous devrez choisir l'environnement de programmation, le modèle de programmation et le langage de programmation dans lequel créer votre application. Pour plus d’informations, consultez [créer un projet Visual Basic Smo dans Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) ou [créer un projet Visual C&#35; Smo dans Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-basic"></a>Création d'une fonction scalaire définie par l'utilisateur en Visual Basic  
 Cet exemple de code montre comment créer et supprimer une fonction scalaire définie par l'utilisateur qui a un paramètre d'objet <xref:System.DateTime> en entrée et un type de retour entier en [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]. La fonction définie par l'utilisateur est créée dans la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . L'exemple crée une fonction définie par l'utilisateur, ISOweek, qui accepte un argument de date et calcule le numéro de semaine ISO. Pour que ce calcul puisse être correctement réalisé, la valeur 1 doit être affectée à l'option de base de données DATEFIRST avant l'appel de la fonction.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBUserDefFuncs1](SMO How to#SMO_VBUserDefFuncs1)]  -->  
  
## <a name="creating-a-scalar-user-defined-function-in-visual-c"></a>Création d'une fonction scalaire définie par l'utilisateur en Visual C#  
 Cet exemple de code montre comment créer et supprimer une fonction scalaire définie par l'utilisateur qui a un paramètre d'objet <xref:System.DateTime> en entrée et un type de retour entier en [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]. La fonction définie par l'utilisateur est créée dans la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . L'exemple crée la fonction définie par l'utilisateur. `ISOweek`. Cette fonction prend un argument date et calcule le numéro de semaine ISO. Pour que ce calcul puisse être correctement réalisé, la valeur `DATEFIRST` doit être affectée à l'option de base de données `1` avant l'appel de la fonction.  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
           Server srv = new Server();  
            //Reference the AdventureWorks2012 database.   
           Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a UserDefinedFunction object variable by supplying the parent database and the name arguments in the constructor.   
            UserDefinedFunction udf = new UserDefinedFunction(db, "IsOWeek");  
  
            //Set the TextMode property to false and then set the other properties.   
            udf.TextMode = false;  
            udf.DataType = DataType.Int;  
            udf.ExecutionContext = ExecutionContext.Caller;  
            udf.FunctionType = UserDefinedFunctionType.Scalar;  
            udf.ImplementationType = ImplementationType.TransactSql;  
  
            //Add a parameter.   
  
     UserDefinedFunctionParameter par = new UserDefinedFunctionParameter(udf, "@DATE", DataType.DateTime);  
            udf.Parameters.Add(par);  
  
            //Set the TextBody property to define the user-defined function.   
            udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;";  
  
            //Create the user-defined function on the instance of SQL Server.   
            udf.Create();  
  
            //Remove the user-defined function.   
            udf.Drop();  
        }  
```  
  
## <a name="creating-a-scalar-user-defined-function-in-powershell"></a>Création d'une fonction scalaire définie par l'utilisateur dans PowerShell  
 Cet exemple de code montre comment créer et supprimer une fonction scalaire définie par l'utilisateur qui a un paramètre d'objet <xref:System.DateTime> en entrée et un type de retour entier en [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]. La fonction définie par l'utilisateur est créée dans la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] . L'exemple crée la fonction définie par l'utilisateur. `ISOweek`. Cette fonction prend un argument date et calcule le numéro de semaine ISO. Pour que ce calcul puisse être correctement réalisé, la valeur `DATEFIRST` doit être affectée à l'option de base de données `1` avant l'appel de la fonction.  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a user defined function object variable by supplying the parent database and name arguments in the constructor.
$udf  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunction -argumentlist $db, "IsOWeek"  
  
# Set the TextMode property to false and then set the other properties.
$udf.TextMode = $false  
$udf.DataType = [Microsoft.SqlServer.Management.SMO.DataType]::Int
$udf.ExecutionContext = [Microsoft.SqlServer.Management.SMO.ExecutionContext]::Caller  
$udf.FunctionType = [Microsoft.SqlServer.Management.SMO.UserDefinedFunctionType]::Scalar  
$udf.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Define a Parameter object variable by supplying the parent function, name and type arguments in the constructor.  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::DateTime  
$par  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.UserDefinedFunctionParameter -argumentlist $udf, "@DATE",$type  
  
# Add the parameter to the function  
$udf.Parameters.Add($par)  
  
#Set the TextBody property to define the user-defined function.
$udf.TextBody = "BEGIN DECLARE @ISOweek int SET @ISOweek= DATEPART(wk,@DATE)+1 -DATEPART(wk,CAST(DATEPART(yy,@DATE) as CHAR(4))+'0104') IF (@ISOweek=0) SET @ISOweek=dbo.ISOweek(CAST(DATEPART(yy,@DATE)-1 AS CHAR(4))+'12'+ CAST(24+DATEPART(DAY,@DATE) AS CHAR(2)))+1 IF ((DATEPART(mm,@DATE)=12) AND ((DATEPART(dd,@DATE)-DATEPART(dw,@DATE))>= 28)) SET @ISOweek=1 RETURN(@ISOweek) END;"  
  
# Create the user-defined function on the instance of SQL Server.
$udf.Create()  
  
# Remove the user-defined function.
$udf.Drop()  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.SqlServer.Management.Smo.UserDefinedFunction>  

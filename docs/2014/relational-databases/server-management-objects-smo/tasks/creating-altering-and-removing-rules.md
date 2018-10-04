---
title: Création, modification et suppression de règles | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- rules [SMO]
ms.assetid: 16981459-524e-4b39-a899-4370eaf763cc
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6785e14e6e6ef08c7b77daa5e7ab555d05ac1744
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084499"
---
# <a name="creating-altering-and-removing-rules"></a>Création, modification et suppression de règles
  Dans SMO, les règles sont représentées par l'objet <xref:Microsoft.SqlServer.Management.Smo.Rule>. La règle est définie par la propriété <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A>, qui est une chaîne de texte contenant une expression de condition qui utilise des opérateurs ou des prédicats, par exemple IN, LIKE ou BETWEEN. Elle ne peut pas faire référence à des colonnes ou à d'autres objets de base de données. Vous pouvez y inclure des fonctions intégrées qui ne font pas référence à des objets de base de données.  
  
 La définition dans la propriété <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> doit contenir une variable qui fait référence à la valeur de données entrée. N’importe quel nom ou le symbole peut être utilisé pour représenter la valeur lors de la création de la règle, mais le premier caractère doit être le \@ symbole.  
  
## <a name="example"></a>Exemple  
 Pour utiliser un exemple de code qui est fourni, vous devrez choisir l'environnement de programmation, le modèle de programmation et le langage de programmation dans lequel créer votre application. Pour plus d’informations, consultez [créer un projet SMO Visual Basic dans Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) ou [créer un Visual C&#35; projet SMO dans Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-basic"></a>Création, modification et suppression d'une règle en Visual Basic  
 Cet exemple de code montre comment créer une règle, l'attacher à une colonne, modifier des propriétés de l'objet <xref:Microsoft.SqlServer.Management.Smo.Rule>, la détacher de la colonne, puis la supprimer.  
  
 L'instruction `Dim` pour l'objet <xref:Microsoft.SqlServer.Management.Smo.Rule> est spécifiée avec le chemin d'accès complet de l'assembly pour éviter toute ambiguïté avec un objet <xref:Microsoft.SqlServer.Management.Smo.Rule> de l'assembly System.Data.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBRules1](SMO How to#SMO_VBRules1)]  -->  
  
## <a name="creating-altering-and-removing-a-rule-in-visual-c"></a>Création, modification et suppression d'une règle en Visual C#  
 Cet exemple de code montre comment créer une règle, l'attacher à une colonne, modifier des propriétés de l'objet <xref:Microsoft.SqlServer.Management.Smo.Rule>, la détacher de la colonne, puis la supprimer.  
  
 L'instruction `Dim` pour l'objet <xref:Microsoft.SqlServer.Management.Smo.Rule> est spécifiée avec le chemin d'accès complet de l'assembly pour éviter toute ambiguïté avec un objet <xref:Microsoft.SqlServer.Management.Smo.Rule> de l'assembly System.Data.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Rule object variable by supplying the parent database, name and schema in the constructor.   
            //Note that the full namespace must be given for the Rule type to differentiate it from other Rule types.   
            Microsoft.SqlServer.Management.Smo.Rule ru;  
            ru = new Rule(db, "TestRule", "Production");  
            //Set the TextHeader and TextBody properties to define the rule.   
            ru.TextHeader = "CREATE RULE [Production].[TestRule] AS";  
            ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())";  
            //Create the rule on the instance of SQL Server.   
            ru.Create();  
            //Bind the rule to a column in the Product table by supplying the table, schema, and   
            //column as arguments in the BindToColumn method.   
            ru.BindToColumn("Product", "SellEndDate", "Production");  
            //Unbind from the column before removing the rule from the database.   
            ru.UnbindFromColumn("Product", "SellEndDate", "Production");  
            ru.Drop();  
  
        }  
```  
  
## <a name="creating-altering-and-removing-a-rule-in-powershell"></a>Création, modification et suppression d'une règle dans PowerShell  
 Cet exemple de code montre comment créer une règle, l'attacher à une colonne, modifier des propriétés de l'objet <xref:Microsoft.SqlServer.Management.Smo.Rule>, la détacher de la colonne, puis la supprimer.  
  
 L'instruction `Dim` pour l'objet <xref:Microsoft.SqlServer.Management.Smo.Rule> est spécifiée avec le chemin d'accès complet de l'assembly pour éviter toute ambiguïté avec un objet <xref:Microsoft.SqlServer.Management.Smo.Rule> de l'assembly System.Data.  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a Rule object variable by supplying the parent database, name and schema in the constructor.   
$ru = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Rule `  
-argumentlist $db, "TestRule", "Production"  
  
#Set the TextHeader and TextBody properties to define the rule.   
$ru.TextHeader = "CREATE RULE [Production].[TestRule] AS"  
$ru.TextBody = "@value BETWEEN GETDATE() AND DATEADD(year,4,GETDATE())"  
  
#Create the rule on the instance of SQL Server.   
$ru.Create()  
  
# Bind the rule to a column in the Product table by supplying the table, schema, and   
# column as arguments in the BindToColumn method.   
$ru.BindToColumn("Product", "SellEndDate", "Production")  
  
#Unbind from the column before removing the rule from the database.   
$ru.UnbindFromColumn("Product", "SellEndDate", "Production")  
$ru.Drop()  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.SqlServer.Management.Smo.Rule>  
  
  

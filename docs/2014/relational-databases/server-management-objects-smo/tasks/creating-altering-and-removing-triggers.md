---
title: Création, modification et suppression de déclencheurs | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- triggers [SMO]
ms.assetid: 8ddbe23b-6e31-4f8e-8a70-17bd5072413e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2ae7ab9d88a407f298156ebeafdb6ec5d70198b1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48220639"
---
# <a name="creating-altering-and-removing-triggers"></a>Création, modification et suppression de déclencheurs
  Dans SMO, les déclencheurs sont représentés à l'aide de l'objet <xref:Microsoft.SqlServer.Management.Smo.Trigger>. Le [!INCLUDE[tsql](../../../includes/tsql-md.md)] code qui s’exécute lorsque le déclencheur est activé est défini par le <xref:Microsoft.SqlServer.Management.Smo.Trigger.TextBody%2A> propriété de l’objet déclencheur. Le type de déclencheur est défini à l'aide d'autres propriétés de l'objet <xref:Microsoft.SqlServer.Management.Smo.Trigger>, par exemple la propriété <xref:Microsoft.SqlServer.Management.Smo.Trigger.Update%2A>. Il s'agit d'une propriété booléenne qui spécifie si le déclencheur est activé par une `UPDATE` des enregistrements sur la table parente.  
  
 L'objet <xref:Microsoft.SqlServer.Management.Smo.Trigger> représente des déclencheurs traditionnels du langage de manipulation de données (DML). Dans [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] et les versions ultérieures, les déclencheurs DDL sont également pris en charge. Les déclencheurs DDL sont représentés par l'objet <xref:Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger> et l'objet <xref:Microsoft.SqlServer.Management.Smo.ServerDdlTrigger>.  
  
## <a name="example"></a>Exemple  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-basic"></a>Création, modification et suppression d'un déclencheur en Visual Basic  
 Cet exemple de code montre comment créer et insérer un déclencheur de mise à jour sur une table existante, nommée `Sales`, dans la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]. Le déclencheur envoie un message de rappel lorsque la table est mise à jour ou qu'un nouvel enregistrement est inséré.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBTriggers1](SMO How to#SMO_VBTriggers1)]  -->  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-c"></a>Création, modification et suppression d'un déclencheur en Visual C#  
 Cet exemple de code montre comment créer et insérer un déclencheur de mise à jour sur une table existante, nommée `Sales`, dans la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]. Le déclencheur envoie un message de rappel lorsque la table est mise à jour ou qu'un nouvel enregistrement est inséré.  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            Server mysrv;  
            mysrv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database mydb;  
            mydb = mysrv.Databases["AdventureWorks2012"];  
            //Declare a Table object variable and reference the Customer table.   
            Table mytab;  
            mytab = mydb.Tables["Customer", "Sales"];  
            //Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.   
            Trigger tr;  
            tr = new Trigger(mytab, "Sales");  
            //Set TextMode property to False, then set other properties to define the trigger.   
            tr.TextMode = false;  
            tr.Insert = true;  
            tr.Update = true;  
            tr.InsertOrder = ActivationOrder.First;  
            string stmt;  
            stmt = " RAISERROR('Notify Customer Relations',16,10) ";  
            tr.TextBody = stmt;  
            tr.ImplementationType = ImplementationType.TransactSql;  
            //Create the trigger on the instance of SQL Server.   
            tr.Create();  
            //Remove the trigger.   
            tr.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-trigger-in-powershell"></a>Création, modification et suppression d'un déclencheur dans PowerShell  
 Cet exemple de code montre comment créer et insérer un déclencheur de mise à jour sur une table existante, nommée `Sales`, dans la base de données [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)]. Le déclencheur envoie un message de rappel lorsque la table est mise à jour ou qu'un nouvel enregistrement est inséré.  
  
```  
# Set the path context to the local, default instance of SQL Server and to the  
#database tables in Adventureworks2012  
CD \sql\localhost\default\databases\AdventureWorks2012\Tables\  
  
#Get reference to the trigger's target table  
$mytab = get-item Sales.Customer  
  
# Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.  
$tr  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Trigger `  
-argumentlist $mytab, "Sales"  
  
# Set TextMode property to False, then set other properties to define the trigger.   
$tr.TextMode = $false  
$tr.Insert = $true  
$tr.Update = $true  
$tr.InsertOrder = [Microsoft.SqlServer.Management.SMO.Agent.ActivationOrder]::First  
$tr.TextBody = " RAISERROR('Notify Customer Relations',16,10) "  
$tr.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Create the trigger on the instance of SQL Server.   
$tr.Create()  
  
#Remove the trigger.   
$tr.Drop()  
```  
  
  

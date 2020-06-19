---
title: Définition des propriétés | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SMO [SQL Server], properties
- SQL Server Management Objects, properties
- properties [SMO]
ms.assetid: 342569ba-d2f7-44d2-8f3f-ae9c701c7f0f
author: stevestein
ms.author: sstein
ms.openlocfilehash: e82debe452a1fb4214c297d781e3a95146ec52aa
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063144"
---
# <a name="setting-properties"></a>Définition de propriétés
  Les propriétés sont des valeurs qui stockent des informations descriptives sur l'objet. Par exemple, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] les options de configuration sont représentées par les <xref:Microsoft.SqlServer.Management.Smo.Server.Configuration%2A> Propriétés de l’objet. Les propriétés sont accessibles soit directement, soit indirectement par le biais de la collection de propriétés. L'accès aux propriétés utilise directement la syntaxe suivante :  
  
 `objInstance.PropertyName`  
  
 Une valeur de propriété peut être modifiée ou récupérée selon que la propriété dispose d'un accès en lecture/écriture ou d'un accès en lecture seule. Il est également nécessaire de définir certaines propriétés avant qu'un objet ne puisse être créé. Pour plus d'informations, consultez la référence SMO pour l'objet particulier.  
  
> [!NOTE]  
>  Les collections d'objets enfants apparaissent en tant que propriété d'un objet. Par exemple, la collection `Tables` est une propriété d'un objet `Server`. Pour plus d'informations, voir [Using Collections](using-collections.md).  
  
 Les propriétés d'un objet sont membres de la collection Properties. La collection Properties peut être utilisée pour parcourir chaque propriété d'un objet.  
  
 Parfois, une propriété n'est pas disponible pour les raisons suivantes :  
  
-   La version du serveur ne prend pas en charge la propriété, notamment si vous essayez d'accéder à une propriété représentant une nouvelle fonctionnalité [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur une ancienne version de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Le serveur ne fournit pas de données pour la propriété, notamment si vous essayez d'accéder à une propriété représentant un composant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui n'est pas installé.  
  
 Vous pouvez gérer ces circonstances en interceptant les exceptions SMO <xref:Microsoft.SqlServer.Management.Smo.UnknownPropertyException> et <xref:Microsoft.SqlServer.Management.Smo.PropertyCannotBeRetrievedException>.  
  
## <a name="setting-default-initialization-fields"></a>Définition des champs d'initialisation par défaut  
 SMO effectue une optimisation lors de la récupération d'objets. L'optimisation réduit le nombre de propriétés chargées en procédant automatiquement à une mise à l'échelle entre les états suivants :  
  
1.  Partiellement chargé. Lorsqu'un objet est référencé pour la première fois, il dispose d'un nombre minimal de propriétés (telles que Nom et Schéma).  
  
2.  Complètement chargé. Lorsqu'une propriété est référencée, les propriétés restantes à chargement rapide sont initialisées et mises à disposition.  
  
3.  Propriétés qui utilisent beaucoup de mémoire. Les propriétés non disponibles restantes utilisent beaucoup de mémoire et la valeur de la propriété <xref:Microsoft.SqlServer.Management.Smo.Property.Expensive%2A> est True (par exemple <xref:Microsoft.SqlServer.Management.Smo.Database.DataSpaceUsage%2A>). Ces propriétés sont chargées uniquement lorsqu'elles sont spécifiquement référencées.  
  
 Si votre application extrait des propriétés supplémentaires, en plus de celles fournies dans l'état partiellement chargé, elle envoie une requête pour récupérer ces propriétés supplémentaires et passe à l'état complètement chargé. Cela peut générer un trafic inutile entre le client et le serveur. Vous pouvez bénéficier d'une meilleure optimisation en appelant la méthode <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A>. La méthode <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> vous permet de spécifier des propriétés qui sont chargées lors de l'initialisation de l'objet.  
  
 La méthode <xref:Microsoft.SqlServer.Management.Smo.Server.SetDefaultInitFields%2A> définit le comportement de chargement des propriétés pour le reste de l'application ou jusqu'à ce qu'elle soit réinitialisée. Vous pouvez enregistrer le comportement d'origine en utilisant la méthode <xref:Microsoft.SqlServer.Management.Smo.Server.GetDefaultInitFields%2A> et en la restaurant selon les besoins.  
  
## <a name="examples"></a>Exemples  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="getting-and-setting-a-property-in-visual-basic"></a>Obtention et définition d'une propriété en Visual Basic  
 Cet exemple de code montre comment obtenir la propriété <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Information> et comment attribuer à la propriété <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> de la propriété <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> le membre `ExecuteSql` du type énuméré <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes>.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties1](SMO How to#SMO_VBProperties1)]  -->  
  
## <a name="getting-and-setting-a-property-in-visual-c"></a>Obtention et définition d'une propriété en Visual C#  
 Cet exemple de code montre comment obtenir la propriété <xref:Microsoft.SqlServer.Management.Smo.Information.Edition%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Information> et comment attribuer à la propriété <xref:Microsoft.SqlServer.Management.Common.ServerConnection.SqlExecutionModes%2A> de la propriété <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> le membre `ExecuteSql` du type énuméré <xref:Microsoft.SqlServer.Management.Common.SqlExecutionModes>.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Get a property.   
Console.WriteLine(srv.Information.Version);   
//Set a property.   
srv.ConnectionContext.SqlExecutionModes = SqlExecutionModes.ExecuteSql;   
}  
```  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-basic"></a>Définition de différentes propriétés avant la création d'un objet en Visual Basic  
 Cet exemple de code montre comment définir directement la propriété <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Table>, et comment créer et ajouter des colonnes avant de créer l'objet <xref:Microsoft.SqlServer.Management.Smo.Table>.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties2](SMO How to#SMO_VBProperties2)]  -->  
  
## <a name="setting-various-properties-before-an-object-is-created-in-visual-c"></a>Définition de différentes propriétés avant la création d'un objet en Visual C#  
 Cet exemple de code montre comment définir directement la propriété <xref:Microsoft.SqlServer.Management.Smo.Table.AnsiNullsStatus%2A> de l'objet <xref:Microsoft.SqlServer.Management.Smo.Table>, et comment créer et ajouter des colonnes avant de créer l'objet <xref:Microsoft.SqlServer.Management.Smo.Table>.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Create a new table in the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
Table tb;   
//Specify the parent database, table schema, and the table name in the constructor.   
tb = new Table(db, "Test_Table", "HumanResources");   
//Add columns because the table requires columns before it can be created.   
Column c1;   
//Specify the parent table, the column name, and data type in the constructor.   
c1 = new Column(tb, "ID", DataType.Int);   
tb.Columns.Add(c1);   
c1.Nullable = false;   
c1.Identity = true;   
c1.IdentityIncrement = 1;   
c1.IdentitySeed = 0;   
Column c2;   
c2 = new Column(tb, "Name", DataType.NVarChar(100));   
c2.Nullable = false;   
tb.Columns.Add(c2);   
tb.AnsiNullsStatus = true;   
//Create the table on the instance of SQL Server.   
tb.Create();   
}  
```  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-basic"></a>Parcours de toutes les propriétés d'un objet en Visual Basic  
 Cet exemple de code parcourt la collection `Properties` de l'objet <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> et affiche les propriétés dans l'écran de sortie de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
 Dans l'exemple, l'objet <xref:Microsoft.SqlServer.Management.Smo.Property> a été mis entre crochets car il s'agit également d'un mot clé dans [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)].  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBProperties3](SMO How to#SMO_VBProperties3)]  -->  
  
## <a name="iterating-through-all-properties-of-an-object-in-visual-c"></a>Parcours de toutes les propriétés d'un objet en Visual C#  
 Cet exemple de code parcourt la collection `Properties` de l'objet <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> et affiche les propriétés dans l'écran de sortie de [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Set properties on the uspGetEmployeedManagers stored procedure on the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
StoredProcedure sp;   
sp = db.StoredProcedures("uspGetEmployeeManagers");   
sp.AnsiNullsStatus = false;   
sp.QuotedIdentifierStatus = false;   
//Iterate through the properties of the stored procedure and display.   
  Property p;   
  foreach ( p in sp.Properties) {   
    Console.WriteLine(p.Name + p.Value);   
  }   
}  
```  
  
## <a name="setting-default-initialization-fields-in-visual-basic"></a>Définition des champs d'initialisation par défaut en Visual Basic  
 Cet exemple de code montre comment réduire le nombre de propriétés d'objet initialisées dans un programme SMO. Vous devez inclure l'instruction `using System.Collections.Specialized` pour utiliser l'objet <xref:System.Collections.Specialized.StringCollection>.  
  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] peut être utilisé pour comparer le nombre d'instructions envoyées à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec cette optimisation.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDefaultInitFields1](SMO How to#SMO_VBDefaultInitFields1)]  -->  
  
## <a name="setting-default-initialization-fields-in-visual-c"></a>Définition des champs d'initialisation par défaut en Visual C#  
 Cet exemple de code montre comment réduire le nombre de propriétés d'objet initialisées dans un programme SMO. Vous devez inclure l'instruction `using System.Collections.Specialized` pour utiliser l'objet <xref:System.Collections.Specialized.StringCollection>.  
  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] peut être utilisé pour comparer le nombre d'instructions envoyées à l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec cette optimisation.  
  
```  
{   
//Connect to the local, default instance of SQL Server.   
Server srv;   
srv = new Server();   
//Reference the AdventureWorks2012 database.   
Database db;   
db = srv.Databases("AdventureWorks2012");   
//Assign the Table object type to a System.Type object variable.   
Table tb;   
Type typ;   
tb = new Table();   
typ = tb.GetType;   
//Assign the current default initialization fields for the Table object type to a   
//StringCollection object variable.   
StringCollection sc;   
sc = srv.GetDefaultInitFields(typ);   
//Set the default initialization fields for the Table object type to the CreateDate property.   
srv.SetDefaultInitFields(typ, "CreateDate");   
//Retrieve the Schema, Name, and CreateDate properties for every table in AdventureWorks2012.   
   //Note that the improvement in performance can be viewed in SQL Server Profiler.   
foreach ( tb in db.Tables) {   
   Console.WriteLine(tb.Schema + "." + tb.Name + " " + tb.CreateDate);   
}   
//Set the default initialization fields for the Table object type back to the original settings.   
srv.SetDefaultInitFields(typ, sc);   
}  
```  
  
  

---
title: Utilisation des synonymes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- synonyms [SMO]
ms.assetid: db0a9022-9549-43e5-b6b3-deb236f05fb8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a96f6ee89b920ec668af21ce625694fc31ce13bd
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "72781871"
---
# <a name="using-synonyms"></a>Utilisation de synonymes
  Un synonyme est un alias donné à un objet dans l'étendue du schéma. Dans SMO, les synonymes sont représentés par l'objet <xref:Microsoft.SqlServer.Management.Smo.Synonym>. L'objet <xref:Microsoft.SqlServer.Management.Smo.Synonym> est un enfant de l'objet <xref:Microsoft.SqlServer.Management.Smo.Database>. Cela signifie que les synonymes ne sont valides que dans le contexte de la base de données dans laquelle ils ont été définis. Toutefois, le synonyme peut faire référence aux objets d'une autre base de données ou d'une instance distante de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 L'objet auquel est attribué un alias est l'objet de base. La propriété de nom de l'objet <xref:Microsoft.SqlServer.Management.Smo.Synonym> est l'alias attribué à l'objet de base.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple de code suivant, vous devez sélectionner l'environnement, le modèle et le langage de programmation à utiliser pour créer votre application. Pour plus d’informations, consultez [créer un projet Visual Basic Smo dans Visual Studio .net](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) et [créer un projet Visual C&#35; Smo dans Visual Studio .net](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="creating-a-synonym-in-visual-basic"></a>Création d'un synonyme en Visual Basic  
 L'exemple de code montre comment créer un synonyme ou un alias pour un objet compris dans l'étendue du schéma. Les applications clientes peuvent utiliser une référence unique pour l'objet de base par le biais d'un synonyme, au lieu d'employer une référence en plusieurs parties à l'objet de base.  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBSynonyms1](SMO How to#SMO_VBSynonyms1)]  -->  
  
## <a name="creating-a-synonym-in-visual-c"></a>Création d'un synonyme en Visual C#  
 L'exemple de code montre comment créer un synonyme ou un alias pour un objet compris dans l'étendue du schéma. Les applications clientes peuvent utiliser une référence unique pour l'objet de base par le biais d'un synonyme, au lieu d'employer une référence en plusieurs parties à l'objet de base.  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Synonym object variable by supplying the   
            //parent database, name, and schema arguments in the constructor.   
            //The name is also a synonym of the name of the base object.   
            Synonym syn = new Synonym(db, "Shop", "Sales");  
  
            //Specify the base object, which is the object on which   
            //the synonym is based.   
            syn.BaseDatabase = "AdventureWorks2012";  
            syn.BaseSchema = "Sales";  
            syn.BaseObject = "Store";  
            syn.BaseServer = srv.Name;  
  
            //Create the synonym on the instance of SQL Server.   
            syn.Create();  
        }  
```  
  
## <a name="creating-a-synonym-in-powershell"></a>Création d'un synonyme dans PowerShell  
 L'exemple de code montre comment créer un synonyme ou un alias pour un objet compris dans l'étendue du schéma. Les applications clientes peuvent utiliser une référence unique pour l'objet de base par le biais d'un synonyme, au lieu d'employer une référence en plusieurs parties à l'objet de base.  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#And the database object corresponding to Adventureworks  
$db = $srv.Databases["AdventureWorks2012"]  
  
$syn = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Synonym -ArgumentList $db, "Shop", "Sales"  
  
#Specify the base object, which is the object on which the synonym is based.  
$syn.BaseDatabase = "AdventureWorks2012"  
$syn.BaseSchema = "Sales"  
$syn.BaseObject = "Store"  
$syn.BaseServer = $srv.Name  
  
#Create the synonym on the instance of SQL Server.  
$syn.Create()  
```  
  
## <a name="see-also"></a>Voir aussi  
 [CREATE SYNONYM &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-synonym-transact-sql)  

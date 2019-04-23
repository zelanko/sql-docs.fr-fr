---
title: Exemple Hello World | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: fed6c358-f5ee-4d4c-9ad6-089778383ba7
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8a44e246bbf6af319c21fca93e57177688c8fa4a
ms.sourcegitcommit: b87c384e10d6621cf3a95ffc79d6f6fad34d420f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60158975"
---
# <a name="hello-world-sample"></a>Exemple Hello World
  L'exemple Hello World montre les opérations de base à effectuer pour créer, déployer et tester une procédure stockée simple et basée sur l'intégration du CLR (Common Language Runtime). Cet exemple montre également comment retourner des données via un enregistrement qui est construit dynamiquement par la procédure stockée et retourné à l'appelant.  
  
 Le `HelloWorld` procédure stockée retourne la chaîne « Hello world ! » dans un jeu de résultats composé d’une ligne. Cet exemple illustre quelques utilisations pour les classes [Microsoft.SqlServer.Server.SqlMetaData](https://go.microsoft.com/fwlink/?LinkID=193572), [Microsoft.SqlServer.Server.SqlDataRecord](https://go.microsoft.com/fwlink/?LinkID=193573) et [ Microsoft.SqlServer.Server.Pipe](https://go.microsoft.com/fwlink/?LinkID=193571).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour créer et exécuter ce projet, les logiciels suivants doivent être installés :  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express. Vous pouvez vous procurer gratuitement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express à partir du site Web [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [(en anglais)](https://go.microsoft.com/fwlink/?LinkId=31046)  
  
-   Base de données AdventureWorks qui est disponible sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] site Web [du Centre pour les développeurs](https://go.microsoft.com/fwlink/?linkid=62796)  
  
-   Le Kit de développement logiciel .NET Framework SDK 2.0 ou version ultérieure, ou Microsoft Visual Studio 2005 ou version ultérieure. Vous pouvez vous procurer gratuitement le Kit de développement logiciel .NET Framework SDK.  
  
-   De plus, les conditions suivantes doivent être réunies :  
  
-   L'intégration du CLR doit être activée sur l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous utilisez.  
  
-   Pour activer l'intégration du CLR, effectuez les étapes suivantes :  
  
    #### <a name="enabling-clr-integration"></a>Activation de l'intégration du CLR  
  
    -   Exécutez les commandes [!INCLUDE[tsql](../../includes/tsql-md.md)] suivantes :  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  Pour activer l'intégration du CLR, vous devez disposer de l'autorisation de niveau serveur `ALTER SETTINGS` qui est attribuée implicitement aux membres des rôles serveur fixes `sysadmin` et `serveradmin`.  
  
-   La base de données AdventureWorks doit être installée sur l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous utilisez.  
  
-   Si vous n'êtes pas administrateur de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisée, vous devez demander à un administrateur de vous accorder l'autorisation **CreateAssembly** pour terminer l'installation.  
  
## <a name="building-the-sample"></a>Génération de l'exemple  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a>Créez et exécutez l'exemple à l'aide des instructions suivantes :  
  
1.  Ouvrez une invite de commandes Visual Studio ou .NET Framework.  
  
2.  Si nécessaire, créez un répertoire pour votre exemple. Pour cet exemple, nous utiliserons C:\MySample.  
  
3.  Dans c:\MySample, créez `HelloWorld.vb` (pour l'exemple Visual Basic) ou `HelloWorld.cs` (pour l'exemple C#) et copiez l'exemple de code Visual Basic ou  C# approprié (ci-dessous) dans le fichier.  
  
4.  Compilez l'exemple de code à partir de l'invite de ligne de commande en exécutant l'un des éléments suivants, selon le langage choisi.  
  
    -   `vbc C:HelloWorld.vb /target:library`  
  
    -   `csc /target:library HelloWorld.cs`  
  
5.  Copiez le code d'installation [!INCLUDE[tsql](../../includes/tsql-md.md)] dans un fichier et enregistrez-le sous `Install.sql` dans le répertoire d'exemple.  
  
6.  Déployez l'assembly et la procédure stockée en exécutant  
  
    -   `sqlcmd -E -I -i install.sql -v root = "C:\MySample\"`  
  
7.  Copiez le script de la commande de test [!INCLUDE[tsql](../../includes/tsql-md.md)] dans un fichier et enregistrez-le sous `test.sql` dans le répertoire d'exemple.  
  
8.  Exécutez le script de test avec la commande suivante  
  
    -   `sqlcmd -E -I -i test.sql`  
  
9. Copiez le script de nettoyage [!INCLUDE[tsql](../../includes/tsql-md.md)] dans un fichier et enregistrez-le sous `cleanup.sql` dans le répertoire d'exemple.  
  
10. Exécutez le script avec la commande suivante  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a>Exemple de code  
 Voici les listes de code pour cet exemple.  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
public partial class StoredProcedures  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld()  
    {  
        Microsoft.SqlServer.Server.SqlMetaData columnInfo  
                = new Microsoft.SqlServer.Server.SqlMetaData("Column1", SqlDbType.NVarChar, 12);  
        SqlDataRecord greetingRecord  
            = new SqlDataRecord(new Microsoft.SqlServer.Server.SqlMetaData[] { columnInfo });  
        greetingRecord.SetString(0, "Hello world!");  
        SqlContext.Pipe.Send(greetingRecord);  
    }  
};  
  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public NotInheritable Class StoredProcedures  
    <Microsoft.SqlServer.Server.SqlProcedure()> _  
    Public Shared Sub HelloWorld()  
        Dim columnInfo As New Microsoft.SqlServer.Server.SqlMetaData("Column1", _  
            SqlDbType.NVarChar, 12)  
        Dim greetingRecord As New SqlDataRecord(New  _  
            Microsoft.SqlServer.Server.SqlMetaData() {columnInfo})  
        greetingRecord.SetString(0, "Hello World!")  
        SqlContext.Pipe.Send(greetingRecord)  
    End Sub  
End Class  
```  
  
 Il s'agit du script d'installation [!INCLUDE[tsql](../../includes/tsql-md.md)] (`Install.sql`), qui déploie l'assembly et crée la procédure stockée dans la base de données.  
  
```  
USE AdventureWorks  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorld')  
DROP ASSEMBLY HelloWorld;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
set @SamplesPath = '$(root)'  
CREATE ASSEMBLY HelloWorld   
FROM @SamplesPath + 'HelloWorld.dll'  
WITH permission_set = Safe;  
GO  
  
CREATE PROCEDURE usp_HelloWorld  
--(  
--    @Greeting nvarchar(12) OUTPUT  
--)  
AS EXTERNAL NAME HelloWorld.[StoredProcedures].HelloWorld;  
GO  
```  
  
 Il s'agit de `test.sql`, qui teste l'exemple en exécutant la procédure stockée.  
  
```  
use AdventureWorks  
go  
execute usp_HelloWorld  
  
USE AdventureWorks;  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
```  
  
 Le code [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant supprime l'assembly et la procédure stockée de la base de données.  
  
```  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorld')  
DROP ASSEMBLY HelloWorld;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Scénarios et exemples d’utilisation pour l’intégration du CLR &#40;Common Language Runtime&#41;](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  

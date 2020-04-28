---
title: Exemple de Hello World Ready | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: 1cb94266-f702-4a57-a1ae-689a89c98757
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8303c387ff38ab5448d15e478534df165e05bddf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "73637657"
---
# <a name="hello-world-ready-sample"></a>Exemple HelloWorldReady
  L'exemple HelloWorldReady présente les opérations de base à effectuer pour créer, déployer et tester une procédure stockée simple basée sur l'intégration du CLR (Common Language Runtime) et adaptée pour un usage international. Un composant est dit adapté pour un usage international lorsqu'il est possible de le localiser facilement, sans changer son code source, en différentes langues pour divers marchés dans le monde entier. Cet exemple montre également comment retourner des données via un paramètre de sortie et via un enregistrement, qui est construit de manière dynamique par la procédure stockée et est retourné au client. Cet exemple est presque identique à l'exemple Hello World, mais il est beaucoup plus facile et sécurisé de localiser cette application. La modification du texte localisé nécessite les opérations suivantes :  
  
1.  Modification d’un fichier XML (.`resx` ) pour la culture particulière dans le répertoire Resources  
  
2.  Génération du fichier des ressources de la culture à l'aide de l'utilitaire `resgen`.  
  
3.  Génération de la DLL satellite mise à jour pour cette culture.  
  
4.  Suppression et ajout de cet assembly dans SQL Server.  
  
 Le code source et l'assembly pour la procédure stockée CLR elle-même ne changent pas. Un script `build.cmd` est fourni, qui montre comment compiler et lier les assemblys de ressource. Bien que le code source pour l'application crée un gestionnaire de ressources basé sur l'assembly en cours d'exécution, vous n'avez pas à incorporer les ressources neutres de culture dans la DLL qui contient la procédure stockée. Le `System.Resources.NeutralResourcesLanguage attribute` permet aux ressources indépendantes de la culture d'exister dans une DLL satellite. Il est bien plus avantageux d'utiliser une DLL distincte à cet effet, de sorte qu'il ne soit pas nécessaire de modifier la DLL principale contenant la procédure stockée CLR lorsqu'un texte localisé doit être ajouté ou modifié. Cela set particulièrement utile pour les types clr définis par l'utilisateur qui peuvent avoir des colonnes et d'autres dépendances qui rendraient la suppression et le rajout du type difficiles à effectuer. Généralement, les versions de DLL satellites doivent être identiques à la version d'assembly principale. Toutefois, vous pouvez utiliser l'attribut `SatelliteContractVersion` pour permettre une mise à jour de l'assembly principal sans mise à jour des assemblys satellites. Pour plus d'informations, consultez la classe `ResourceManager` dans la documentation Microsoft .NET.  
  
## <a name="prerequisites"></a>Prérequis  
 Cet exemple fonctionne uniquement avec SQL Server 2005 et les versions ultérieures.  
  
 Pour créer et exécuter ce projet, les logiciels suivants doivent être installés :  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express. Vous pouvez vous procurer gratuitement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express à partir du site Web [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [(en anglais)](https://www.microsoft.com/sql-server/sql-server-editions-express)  
  
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
  
-   Si vous n’êtes pas administrateur de l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance que vous utilisez, vous devez demander à un administrateur de vous accorder l’autorisation **CreateAssembly** pour terminer l’installation.  
  
## <a name="building-the-sample"></a>Génération de l'exemple  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a>Créez et exécutez l'exemple à l'aide des instructions suivantes :  
  
1.  Ouvrez une invite de commandes Visual Studio ou .NET Framework.  
  
2.  Si nécessaire, créez un répertoire pour votre exemple. Pour cet exemple, nous utiliserons C:\MySample.  
  
3.  Dans c:\MySample, créez `HelloWorld.vb` (pour l'exemple Visual Basic) ou `HelloWorld.cs` (pour l'exemple C#) et copiez l'exemple de code Visual Basic ou  C# approprié (ci-dessous) dans le fichier.  
  
4.  Dans c:\MySample, créez le fichier `messages.resx` et copiez l'exemple de code C# dans le fichier.  
  
5.  Dans c:\MySample, créez le fichier `messages.de.resx` en enregistrant le `messages.resx` fichier `messages.de.resx` comme après avoir modifié la ligne.  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   Pour lire  
  
    -   `<value xml:space="preserve">Hallo Welt!</value>`  
  
6.  Dans c:\MySample, créez le fichier `messages.es.resx` en enregistrant le `messages.resx` fichier `messages.es.resx` comme après avoir modifié la ligne.  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   Pour lire  
  
    -   `<value xml:space="preserve">Hola a todos</value>`  
  
7.  Dans c:\MySample, créez le fichier `messages.fr.resx` en enregistrant le `messages.resx` fichier `messages.fr.resx` comme après avoir modifié la ligne.  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   Pour lire  
  
    -   `<value xml:space="preserve">BonjourÂ !</value>`  
  
8.  Dans c:\MySample, créez le fichier `messages.fr-FR.resx` en enregistrant le `messages.resx` fichier `messages.fr-FR.resx` comme après avoir modifié la ligne.  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   Pour lire  
  
    -   `<value xml:space="preserve">Bonjour de France!</value>`  
  
9. Dans c:\MySample, créez le fichier `messages.it.resx` en enregistrant le `messages.resx` fichier `messages.it.resx` comme après avoir modifié la ligne.  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   Pour lire  
  
    -   `<value xml:space="preserve">Buongiorno</value>`  
  
10. Dans c:\MySample, créez le fichier `messages.ja.resx` en enregistrant le `messages.resx` fichier `messages.ja.resx` comme après avoir modifié la ligne.  
  
    -   `<value xml:space="preserve">Hello, World!</value>`  
  
    -   Pour lire  
  
    -   `<value xml:space="preserve">` `ã"ã‚"ã«ã¡ã¯</value>`  
  
11. Dans c:\MySample, créez le fichier `build.com` et copiez l'exemple de code dans le fichier.  
  
12. Générez l'assembly satellite en exécutant la version de fichier à l'invite de commandes.  
  
13. Compilez l'exemple de code de l'invite de ligne de commande en exécutant l'une des commandes suivantes :  
  
    -   `Vbc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll,C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Xml.dll /out:HelloWorldReady.dll /target:library HelloWorld.vb`  
  
    -   `Csc /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.Data.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.dll /reference:C:\Windows\Microsoft.NET\Framework\v2.0.50727\System.XML.dll /out:HelloWorldReady.dll /target:library Hello.csCopy the tsql installation code into a file and save it as Install.sql in the sample directory.`  
  
14. Si l'exemple est installé dans un répertoire autre que `C:\MySample\`, modifiez le fichier `Install.sql` comme indiqué pour pointer sur cet emplacement.  
  
15. Déployez l'assembly et la procédure stockée en exécutant  
  
    -   `sqlcmd -E -I -i install.sql`  
  
16. Copiez le script de la commande de test [!INCLUDE[tsql](../../includes/tsql-md.md)] dans un fichier et enregistrez-le sous `test.sql` dans le répertoire d'exemple.  
  
17. Exécutez le script de test avec la commande suivante  
  
    -   `sqlcmd -E -I -i test.sql`  
  
18. Copiez le script de nettoyage [!INCLUDE[tsql](../../includes/tsql-md.md)] dans un fichier et enregistrez-le sous `cleanup.sql` dans le répertoire d'exemple.  
  
19. Exécutez le script avec la commande suivante  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a>Exemple de code  
 Voici les listes de code pour cet exemple.  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.Sql;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
using System.Globalization;  
using System.Threading;  
using System.Resources;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
  
[assembly: System.Resources.NeutralResourcesLanguage("", System.Resources.UltimateResourceFallbackLocation.Satellite)]  
[assembly: System.Security.Permissions.SecurityPermissionAttribute(System.Security.Permissions.SecurityAction.RequestMinimum)]  
[assembly: System.Runtime.ConstrainedExecution.ReliabilityContract(System.Runtime.ConstrainedExecution.Consistency.MayCorruptInstance, System.Runtime.ConstrainedExecution.Cer.None)]  
  
    public sealed partial class StoredProcedures  
    {  
        private StoredProcedures()  
        {  
        }  
  
        [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1021:AvoidOutParameters"), Microsoft.SqlServer.Server.SqlProcedure]  
        public static void HelloWorldReady(string culture, out string greeting)  
        {  
ResourceManager rm   
= new ResourceManager("Messages",   
Assembly.GetExecutingAssembly());  
  
string message = rm.GetString("HelloWorld", CultureInfo.GetCultureInfo(culture));  
  
            Microsoft.SqlServer.Server.SqlMetaData columnInfo  
                = new Microsoft.SqlServer.Server.SqlMetaData("Column1", SqlDbType.NVarChar, 24);  
            SqlDataRecord greetingRecord  
                = new SqlDataRecord(new Microsoft.SqlServer.Server.SqlMetaData[] { columnInfo });  
            greetingRecord.SetString(0, message);  
            SqlContext.Pipe.Send(greetingRecord);  
            greeting = message;  
        }  
    }  
  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Globalization  
Imports System.Resources  
Imports System.Reflection  
Imports System.Runtime.InteropServices  
<Assembly: AssemblyVersion("1.0.*")>   
<Assembly: System.Runtime.InteropServices.ComVisible(False)>   
<Assembly: System.CLSCompliant(True)>   
<Assembly: System.Resources.NeutralResourcesLanguage("", System.Resources.UltimateResourceFallbackLocation.Satellite)>   
<Assembly: System.Security.Permissions.SecurityPermissionAttribute(System.Security.Permissions.SecurityAction.RequestMinimum)>   
<Assembly: System.Runtime.ConstrainedExecution.ReliabilityContract(System.Runtime.ConstrainedExecution.Consistency.WillNotCorruptState, Runtime.ConstrainedExecution.Cer.None)>   
  
Partial Public NotInheritable Class StoredProcedures  
    Private Sub New()  
    End Sub  
    <Microsoft.SqlServer.Server.SqlProcedure()> _  
    Public Shared Sub HelloWorldReady(ByVal culture As String, ByRef greeting As String)  
        Dim rm As New ResourceManager("Messages", Assembly.GetExecutingAssembly())  
        Dim message As String = rm.GetString("HelloWorld", CultureInfo.GetCultureInfo(culture))  
        Dim columnInfo As New Microsoft.SqlServer.Server.SqlMetaData("Column1", _  
            SqlDbType.NVarChar, 24)  
        Dim greetingRecord As New SqlDataRecord(New  _  
            Microsoft.SqlServer.Server.SqlMetaData() {columnInfo})  
        greetingRecord.SetString(0, message)  
        SqlContext.Pipe.Send(greetingRecord)  
        greeting = message  
    End Sub  
End Class  
  
```  
  
 Il s'agit de `build.com`, qui génère les assemblys satellites.  
  
```  
resgen Messages.resx  
resgen Messages.de.resx  
resgen Messages.es.resx  
resgen Messages.fr.resx  
resgen Messages.fr-Fr.resx  
resgen Messages.it.resx  
resgen Messages.ja.resx  
if not exist de/ mkdir de  
if not exist es/ mkdir es  
if not exist fr/ mkdir fr  
if not exist fr-FR/ mkdir fr-FR  
if not exist it/ mkdir it  
if not exist ja/ mkdir ja  
al /t:lib /culture:de /embed:Messages.de.resources /out:de\HelloWorldReady.resources.dll  
al /t:lib /culture:es /embed:Messages.es.resources /out:es\HelloWorldReady.resources.dll  
al /t:lib /culture:fr /embed:Messages.fr.resources /out:fr\HelloWorldReady.resources.dll  
al /t:lib /culture:fr-FR /embed:Messages.fr-FR.resources /out:fr-FR\HelloWorldReady.resources.dll  
al /t:lib /culture:it /embed:Messages.it.resources /out:it\HelloWorldReady.resources.dll  
al /t:lib /culture:ja /embed:Messages.ja.resources /out:ja\HelloWorldReady.resources.dll  
al /t:lib /culture:"" /embed:Messages.resources /out:HelloWorldReady.resources.dll  
```  
  
 Il s'agit du script d'installation [!INCLUDE[tsql](../../includes/tsql-md.md)] (`Install.sql`), qui déploie les assemblys et crée la procédure stockée dans la base de données.  
  
```  
USE AdventureWorks  
GO  
  
-- Drop existing sproc and assembly if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorldReady')  
DROP PROCEDURE usp_HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady')  
DROP ASSEMBLY HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.neutral')  
DROP ASSEMBLY [HelloWorldReady.resources.neutral]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.de')  
DROP ASSEMBLY [HelloWorldReady.resources.de]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.es')  
DROP ASSEMBLY [HelloWorldReady.resources.es]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr')  
DROP ASSEMBLY [HelloWorldReady.resources.fr]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr-FR')  
DROP ASSEMBLY [HelloWorldReady.resources.fr-FR]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.it')  
DROP ASSEMBLY [HelloWorldReady.resources.it]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.ja')  
DROP ASSEMBLY [HelloWorldReady.resources.ja]  
GO  
  
DECLARE @SamplesPath nvarchar(1024)  
-- You may need to modify the value of this variable if you have installed the sample someplace other than the default location.  
Set @SamplesPath = N'C:\MySample\'  
  
-- Add the assembly and CLR integration based stored procedure  
  
CREATE ASSEMBLY HelloWorldReady  
FROM @SamplesPath + 'HelloWorldReady.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.neutral]  
FROM @SamplesPath + 'HelloWorldReady.resources.dll'  
WITH permission_set = Safe;   
  
CREATE ASSEMBLY [HelloWorldReady.resources.de]  
FROM @SamplesPath + '\de\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.es]  
FROM @SamplesPath + '\es\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.fr]  
FROM @SamplesPath + '\fr\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.fr-FR]  
FROM @SamplesPath + '\fr-FR\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.it]  
FROM @SamplesPath + '\it\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
  
CREATE ASSEMBLY [HelloWorldReady.resources.ja]  
FROM @SamplesPath + '\ja\HelloWorldReady.resources.dll'  
WITH permission_set = Safe;  
GO  
  
CREATE PROCEDURE usp_HelloWorldReady  
(  
@Culture NVarchar(12),  
@Greeting NVarchar(24) OUTPUT  
)  
AS EXTERNAL NAME HelloWorldReady.StoredProcedures.HelloWorldReady;  
GO  
  
USE master;  
GO  
```  
  
 Il s'agit de `test.sql`, qui teste l'exemple en exécutant les fonctions sur chaque paramètre régional.  
  
```  
USE AdventureWorks  
GO  
  
DECLARE @GreetingDe nvarchar(24);  
DECLARE @GreetingDe_CH nvarchar(24);  
DECLARE @GreetingEn nvarchar(24);  
DECLARE @GreetingEs nvarchar(24);  
DECLARE @GreetingFr nvarchar(24);  
DECLARE @GreetingFr_FR nvarchar(24);  
DECLARE @GreetingIt nvarchar(24);  
DECLARE @GreetingJa nvarchar(24);  
  
--German as spoken anywhere in the world (the neutral German culture)  
EXEC usp_HelloWorldReady 'de', @GreetingDe OUTPUT;  
--German as spoken in Switzerland.  Because we don't have a specific assembly  
--for this case, the .NET Framework will automatically fall back to the neutral German culture DLL.  
EXEC usp_HelloWorldReady 'de-CH', @GreetingDe_CH OUTPUT;  
EXEC usp_HelloWorldReady 'en', @GreetingEn OUTPUT;  
EXEC usp_HelloWorldReady 'es', @GreetingEs OUTPUT;  
--French as spoken anywhere in the world (the neutral French culture)  
EXEC usp_HelloWorldReady 'fr', @GreetingFr OUTPUT  
--French as spoken in France.  Since we do have a specific assembly for this case, a specific   
--greeting is provided from that DLL.  The neutral French culture DLL is not used in this case.  
EXEC usp_HelloWorldReady 'fr-FR', @GreetingFr_FR OUTPUT  
EXEC usp_HelloWorldReady 'it', @GreetingIt OUTPUT;  
EXEC usp_HelloWorldReady 'ja', @GreetingJa OUTPUT;  
  
SELECT @GreetingDe AS OUTPUT_PARAMETER_DE;  
SELECT @GreetingDe_CH AS OUTPUT_PARAMETER_De_CH;  
SELECT @GreetingEn AS OUTPUT_PARAMETER_EN;  
SELECT @GreetingEs AS OUTPUT_PARAMETER_ES;  
SELECT @GreetingFr AS OUTPUT_PARAMETER_FR;  
SELECT @GreetingFr_FR AS OUTPUT_PARAMETER_Fr_FR;  
SELECT @GreetingIt AS OUTPUT_PARAMETER_IT;  
SELECT @GreetingJa AS OUTPUT_PARAMETER_JA;  
  
GO  
```  
  
 Le code [!INCLUDE[tsql](../../includes/tsql-md.md)] suivant supprime les assemblys et la procédure stockée de la base de données.  
  
```  
USE AdventureWorks;  
GO  
  
-- Drop existing sproc and assembly if any.  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorldReady')  
DROP PROCEDURE usp_HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady')  
DROP ASSEMBLY HelloWorldReady;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.neutral')  
DROP ASSEMBLY [HelloWorldReady.resources.neutral]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.de')  
DROP ASSEMBLY [HelloWorldReady.resources.de]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.es')  
DROP ASSEMBLY [HelloWorldReady.resources.es]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr')  
DROP ASSEMBLY [HelloWorldReady.resources.fr]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.fr-FR')  
DROP ASSEMBLY [HelloWorldReady.resources.fr-FR]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.it')  
DROP ASSEMBLY [HelloWorldReady.resources.it]  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorldReady.resources.ja')  
DROP ASSEMBLY [HelloWorldReady.resources.ja]  
GO  
  
USE master;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Scénarios et exemples d’utilisation pour l’intégration du CLR &#40;Common Language Runtime&#41;](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  

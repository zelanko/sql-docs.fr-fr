---
title: Configuration de SQL Server dans SMO
ms.custom: seo-dt-2019
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server, configuring
- configuration options [SMO]
ms.assetid: 0a372643-15cb-45a7-8665-04f1215df8ed
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f973b47d4b55624e0f78658f7dfa13ec1aebd80c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74095951"
---
# <a name="configuring-sql-server-in-smo"></a>Configuration de SQL Server dans SMO
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

  Dans SMO, l' <xref:Microsoft.SqlServer.Management.Smo.Information> <xref:Microsoft.SqlServer.Management.Smo.Settings> objet, l’objet, l' <xref:Microsoft.SqlServer.Management.Smo.UserOptions> objet et l' <xref:Microsoft.SqlServer.Management.Smo.Configuration> objet contiennent des paramètres et des informations pour l’instance [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]de.  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] possède de nombreuses propriétés qui décrivent le comportement de l'instance installée. Les propriétés décrivent les options de démarrage, les valeurs par défaut du serveur, les fichiers et répertoires, les informations sur le processeur et le système, le produit et les versions, les informations sur la connexion, les options de mémoire, les sélections de langue et de classement et le mode d'authentification.  
  
## <a name="sql-server-configuration"></a>Configuration de SQL Server  
 Les propriétés de l'objet <xref:Microsoft.SqlServer.Management.Smo.Information> contiennent des informations sur l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], par exemple le processeur et la plateforme.  
  
 Les propriétés de l'objet <xref:Microsoft.SqlServer.Management.Smo.Settings> contiennent des informations sur l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le fichier et le répertoire par défaut de la base de données peuvent être modifiés en plus du profil de messagerie et du compte du serveur. Ces propriétés restent valables pendant toute la durée de la connexion.  
  
 Les propriétés de l'objet <xref:Microsoft.SqlServer.Management.Smo.UserOptions> contiennent des informations sur le comportement des connexions actuelles en ce qui concerne l'arithmétique, les normes ANSI et les transactions.  
  
 Il existe également un jeu d'options de configuration représenté par l'objet <xref:Microsoft.SqlServer.Management.Smo.Configuration>. Il contient un jeu de propriétés qui représentent les options qui peuvent être modifiées par la procédure stockée **sp_configure** . Les options telles **que renforcement de priorité**, intervalle de **récupération** et **taille du paquet réseau**contrôlent les [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]performances de l’instance de. Nombre de ces options peuvent être modifiées de manière dynamique, mais dans certains cas, la valeur est d'abord configurée, puis modifiée lorsque l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est redémarrée.  
  
 Il existe une propriété d'objet <xref:Microsoft.SqlServer.Management.Smo.Configuration> pour chaque option de configuration. Vous pouvez modifier le paramètre de configuration global en utilisant l'objet <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>. De nombreuses propriétés disposent de valeurs minimum et maximum qui sont également stockées sous la forme de propriétés <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty>. Ces propriétés requièrent <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> la méthode pour valider la modification apportée [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]à l’instance de.  
  
 Toutes les options de configuration de l'objet <xref:Microsoft.SqlServer.Management.Smo.Configuration> doivent être modifiées par l'administrateur système.  
  
## <a name="examples"></a>Exemples  
 Dans les exemples de code suivants, vous devez sélectionner l'environnement, le modèle et le langage de programmation à utiliser pour créer votre application. Pour plus d’informations, consultez [créer un projet Visual C&#35; Smo dans Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).  
  
## <a name="modifying-sql-server-configuration-options-in-visual-basic"></a>Modification des options de configuration de SQL Server en Visual Basic  
 L'exemple de code montre comment mettre à jour une option de configuration en Visual Basic .NET. Il récupère et affiche également des informations relatives aux valeurs minimale et maximale de l'option de configuration spécifiée. Enfin, le programme indique à l'utilisateur si la modification a été apportée dynamiquement ou si elle est stockée jusqu'au redémarrage de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Display all the configuration options.
Dim p As ConfigProperty
For Each p In srv.Configuration.Properties
    Console.WriteLine(p.DisplayName)
Next
Console.WriteLine("There are " & srv.Configuration.Properties.Count.ToString & " configuration options.")
'Display the maximum and minimum values for ShowAdvancedOptions.
Dim min As Integer
Dim max As Integer
min = srv.Configuration.ShowAdvancedOptions.Minimum
max = srv.Configuration.ShowAdvancedOptions.Maximum
Console.WriteLine("Minimum and Maximum values are " & min & " and " & max & ".")
'Modify the value of ShowAdvancedOptions and run the Alter method.
srv.Configuration.ShowAdvancedOptions.ConfigValue = 0
srv.Configuration.Alter()
'Display when the change takes place according to the IsDynamic property.
If srv.Configuration.ShowAdvancedOptions.IsDynamic = True Then
    Console.WriteLine("Configuration option has been updated.")
Else
    Console.WriteLine("Configuration option will be updated when SQL Server is restarted.")
End If
``` 
  
## <a name="modifying-sql-server-settings-in-visual-basic"></a>Modification des paramètres de SQL Server en Visual Basic  
 L’exemple de code affiche des informations sur l' [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance <xref:Microsoft.SqlServer.Management.Smo.Information> de <xref:Microsoft.SqlServer.Management.Smo.Settings>dans et, et modifie les <xref:Microsoft.SqlServer.Management.Smo.Settings> paramètres <xref:Microsoft.SqlServer.Management.Smo.UserOptions>dans et les propriétés de l’objet.  
  
 Dans l'exemple, l'objet <xref:Microsoft.SqlServer.Management.Smo.UserOptions> et l'objet <xref:Microsoft.SqlServer.Management.Smo.Settings> disposent tous deux d'une méthode <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. Vous pouvez exécuter ces méthodes <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> individuellement.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Display information about the instance of SQL Server in Information and Settings.
Console.WriteLine("OS Version = " & srv.Information.OSVersion)
Console.WriteLine("State = " & srv.Settings.State.ToString)
'Display information specific to the current user in UserOptions.
Console.WriteLine("Quoted Identifier support = " & srv.UserOptions.QuotedIdentifier)
'Modify server settings in Settings.

srv.Settings.LoginMode = ServerLoginMode.Integrated
'Modify settings specific to the current connection in UserOptions.
srv.UserOptions.AbortOnArithmeticErrors = True
'Run the Alter method to make the changes on the instance of SQL Server.
srv.Alter()
```
  
## <a name="modifying-sql-server-settings-in-visual-c"></a>Modification des paramètres de SQL Server en Visual C#  
 L’exemple de code affiche des informations sur l' [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance <xref:Microsoft.SqlServer.Management.Smo.Information> de <xref:Microsoft.SqlServer.Management.Smo.Settings>dans et, et modifie les <xref:Microsoft.SqlServer.Management.Smo.Settings> paramètres <xref:Microsoft.SqlServer.Management.Smo.UserOptions>dans et les propriétés de l’objet.  
  
 Dans l'exemple, l'objet <xref:Microsoft.SqlServer.Management.Smo.UserOptions> et l'objet <xref:Microsoft.SqlServer.Management.Smo.Settings> disposent tous deux d'une méthode <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. Vous pouvez exécuter ces méthodes <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> individuellement.  
  
 `//Connect to the local, default instance of SQL Server.`  
  
```csharp  
{  
            Server srv = new Server();  
            //Display all the configuration options.   
  
            foreach (ConfigProperty p in srv.Configuration.Properties)  
            {  
                Console.WriteLine(p.DisplayName);  
            }  
            Console.WriteLine("There are " + srv.Configuration.Properties.Count.ToString() + " configuration options.");  
            //Display the maximum and minimum values for ShowAdvancedOptions.   
            int min = 0;  
            int max = 0;  
            min = srv.Configuration.ShowAdvancedOptions.Minimum;  
            max = srv.Configuration.ShowAdvancedOptions.Maximum;  
            Console.WriteLine("Minimum and Maximum values are " + min + " and " + max + ".");  
            //Modify the value of ShowAdvancedOptions and run the Alter method.   
            srv.Configuration.ShowAdvancedOptions.ConfigValue = 0;  
            srv.Configuration.Alter();  
            //Display when the change takes place according to the IsDynamic property.   
            if (srv.Configuration.ShowAdvancedOptions.IsDynamic == true)  
            {  
                Console.WriteLine("Configuration option has been updated.");  
            }  
            else  
            {  
                Console.WriteLine("Configuration option will be updated when SQL Server is restarted.");  
            }  
        }  
```  
  
## <a name="modifying-sql-server-settings-in-powershell"></a>Modification des paramètres de SQL Server dans PowerShell  
 L’exemple de code affiche des informations sur l' [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance <xref:Microsoft.SqlServer.Management.Smo.Information> de <xref:Microsoft.SqlServer.Management.Smo.Settings>dans et, et modifie les <xref:Microsoft.SqlServer.Management.Smo.Settings> paramètres <xref:Microsoft.SqlServer.Management.Smo.UserOptions>dans et les propriétés de l’objet.  
  
 Dans l'exemple, l'objet <xref:Microsoft.SqlServer.Management.Smo.UserOptions> et l'objet <xref:Microsoft.SqlServer.Management.Smo.Settings> disposent tous deux d'une méthode <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A>. Vous pouvez exécuter ces méthodes <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> individuellement.  
  
```powershell 
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = get-item default  
  
#Display information about the instance of SQL Server in Information and Settings.  
"OS Version = " + $srv.Information.OSVersion  
"State = "+ $srv.Settings.State.ToString()  
  
#Display information specific to the current user in UserOptions.  
"Quoted Identifier support = " + $srv.UserOptions.QuotedIdentifier  
  
#Modify server settings in Settings.  
$srv.Settings.LoginMode = [Microsoft.SqlServer.Management.SMO.ServerLoginMode]::Integrated  
  
#Modify settings specific to the current connection in UserOptions.  
$srv.UserOptions.AbortOnArithmeticErrors = $true  
  
#Run the Alter method to make the changes on the instance of SQL Server.  
$srv.Alter()  
```  
  
## <a name="modifying-sql-server-configuration-options-in-powershell"></a>Modification des options de configuration de SQL Server dans PowerShell  
 L'exemple de code montre comment mettre à jour une option de configuration en Visual Basic .NET. Il récupère et affiche également des informations relatives aux valeurs minimale et maximale de l'option de configuration spécifiée. Enfin, le programme indique à l'utilisateur si la modification a été apportée dynamiquement ou si elle est stockée jusqu'au redémarrage de l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
```powershell 
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalMachine  
$svr = get-item default  
  
#enumerate its properties  
foreach ($Item in $Svr.Configuration.Properties)   
{  
 $Item.DisplayName  
}  
  
"There are " + $svr.Configuration.Properties.Count.ToString() + " configuration options."  
  
#Display the maximum and minimum values for ShowAdvancedOptions.  
$min = $svr.Configuration.ShowAdvancedOptions.Minimum  
$max = $svr.Configuration.ShowAdvancedOptions.Maximum  
"Minimum and Maximum values are " + $min.ToString() + " and " + $max.ToString() + "."  
  
#Modify the value of ShowAdvancedOptions and run the Alter method.  
$svr.Configuration.ShowAdvancedOptions.ConfigValue = 0  
$svr.Configuration.Alter()  
  
#Display when the change takes place according to the IsDynamic property.  
If ($svr.Configuration.ShowAdvancedOptions.IsDynamic -eq $true)  
 {    
   "Configuration option has been updated."  
 }  
Else  
{  
    "Configuration option will be updated when SQL Server is restarted."  
}  
```  
  
  

---
title: Charger les assemblys SMO dans Windows PowerShell | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ca42b69-da5a-47f4-9085-34e443f0e389
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 149ba0be18c46dbf2171f7a1fac0641ae81d3515
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="load-the-smo-assemblies-in-windows-powershell"></a>Charger les assemblys SMO dans Windows PowerShell
  Cette rubrique décrit comment charger les assemblys SMO (SQL Server Management Object) dans des scripts Windows PowerShell qui n'utilisent pas le fournisseur SQL Server PowerShell.  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Le mécanisme recommandé pour le chargement des assemblys SMO consiste à charger le module **sqlps** . Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inclus dans le module charge automatiquement les assemblys SMO et implémente des fonctionnalités qui étendent l'utilité des objets SMO dans les scripts PowerShell.  Pour plus d’informations, consultez [Importer le module SQLPS](../../relational-databases/scripting/import-the-sqlps-module.md).
  
 Il existe deux cas dans lesquels vous pouvez être amené à charger les assemblys SMO directement :  
  
-   Votre script fait référence à un objet SMO avant la première commande faisant référence au fournisseur ou aux applets de commande des composants logiciels enfichables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Vous souhaitez porter du code SMO à partir d'un autre langage, par exemple C# ou Visual Basic, qui n'utilise pas le fournisseur ou les applets de commande.  
  
## <a name="example-loading-the-sql-server-management-objects"></a>Exemple : chargement d'objets SMO (SQL Server Management Object)  
 Le code suivant charge les assemblys SMO :  
  
```  
#  
# Loads the SQL Server Management Objects (SMO)  
#  
  
$ErrorActionPreference = "Stop"  
  
$sqlpsreg="HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.SqlServer.Management.PowerShell.sqlps"  
  
if (Get-ChildItem $sqlpsreg -ErrorAction "SilentlyContinue")  
{  
    throw "SQL Server Provider for Windows PowerShell is not installed."  
}  
else  
{  
    $item = Get-ItemProperty $sqlpsreg  
    $sqlpsPath = [System.IO.Path]::GetDirectoryName($item.Path)  
}  
  
$assemblylist =   
"Microsoft.SqlServer.Management.Common",  
"Microsoft.SqlServer.Smo",  
"Microsoft.SqlServer.Dmf ",  
"Microsoft.SqlServer.Instapi ",  
"Microsoft.SqlServer.SqlWmiManagement ",  
"Microsoft.SqlServer.ConnectionInfo ",  
"Microsoft.SqlServer.SmoExtended ",  
"Microsoft.SqlServer.SqlTDiagM ",  
"Microsoft.SqlServer.SString ",  
"Microsoft.SqlServer.Management.RegisteredServers ",  
"Microsoft.SqlServer.Management.Sdk.Sfc ",  
"Microsoft.SqlServer.SqlEnum ",  
"Microsoft.SqlServer.RegSvrEnum ",  
"Microsoft.SqlServer.WmiEnum ",  
"Microsoft.SqlServer.ServiceBrokerEnum ",  
"Microsoft.SqlServer.ConnectionInfoExtended ",  
"Microsoft.SqlServer.Management.Collector ",  
"Microsoft.SqlServer.Management.CollectorEnum",  
"Microsoft.SqlServer.Management.Dac",  
"Microsoft.SqlServer.Management.DacEnum",  
"Microsoft.SqlServer.Management.Utility"  
  
foreach ($asm in $assemblylist)  
{  
    $asm = [Reflection.Assembly]::LoadWithPartialName($asm)  
}  
  
Push-Location  
cd $sqlpsPath  
update-FormatData -prependpath SQLProvider.Format.ps1xml   
Pop-Location  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  


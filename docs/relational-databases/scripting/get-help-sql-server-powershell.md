---
title: "Obtenir de l’aide sur SQL Server PowerShell | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [PowerShell]
- Help [SQL Server], PowerShell
- PowerShell [SQL Server], help
ms.assetid: 968c316d-db83-4c24-8ea6-9f18736842f7
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ed2c615535a6886f5157be2eda71de15f54ce1f0
ms.lasthandoff: 04/11/2017

---
# <a name="get-help-sql-server-powershell"></a>Obtenir de l'aide sur SQL Server PowerShell
  Il existe plusieurs sources d'informations sur l'utilisation du fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour Windows PowerShell et des applets de commande. Cela inclut l'aide qui est disponible dans l'environnement Windows PowerShell.  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Pour en savoir plus sur Windows PowerShell, consultez le [Guide Mise en route de Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=217083).  
  
 Pour obtenir une vue d’ensemble des applets de commande et du fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md).  
  
### <a name="help-in-the-windows-powershell-environment"></a>Aide dans l'environnement Windows PowerShell  
 Utilisez l’applet de commande **Get-Help** pour obtenir de l’aide dans l’environnement Windows PowerShell. **Get-Help** fournit l’aide de base pour le langage Windows PowerShell, ainsi que pour les différentes applets de commande et les divers fournisseurs disponibles dans Windows PowerShell.  
  
 Pour plus d’informations sur les moyens d’utiliser **Get-Help**, consultez [Obtention d’aide : Get-Help](http://go.microsoft.com/fwlink/?LinkId=102136).  
  
### <a name="sql-server-powershell-provider-help"></a>Aide du fournisseur PowerShell SQL Server  
 Le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell implémente plusieurs dossiers sur un lecteur virtuel SQLSERVER, tels que les dossiers SQLSERVER:\SQL et SQLSERVER:\DAC. Chaque dossier est associé à l'un des modèles d'objet de gestion SQL Server. Vous pouvez répertorier les méthodes et les propriétés associées à chaque nœud dans un chemin d'accès SQL Server, mais vous ne pouvez pas obtenir de l'aide sur celles-ci dans l'environnement PowerShell. Pour obtenir un tableau des dossiers avec des liens à la référence de programmation associée, consultez [SQL Server PowerShell Provider](../../relational-databases/scripting/sql-server-powershell-provider.md).  
  
### <a name="invoke-sqlcmd-help"></a>Aide d'Invoke-Sqlcmd  
 L’applet de commande **Invoke-Sqlcmd** utilise comme entrée une requête ou un fichier de script exécutable par l’utilitaire **sqlcmd** . Vous pouvez utiliser **Get-Help** pour obtenir des informations concernant **Invoke-Sqlcmd** et ses paramètres, mais **Get-Help** ne couvre pas les requêtes **sqlcmd** .  
  
 L’entrée *-Query* ou *-QueryFromFile* peut contenir :  
  
-   Variables et commandes**sqlcmd** . Pour plus d'informations sur ces variables et commandes, consultez la section Notes de [sqlcmd Utility](../../tools/sqlcmd-utility.md).  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] . Pour plus d’informations sur le langage [!INCLUDE[tsql](../../includes/tsql-md.md)], consultez [Référence Transact-SQL &#40;moteur de base de données&#41;](../../t-sql/transact-sql-reference-database-engine.md).  
  
-   Instructions XQuery. Pour plus d’informations sur le langage XQuery pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Références relatives au langage Xquery &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md).  
  
## <a name="get-help-for-a-sql-server-cmdlet"></a>Obtenir de l'aide pour une applet de commande SQL Server  
 **Pour obtenir de l'aide pour une applet de commande**  
  
-   Exécutez Get-Help en spécifiant le nom de l'applet de commande et le niveau de l'aide à retourner.  
  
### <a name="example-cmdlet-get-help"></a>Exemple : applet de commande Get-Help  
 Les exemples ci-après renvoient différents niveaux d’aide pour **Invoke-Sqlcmd**:  
  
```  
## Get the basic help.  
Get-Help Invoke-Sqlcmd  
  
## Get the full help.  
Get-Help Invoke-Sqlcmd –Full  
  
## Get the parameter descriptions.  
Get-Help Invoke-Sqlcmd -Parameter *  
  
## Get the code examples.  
Get-Help Invoke-Sqlcmd –Examples  
  
## Get the syntax diagram.  
Get-Help Invoke-Sqlcmd –Syntax  
```  
  
## <a name="get-a-list-of-providers"></a>Obtenir une liste de fournisseurs  
 **Pour obtenir une liste des fournisseurs actifs**  
  
1.  Exécutez Get-Help en spécifiant la catégorie de fournisseur.  
  
 Pour plus d'informations sur l'obtention d'aide sur les fournisseurs dans Windows PowerShell, consultez [Drives and Providers](http://go.microsoft.com/fwlink/?LinkId=102137)(en anglais).  
  
### <a name="example-get-a-list-of-providers"></a>Exemple : obtenir une liste de fournisseurs  
 Le code suivant retourne la liste des fournisseurs actuellement activés dans votre session Windows PowerShell :  
  
```  
Get-Help -Category provider  
```  
  
## <a name="get-help-about-the-sql-server-provider"></a>Obtenir de l'aide sur le fournisseur SQL Server  
 **Pour obtenir de l'aide sur le fournisseur**  
  
1.  Exécuter Get-Help en spécifiant le nom SQLServer  
  
### <a name="example-get-sql-server-provider-help"></a>Exemple : obtenir de l'aide sur le fournisseur SQL Server  
 Cet exemple retourne des informations de base sur le fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
```  
Get-Help SQLServer  
```  
  
## <a name="list-methods-and-properties"></a>Répertorier les méthodes et les propriétés  
 **Pour répertorier les méthodes et les propriétés pour un nœud dans un chemin d'accès du fournisseur SQL Server**  
  
1.  Utilisez la commande CD pour passer à un nœud dans le chemin d'accès de SQL Server ou créez une variable ayant pour valeur cet emplacement.  
  
2.  Exécutez l’applet de commande **Get-Member** avec le paramètre –Type défini sur Methods ou Properties.  
  
### <a name="examples-listing-methods-and-properties"></a>Exemples : affichage de la liste des méthodes et des propriétés  
 L'exemple suivant répertorie les méthodes prises en charge pour le nœud Bases de données :  
  
```  
Set-Location SQL:\MyComputer\DEFAULT\Databases  
Get-Item . | Get-Member -Type Methods  
```  
  
 Cet exemple répertorie les propriétés pour une variable dont la valeur est un objet SMO Table :  
  
```  
$MyVar = New-Object Microsoft.SqlServer.Management.SMO.Table  
$MyVar | Get-Member -Type Properties  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server PowerShell Provider](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [Utiliser les applets de commande du Moteur de base de données](../../relational-databases/scripting/use-the-database-engine-cmdlets.md)  
  
  

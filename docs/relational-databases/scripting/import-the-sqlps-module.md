---
title: "Importer le module SQLPS | Microsoft Docs"
ms.custom: ""
ms.date: "08/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a972c56e-b2af-4fe6-abbd-817406e2c93a
caps.latest.revision: 12
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 11
---
# Importer le module SQLPS
  La méthode recommandée pour gérer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir de PowerShell consiste à importer le module **sqlps** dans un environnement Windows PowerShell. Le module charge et inscrit les assemblys de facilité de gestion et les composants logiciels enfichables [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  À partir de Windows PowerShell 3.0, les modules sont importés automatiquement lorsqu’une applet de commande ou une fonction dans le module est utilisée dans une commande. Cette fonctionnalité fonctionne sur n’importe quel module d’un répertoire inclus dans la valeur de la variable d’environnement PSModulePath.  Pour plus d’informations, consultez [Importation d’un module PowerShell](https://msdn.microsoft.com/library/dd878284(v=vs.85).aspx)
  
1.  **Avant de commencer :**  [Sécurité](#Security)  
  
2.  **Pour charger le module :**  [Charger le module sqlps](#LoadSqlps)  
  
## Avant de commencer  
 Après avoir importé le module **sqlps** dans Windows PowerShell, vous pouvez :  
  
-   exécuter des commandes Windows PowerShell de façon interactive ;  
  
-   exécuter des fichiers de script Windows PowerShell ;  
  
-   exécuter des applets de commande [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   utiliser les chemins d'accès du fournisseur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour naviguer dans la hiérarchie des objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   utiliser les modèles objets de la facilité de gestion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (tels que Microsoft.SqlServer.Management.Smo) pour gérer des objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Les verbes utilisés dans les noms de deux applets de commande SQL Server (**Encode-Sqlname** et **Decode-Sqlname**) ne correspondent pas aux verbes approuvés pour Windows PowerShell. Cela n'a aucun effet sur leur opération, mais Windows PowerShell déclenche un avertissement lorsque le module **sqlps** est importé dans une session.  
  
###  <a name="Security"></a> Sécurité  
 Par défaut, Windows PowerShell s’exécute avec le niveau **Restreint**de la stratégie d’exécution de scripts, ce qui empêche l’exécution de tout script Windows PowerShell. Pour charger le module **sqlps**, vous pouvez utiliser l’applet de commande **Set-ExecutionPolicy** pour activer l’exécution de scripts signés ou de tout type de script. Exécutez uniquement des scripts provenant de sources fiables et sécurisez tous les fichiers d'entrée et de sortie en utilisant les autorisations NTFS appropriées. Pour plus d'informations sur l'activation de scripts Windows PowerShell, consultez [Exécution de scripts Windows PowerShell](http://www.microsoft.com/technet/scriptcenter/topics/winpsh/manual/run.mspx).  
  
##  <a name="LoadSqlps"></a> Charger le module sqlps  
 **Pour charger le module sqlps dans Windows PowerShell**  
  
1.  Utilisez l’applet de commande **Set-ExecutionPolicy** pour définir la stratégie d’exécution de scripts appropriée.  
  
2.  Utilisez l’applet de commande **Import-Module** pour importer le module sqlps. Spécifiez le paramètre **DisableNameChecking** si vous souhaitez supprimer l’avertissement sur **Encode-Sqlname** et **Decode-Sqlname**.  
  
###  Exemple  
 Cet exemple charge le module **sqlps** avec la fonction de vérification des noms désactivée.  
  
```powershell 
# Import the SQL Server Module.    
Import-Module Sqlps -DisableNameChecking;

# To check whether the module is installed.
Get-Module -ListAvailable -Name Sqlps;
```  
  
> [!NOTE]  
>  Si le module **sqlps** ne se trouve pas sur votre chemin d’accès, indiquez l’emplacement du module ou le chemin d’accès complet dans le script (en utilisant des guillemets doubles de dossiers dans votre chemin d’accès, avec des espaces). Le module **sqlps** se trouve dans le dossier Tools\Powershell associé à votre instance SQL Server.  
  
 ![Icône de flèche utilisée avec le lien Retour en haut](../../analysis-services/instances/media/uparrow16x16.png "Icône de flèche utilisée avec le lien Retour en haut") [&#91;Haut&#93;](#Intro)  
  
## Voir aussi  
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)   
 [fournisseur PowerShell SQL Server](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [Utiliser les applets de commande du Moteur de base de données](../../relational-databases/scripting/use-the-database-engine-cmdlets.md)  
 [Installation d’un module PowerShell](https://msdn.microsoft.com/library/dd878350(v=vs.85).aspx)  
 [Module d’importation](https://technet.microsoft.com/library/hh849725.aspx)
  
  
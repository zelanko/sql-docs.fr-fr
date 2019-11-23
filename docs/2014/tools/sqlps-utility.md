---
title: Utilitaire sqlps | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- sqlps utility
- PowerShell [SQL Server], sqlps utility
ms.assetid: 4b2515a6-12c3-44fb-b263-1c567681cd2b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8ff96b99ee7982be89126e79687dbc8a2215f42f
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798136"
---
# <a name="sqlps-utility"></a>Utilitaire sqlps
  L'utilitaire `sqlps` démarre une session Windows PowerShell 2.0 avec les applets de commande et le fournisseur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell chargés et inscrits. Vous pouvez entrer des scripts ou des commandes PowerShell qui utilisent les composants [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell pour travailler avec des instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et leurs objets.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)] Utilisez plutôt le module `sqlps` PowerShell. Pour plus d’informations sur le module `sqlps`, consultez [importer le module sqlps](../database-engine/import-the-sqlps-module.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      sqlps   
[ [ [ -NoLogo ][ -NoExit ][ -NoProfile ]  
    [ -OutPutFormat { Text | XML } ] [ -InPutFormat { Text | XML } ]  
  ]  
  [ -Command { -  
             | script_block [ -argsargument_array ]  
             | string [ command_parameters ]  
             }  
  ]  
]  
[ -? | -Help ]  
```  
  
## <a name="arguments"></a>Arguments  
 **-NoLogo**  
 Spécifie que l'utilitaire `sqlps` doit masquer la bannière de copyright lorsqu'il démarre.  
  
 **-NoExit**  
 Spécifie que l'utilitaire `sqlps` doit poursuivre son exécution après le lancement des commandes de démarrage.  
  
 **-NoProfile**  
 Spécifie que l'utilitaire `sqlps` ne doit pas charger de profil utilisateur. Les profils utilisateur enregistrent des alias, fonctions et variables fréquemment utilisés en vue de leur utilisation au cours de différentes sessions PowerShell.  
  
 **-OutPutFormat** { **Text** | **XML** }  
 Spécifie que la sortie de l’utilitaire `sqlps` être mise en forme en tant que chaînes de texte (**texte**) ou dans un format CLIXML sérialisé (**XML**).  
  
 **-InPutFormat** { **Text** | **XML** }  
 Spécifie que l’entrée de l’utilitaire de `sqlps` est mise en forme en tant que chaînes de texte (**texte**) ou dans un format CLIXML sérialisé (**XML**).  
  
 **-Command**  
 Spécifie la commande de l'utilitaire `sqlps` à utiliser. L’utilitaire `sqlps` exécute la commande, puis se ferme, sauf si **-NoExit** est également spécifié. Ne spécifiez pas d’autres commutateurs après **-Command**, car ils seront lus comme des paramètres de commande.  
  
 **-**  
 **-Command :** spécifie que l’utilitaire de `sqlps` lit l’entrée à partir de l’entrée standard.  
  
 *script_block* [ **-args**_argument_array_ ]  
 Spécifie un bloc de commandes PowerShell à exécuter ; le bloc doit être placé entre des accolades : {}. *Script_block* peut être spécifié uniquement quand l’utilitaire `sqlps` est appelé à partir de **PowerShell** ou d’une autre session de l’utilitaire de `sqlps`. *argument_array* est un tableau de variables PowerShell contenant les arguments pour les commandes PowerShell de *script_block*.  
  
 *string* [ *command_parameters* ]  
 Spécifie une chaîne qui contient les commandes PowerShell à exécuter. Utilisez le format **« & { *`command`* } »** . Les guillemets indiquent une chaîne, tandis que l’opérateur d’appel (&) entraîne l’exécution de la commande par l’utilitaire `sqlps`.  
  
 [ **-?** |  **-Help** ]  
 Affiche le récapitulatif de la syntaxe des options de l'utilitaire `sqlps`.  
  
## <a name="remarks"></a>Notes  
 L’utilitaire `sqlps` démarre l’environnement PowerShell (PowerShell. exe) et charge le module [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell. Le module, également nommé `sqlps`, charge et inscrit ces composants logiciels enfichables PowerShell [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] :  
  
-   Microsoft.SqlServer.Management.PSProvider.dll  
  
     Implémente le fournisseur PowerShell pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les applets de commande associées, comme **Encode-SqlName** et **Decode-SqlName**.  
  
-   Microsoft.SqlServer.Management.PSSnapin.dll  
  
     Implémente les applets de commande **Invoke-Sqlcmd** et **Invoke-PolicyEvaluation** .  
  
 Vous pouvez recourir à l'utilitaire `sqlps` pour effectuer les opérations suivantes :  
  
-   exécuter des commandes PowerShell de façon interactive ;  
  
-   exécuter des fichiers script PowerShell ;  
  
-   exécuter des applets de commande [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ;  
  
-   utiliser les chemins d'accès du fournisseur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour naviguer dans la hiérarchie des objets [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ;  
  
 Par défaut, l’utilitaire `sqlps` s’exécute avec la stratégie d’exécution de script définie sur **restreint**. Cela empêche l'exécution de scripts PowerShell. Vous pouvez utiliser l’applet de commande **Set-ExecutionPolicy** pour activer l’exécution de scripts signés ou de tout type de script. Exécutez uniquement des scripts provenant de sources fiables et sécurisez tous les fichiers d'entrée et de sortie en utilisant les autorisations NTFS appropriées. Pour plus d'informations sur l'activation de scripts PowerShell, consultez [Exécution de scripts Windows PowerShell](https://www.tech-recipes.com/rx/2513/powershell_enable_script_support/).  
  
 La version de l'utilitaire `sqlps` dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] et [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] a été implémentée en tant que mini-shell Windows PowerShell 1.0. Les mini-shells comportent certaines restrictions, comme le fait de ne pas autoriser les utilisateurs à charger des composants logiciels enfichables autres que ceux chargés par le mini-shell. Ces restrictions ne s'appliquent pas à la version [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] et aux versions ultérieures de l'utilitaire, qui ont été modifiées pour utiliser le module `sqlps`.  
  
## <a name="examples"></a>Exemples  

### <a name="a-run-the-sqlps-utility-in-default-interactive-mode-without-the-copyright-banner"></a>A. Exécution de l’utilitaire sqlps en mode interactif par défaut, sans bannière de copyright
  
```cmd
sqlps -NoLogo  
```  
  
### <a name="b-run-a-sql-server-powershell-script-from-the-command-prompt"></a>B. Exécution d'un script SQL Server PowerShell à partir de l'invite de commandes
  
```cmd
sqlps -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
### <a name="c-run-a-sql-server-powershell-script-from-the-command-prompt-and-keep-running-after-the-script-completes"></a>C. Exécution d'un script SQL Server PowerShell à partir de l'invite de commandes et poursuite de l'exécution une fois le script terminé
  
```cmd
sqlps -NoExit -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Activer ou désactiver un protocole réseau de serveur](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)  

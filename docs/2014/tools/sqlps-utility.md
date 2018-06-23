---
title: Utilitaire sqlps | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- sqlps utility
- PowerShell [SQL Server], sqlps utility
ms.assetid: 4b2515a6-12c3-44fb-b263-1c567681cd2b
caps.latest.revision: 20
author: mgblythe
ms.author: mblythe
manager: jhubbard
ms.openlocfilehash: b49895ee08de2a9f08d263c92f5372c6b22ec604
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042617"
---
# <a name="sqlps-utility"></a>sqlps (utilitaire)
  L'utilitaire `sqlps` démarre une session Windows PowerShell 2.0 avec les applets de commande et le fournisseur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell chargés et inscrits. Vous pouvez entrer des scripts ou des commandes PowerShell qui utilisent les composants [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell pour travailler avec des instances de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et leurs objets.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../includes/ssnotedepfutureavoid-md.md)] Utilisez plutôt le module `sqlps` PowerShell. Pour plus d’informations sur la `sqlps` module, consultez [importer le Module SQLPS](../database-engine/import-the-sqlps-module.md).  
  
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
 Spécifie que le `sqlps` sortie de l’utilitaire mettre en forme comme chaînes de texte (**texte**) ou dans un format CLIXML sérialisé (**XML**).  
  
 **-InPutFormat** { **Text** | **XML** }  
 Spécifie que l’entrée de la `sqlps` utilitaire est mis en forme comme chaînes de texte (**texte**) ou dans un format CLIXML sérialisé (**XML**).  
  
 **-Command**  
 Spécifie la commande de l'utilitaire `sqlps` à utiliser. Le `sqlps` utilitaire s’exécute la commande, puis se ferme, sauf si **- NoExit** est également spécifié. Ne spécifiez pas d’autres commutateurs après **-Command**, car ils seront lus comme des paramètres de commande.  
  
 **-**  
 **-Command -** Spécifie que le `sqlps` utilitaire lire l’entrée de l’entrée standard.  
  
 *script_block* [ **-args***argument_array* ]  
 Spécifie un bloc de commandes PowerShell à exécuter ; le bloc doit être placé entre des accolades : {}. *Script_block* peut être spécifié uniquement lorsque le `sqlps` utilitaire est appelé depuis **PowerShell** ou un autre `sqlps` session de l’utilitaire. *argument_array* est un tableau de variables PowerShell contenant les arguments pour les commandes PowerShell de *script_block*.  
  
 *string* [ *command_parameters* ]  
 Spécifie une chaîne qui contient les commandes PowerShell à exécuter. Utilisez le format **« & {*`command`*} »**. Les guillemets indiquent une chaîne et l'opérateur d'appel (&) entraîne l'exécution de la commande par l'utilitaire `sqlps`.  
  
 [ **-?** | **-Help** ]  
 Affiche le récapitulatif de la syntaxe des options de l'utilitaire `sqlps`.  
  
## <a name="remarks"></a>Notes  
 Le `sqlps` utilitaire démarre l’environnement PowerShell (PowerShell.exe) et charge le [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] module PowerShell. Le module, également nommé `sqlps`, charge et inscrit ces [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] les composants logiciels enfichables PowerShell :  
  
-   Microsoft.SqlServer.Management.PSProvider.dll  
  
     Implémente le fournisseur PowerShell pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les applets de commande associées, comme **Encode-SqlName** et **Decode-SqlName**.  
  
-   Microsoft.SqlServer.Management.PSSnapin.dll  
  
     Implémente les applets de commande **Invoke-Sqlcmd** et **Invoke-PolicyEvaluation** .  
  
 Vous pouvez recourir à l'utilitaire `sqlps` pour effectuer les opérations suivantes :  
  
-   exécuter des commandes PowerShell de façon interactive ;  
  
-   exécuter des fichiers script PowerShell ;  
  
-   exécuter des applets de commande [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ;  
  
-   utiliser les chemins d'accès du fournisseur [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] pour naviguer dans la hiérarchie des objets [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ;  
  
 Par défaut, le `sqlps` utilitaire s’exécute avec la stratégie d’exécution scripts **Restricted**. Cela empêche l'exécution de scripts PowerShell. Vous pouvez utiliser l’applet de commande **Set-ExecutionPolicy** pour activer l’exécution de scripts signés ou de tout type de script. Exécutez uniquement des scripts provenant de sources fiables et sécurisez tous les fichiers d'entrée et de sortie en utilisant les autorisations NTFS appropriées. Pour plus d'informations sur l'activation de scripts PowerShell, consultez [Exécution de scripts Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=103166).  
  
 La version de la `sqlps` utilitaire dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] et [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] a été implémenté en tant que Windows PowerShell 1.0 mini-shell. Les mini-shells comportent certaines restrictions, comme le fait de ne pas autoriser les utilisateurs à charger des composants logiciels enfichables autres que ceux chargés par le mini-shell. Ces restrictions ne s'appliquent pas à la version [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] et aux versions ultérieures de l'utilitaire, qui ont été modifiées pour utiliser le module `sqlps`.  
  
## <a name="examples"></a>Exemples  
 **A. Exécuter l’utilitaire sqlps en mode interactif par défaut, sans bannière de copyright**  
  
```  
sqlps -NoLogo  
```  
  
 **B. Exécuter un script SQL Server PowerShell à partir de l’invite de commandes**  
  
```  
sqlps -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
 **C. Exécuter un script SQL Server PowerShell à partir de l’invite de commandes et poursuivre l’exécution une fois le script terminé**  
  
```  
sqlps -NoExit -Command "&{.\MyFolder.MyScript.ps1}"  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Activer ou désactiver un protocole réseau de serveur](../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)   
 [SQL Server PowerShell](../powershell/sql-server-powershell.md)  
  
  
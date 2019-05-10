---
title: Extension PowerShell
titleSuffix: Azure Data Studio
description: Installer et utiliser la commande PowerShell pour Azure Data Studio
ms.custom: seodec18
ms.date: 04/19/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: SQLvariant
ms.author: aanelson
manager: matthend
ms.openlocfilehash: c7a2dbdccf92a52d5733a04915acc3f76dc3f033
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105945"
---
# <a name="powershell-editor-support-for-azure-data-studio"></a>Prise en charge de l’éditeur PowerShell pour Azure Data Studio

Cette extension offre un support de l’éditeur PowerShell enrichi dans [Azure Data Studio](https://github.com/Microsoft/azuredatastudio).
Vous pouvez maintenant écrire et déboguer des scripts PowerShell à l’aide de l’interface IDE de type excellent fournies par Azure Data Studio.

![Extension PowerShell](media/powershell-extension/powershell-extension.png)


## <a name="features"></a>Fonctionnalités

- La coloration syntaxique
- Extraits de code
- IntelliSense pour les applets de commande et bien plus encore
- Analyse basée sur les règles fournie par [Analyseur de Script PowerShell](http://github.com/PowerShell/PSScriptAnalyzer)
- Atteindre la définition des variables et des applets de commande
- Rechercher des références des applets de commande et des variables
- Découverte de symbole de document et l’espace de travail
- Exécuter la sélection sélectionnée de l’utilisation de code PowerShell <kbd>F8</kbd>
- Lancer l’aide en ligne pour le symbole sous le curseur à l’aide <kbd>Ctrl</kbd>+<kbd>F1</kbd>
- Prise en charge de la console interactive Visual Basic !


## <a name="installing-the-extension"></a>Installation de l’Extension

Vous pouvez installer la version officielle de l’extension PowerShell en suivant les étapes décrites dans le [documentation d’Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/extensions).
Dans le volet Extensions, recherche d’extension de « PowerShell » et y installer.  Vous êtes informé automatiquement sur les mises à jour de l’extension future !

Vous pouvez également installer un package VSIX à partir de notre [page des publications](https://github.com/PowerShell/vscode-powershell/releases) et l’installer via la ligne de commande :

```powershell
azuredatastudio --install-extension PowerShell-<version>.vsix
```

## <a name="platform-support"></a>Prise en charge de la plateforme

- **Windows des 7 à 10** avec Windows PowerShell v3 et versions ultérieures et PowerShell Core
- **Linux** avec PowerShell Core (toutes les distributions prises en charge de PowerShell)
- **macOS** avec PowerShell Core

Lire le [FAQ](https://github.com/PowerShell/vscode-powershell/wiki/FAQ) pour obtenir des réponses aux questions courantes.

## <a name="installing-powershell-core"></a>Installation de PowerShell Core

Si vous exécutez Azure Data Studio sur Mac OS ou Linux, vous serez peut-être amené à installer PowerShell Core.

PowerShell Core est un projet Open Source sur [GitHub](https://github.com/powershell/powershell).
Pour plus d’informations sur l’installation de PowerShell Core sur des plateformes Mac OS ou Linux, consultez les articles suivants :

- [Installation de PowerShell Core sur Linux](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-6)
- [Installation de PowerShell Core sur macOS](https://docs.microsoft.com/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-6)

## <a name="example-scripts"></a>Exemples de Scripts

Il existe quelques exemples des scripts dans l’extension `examples` dossier que vous pouvez utiliser pour découvrir PowerShell Édition et fonctionnalités de débogage.  Découvrez les éléments inclus [README.md](https://github.com/PowerShell/vscode-powershell/blob/master/examples/README.md) fichier pour en savoir plus sur comment les utiliser.

Vous trouverez ce dossier à l’emplacement suivant :

```powershell
$HOME/.azuredatastudio/extensions/ms-vscode.PowerShell-<version>/examples
```

ou si vous utilisez la version préliminaire de l’extension

 ```powershell
$HOME/.azuredatastudio/extensions/ms-vscode.powershell-preview-<version>/examples
```

Pour ouvrir/afficher les exemples de l’extension dans Azure Data Studio, exécutez le code suivant à partir de l’invite de commandes PowerShell :

```powershell
azuredatastudio (Get-ChildItem $Home\.azuredatastudio\extensions\ms-vscode.PowerShell-*\examples)[-1]
```

### <a name="creating-and-opening-files"></a>Création et ouverture de fichiers

Pour créer et ouvrir un nouveau fichier à l’intérieur de l’éditeur, utilisez New-EditorFile à partir de dans le Terminal intégré de PowerShell.

```powershell
PS C:\temp> New-EditorFile ExportData.ps1
```

Cette commande fonctionne pour n’importe quel type de fichier, pas seulement les fichiers PowerShell.

```powershell
PS C:\temp> New-EditorFile ImportData.py
```

Pour ouvrir un ou plusieurs fichiers dans Azure Data Studio, utilisez le `Open-EditorFile` commande.

```powershell
Open-EditorFile ExportData.ps1, ImportData.py
```

### <a name="no-focus-on-console-when-executing"></a>Sans le focus sur la console lors de l’exécution

Pour les utilisateurs qui sont utilisés pour l’utilisation de SSMS, vous êtes habitué à la possibilité d’exécuter une requête et en étant capable d’exécuter de nouveau à nouveau sans avoir à basculer vers le volet de requête.  Dans ce cas, le comportement par défaut de l’éditeur de code peut paraître étrange pour vous.  Pour conserver le focus dans l’éditeur lorsque vous exécutez avec <kbd>F8</kbd> modifier le paramètre suivant :

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

La valeur par défaut est `true` à des fins d’accessibilité.

N’oubliez pas ce paramètre empêche le focus de modification à la console, même lorsque vous utilisez une commande explicitement les appels pour l’entrée, telles que `Get-Credential`.

## <a name="sql-powershell-examples"></a>Exemples de PowerShell SQL
Pour pouvoir utiliser ces exemples (ci-dessous), vous devez installer le module SQL Server à partir de la [PowerShell Gallery](https://www.powershellgallery.com/packages/SqlServer).

```powershell
Install-Module -Name SqlServer
```

> [!NOTE]
> Avec la version `21.1.18102` et, le `SqlServer` module prend en charge [PowerShell Core](https://github.com/PowerShell/PowerShell) 6.2 et, en plus de Windows PowerShell.

Dans cet exemple, nous utilisons le `Get-SqlInstance` pour obtenir les objets serveur SMO pour ServerA et ServerB.  La valeur par défaut de sortie de cette commande inclut le nom d’Instance, version, Service Pack & niveau de mise à jour CU des instances.

```powershell
Get-SqlInstance -ServerInstance ServerA, ServerB
```

Voici un exemple de ce que la sortie se présente comme :

```
Instance Name             Version    ProductLevel UpdateLevel  HostPlatform HostDistribution
-------------             -------    ------------ -----------  ------------ ----------------
ServerA                   13.0.5233  SP2          CU4          Windows      Windows Server 2016 Datacenter
ServerB                   14.0.3045  RTM          CU12         Linux        Ubuntu
```
Le `SqlServer` module contient un fournisseur appelé `SQLRegistration` qui permet d’accéder par programmation les types de suivant de connexions de SQL Server enregistrées :

+ Serveur de moteur de base de données (serveurs inscrits)
+ Serveur d’administration centrale (CMS)
+ Analysis Services
+ Integration Services
+ Reporting Services

 Dans l’exemple suivant, nous ferons un `dir` (alias pour `Get-ChildItem`) pour obtenir la liste de toutes les instances de SQL Server apparaît dans votre fichier de serveurs inscrits.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse 
```

Voici un exemple de ce que la sortie pourrait ressembler à :

```powershell
Mode Name
---- ----
-    ServerA
-    ServerB
-    localhost\SQL2017
-    localhost\SQL2016Happy
-    localhost\SQL2017
```

Pour de nombreuses opérations qui impliquent une base de données ou d’objets au sein d’une base de données, le `Get-SqlDatabase` applet de commande peut être utilisé.  Si vous fournissez des valeurs à la fois pour le `-ServerInstance` et `-Database` paramètres, que cet objet d’une base de données seront récupérées.  Toutefois, si vous spécifiez uniquement le `-ServerInstance` paramètre, une liste complète de toutes les bases de données sur cette instance sera retournée.

Voici un exemple de ce que la sortie se présente comme :

```
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2017   Normal      336.00 MB   57.01 MB Simple       140 sa
master               Normal        6.00 MB  368.00 KB Simple       140 sa
model                Normal       16.00 MB    5.53 MB Full         140 sa
msdb                 Normal       48.44 MB    1.70 MB Simple       140 sa
PBIRS                Normal      144.00 MB   55.95 MB Full         140 sa
PBIRSTempDB          Normal       16.00 MB    4.20 MB Simple       140 sa
SSISDB               Normal      325.06 MB   26.21 MB Full         140 sa
tempdb               Normal       72.00 MB   61.25 MB Simple       140 sa
WideWorldImporters   Normal         3.2 GB     2.6 GB Simple       130 sa
```

L’exemple suivant utilise le `Get-SqlDatabase` applet de commande pour récupérer une liste de toutes les bases de données sur l’instance de serveur b, puis présente une grille (à l’aide de la `Out-GridView` applet de commande) pour sélectionner les bases de données doivent être sauvegardées.  Une fois que l’utilisateur clique sur le bouton « OK », uniquement les bases de données en surbrillance seront sauvegardées.

```powershell
Get-SqlDatabase -ServerInstance ServerB |
Out-GridView -PassThru |
Backup-SqlDatabase -CompressionOption On
```

Cet exemple, là encore, obtenir une liste de toutes les instances de SQL Server répertoriées dans votre fichier de serveurs inscrits, puis appelle le `Get-SqlAgentJobHistory` qui signale chaque travail de l’Agent SQL ayant échoué depuis minuit, pour chaque instance de SQL Server répertorié.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse |
WHERE {$_.Mode -ne 'd' } |
FOREACH {
    Get-SqlAgentJobHistory -ServerInstance  $_.Name -Since Midnight -OutcomesType Failed
}
```

Dans cet exemple, nous ferons un `dir` (alias pour `Get-ChildItem`) pour obtenir la liste de toutes les instances de SQL Server apparaît dans votre fichier de serveurs inscrits, puis utiliser le `Get-SqlDatabase` pour obtenir une liste des bases de données pour chacun de ces instances.

```powershell
dir 'SQLSERVER:\SQLRegistration\Database Engine Server Group' -Recurse |
WHERE { $_.Mode -ne 'd' } |
FOREACH {
    Get-SqlDatabase -ServerInstance $_.Name
}
```

Voici un exemple de ce que la sortie se présente comme :

```
Name                 Status           Size     Space  Recovery Compat. Owner
                                            Available  Model     Level      
----                 ------           ---- ---------- -------- ------- -----
AdventureWorks2017   Normal      336.00 MB   57.01 MB Simple       140 sa   
master               Normal        6.00 MB  368.00 KB Simple       140 sa   
model                Normal       16.00 MB    5.53 MB Full         140 sa   
msdb                 Normal       48.44 MB    1.70 MB Simple       140 sa   
PBIRS                Normal      144.00 MB   55.95 MB Full         140 sa   
PBIRSTempDB          Normal       16.00 MB    4.20 MB Simple       140 sa   
SSISDB               Normal      325.06 MB   26.21 MB Full         140 sa   
tempdb               Normal       72.00 MB   61.25 MB Simple       140 sa   
WideWorldImporters   Normal         3.2 GB     2.6 GB Simple       130 sa   
```

## <a name="reporting-problems"></a>Signalement des problèmes

Si vous rencontrez des problèmes avec le PowerShell Extension, consultez [la documentation de dépannage](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md) pour plus d’informations sur le diagnostic et de signaler des problèmes.

#### <a name="security-note"></a>Remarque relative à la sécurité

Pour tout problème de sécurité, consultez [ici](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md#note-on-security).

## <a name="contributing-to-the-code"></a>Contribution au Code

Découvrez le [documentation de développement](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md) pour plus d’informations sur la façon de contribuer à cette extension !

## <a name="maintainers"></a>Les chargés de maintenance

- [Keith Hill](https://github.com/rkeithhill) - [@r_keith_hill](http://twitter.com/r_keith_hill)
- [Tyler Leonhardt](https://github.com/tylerl0706) - [@TylerLeonhardt](http://twitter.com/tylerleonhardt)
- [Rob Holt](https://github.com/rjmholt)

## <a name="license"></a>Licence

Cette extension est [concédé sous licence MIT](https://github.com/PowerShell/vscode-powershell/blob/master/LICENSE.txt). Pour plus d’informations sur les fichiers binaires tiers qui nous incluons avec les versions de ce projet, consultez le [mentions tierces](https://github.com/PowerShell/vscode-powershell/blob/master/Third%20Party%20Notices.txt) fichier.

## <a name="code-of-conductconduct-md"></a>[Code de conduite][conduct-md]

Ce projet a adopté le [Microsoft Source Code de conduite Open][conduct-code].
Pour plus d’informations, consultez le [Code de conduite Forum aux questions] [ conduct-FAQ] ou contactez [ opencode@microsoft.com ] [ conduct-email] avec des questions ou commentaires supplémentaires.

[conduct-code]: http://opensource.microsoft.com/codeofconduct/
[conduct-FAQ]: http://opensource.microsoft.com/codeofconduct/faq/
[conduct-email]: mailto:opencode@microsoft.com
[conduct-md]: https://github.com/PowerShell/vscode-powershell/blob/master/CODE_OF_CONDUCT.md

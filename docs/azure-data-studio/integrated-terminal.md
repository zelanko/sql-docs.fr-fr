---
title: Terminal intégré
titleSuffix: Azure Data Studio
description: En savoir plus sur le terminal intégré dans Azure Data Studio.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 6677119a35d1d51ac8b6563d9bd9b9f32668c273
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63239384"
---
# <a name="integrated-terminal"></a>Terminal intégré

Dans [!INCLUDE[name-sos](../includes/name-sos-short.md)], vous pouvez ouvrir un terminal intégré, initialement en commençant à la racine de votre espace de travail. Cela peut être pratique car vous n’êtes pas obligé de passer de windows ou de modifier l’état d’un terminal pour effectuer une tâche de ligne de commande rapide existant.

Pour ouvrir le terminal :

* Utilisez le **Ctrl +'** raccourci clavier par le caractère accent grave.
* Utilisez le **vue** | **Terminal intégré** commande de menu.
* À partir de la **Palette de commandes** (**Ctrl + Maj + P**), utilisez le **Terminal intégré : activer/désactiver le** commande.

![Terminal Server](media/integrated-terminal/terminal-screen.png)

> [!NOTE]
> Vous pouvez toujours ouvrir un interpréteur de commandes externe avec l’Explorateur de **ouvrir dans l’invite de commande** commande (**ouvrir dans Terminal** sur Mac ou Linux) si vous préférez travailler en dehors de [!INCLUDE[name-sos](../includes/name-sos-short.md)].

## <a name="managing-multiple-terminals"></a>La gestion de plusieurs terminaux

Vous pouvez créer plusieurs terminaux ouverte à différents emplacements et naviguer facilement entre eux. Instances Terminal Server peuvent être ajoutées en appuyant sur l’icône plus (+) dans l’angle supérieur droit de la **TERMINAL** panneau ou en déclenchant le **Ctrl + Maj +'** commande. Cela crée une autre entrée dans la liste déroulante qui peut être utilisée pour passer à l’autre.

![Plusieurs terminaux](media/integrated-terminal/terminal-multiple-instances.png)

Supprimez les instances de terminal en appuyant sur la Corbeille peuvent bouton.

> [!TIP]
> Si vous utilisez plusieurs terminaux largement, vous pouvez ajouter des combinaisons de touches pour la `focusNext`, `focusPrevious` et `kill` commandes décrites dans le [section de combinaisons de touches](#key-bindings) pour permettre la navigation entre eux en utilisant uniquement le clavier.

## <a name="configuration"></a>Configuration

L’interpréteur de commandes utilisé par défaut, `$SHELL` sur Linux et macOS, PowerShell sur Windows 10 et cmd.exe dans les versions antérieures de Windows. Celles-ci peuvent être remplacées manuellement en définissant `terminal.integrated.shell.*` dans [paramètres](settings.md). Arguments peuvent être passés à l’interpréteur de commandes terminal sur Linux et macOS à l’aide du `terminal.integrated.shellArgs.*` paramètres.

### <a name="windows"></a>Windows

Configurez correctement votre interpréteur de commandes sur Windows est une question de localisation de l’exécutable de droite et de la mise à jour le paramètre. Voici une liste des exécutables shell courants et leurs emplacements par défaut :

```json
// 64-bit cmd if available, otherwise 32-bit
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\cmd.exe"
// 64-bit PowerShell if available, otherwise 32-bit
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\WindowsPowerShell\\v1.0\\powershell.exe"
// Git Bash
"terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe"
// Bash on Ubuntu (on Windows)
"terminal.integrated.shell.windows": "C:\\Windows\\sysnative\\bash.exe"
```

> [!NOTE]
> Pour être utilisés comme un terminal intégré, l’exécutable de l’interpréteur de commandes doit être une application console afin que `stdin/stdout/stderr` peuvent être redirigées.

> [!TIP]
> L’interpréteur de commandes terminal intégré s’exécute avec les autorisations de [!INCLUDE[name-sos](../includes/name-sos-short.md)]. Si vous avez besoin exécuter une commande de l’interpréteur de commandes avec élévation de privilèges (administrateur) ou des autorisations différentes, vous pouvez utiliser les utilitaires de plateforme telles que `runas.exe` au sein d’un terminal.

### <a name="shell-arguments"></a>Arguments de l’interpréteur de commandes

Vous pouvez passer des arguments à l’interpréteur de commandes lorsqu’elle est lancée.

Par exemple, pour activer l’interpréteur de commandes en cours d’exécution en tant que connexion shell (qui s’exécute `.bash_profile`), passez la `-l` argument (avec des guillemets doubles) :

```json
// Linux
"terminal.integrated.shellArgs.linux": ["-l"]
```

## <a name="terminal-display-settings"></a>Paramètres d’affichage de Terminal Server

Vous pouvez personnaliser la police terminal intégré et la hauteur de ligne avec les paramètres suivants :

* `terminal.integrated.fontFamily`
* `terminal.integrated.fontSize`
* `terminal.integrated.lineHeight`

## <a id="key-bindings"></a>Combinaisons de touches Terminal

Le **vue : Activer/désactiver Terminal intégré** commande est liée à **Ctrl +'** pour rapidement activer/désactiver le panneau de terminal intégré hors de l’affichage.

Voici les raccourcis clavier pour naviguer rapidement dans le terminal intégré :

Key|Command
---|---
**CTRL +'**| Afficher le terminal intégré
**CTRL + MAJ +'**| Créer nouveau terminal
**Ctrl+Up**|Défilement vers le haut
**Ctrl+Down**|Défiler vers le bas
**Ctrl+PageUp**|Page de défilement précédente
**Ctrl+PageDown**|Défiler d’une page vers le bas
**Ctrl+Home**|Faites défiler vers le haut
**Ctrl+End**|Faites défiler vers le bas
**Ctrl+K**|Désactivez le terminal

Autres commandes de Terminal Server sont disponibles et peuvent être liés à vos raccourcis clavier par défaut.

Celles-ci sont les suivantes :

* `workbench.action.terminal.focus`: Concentrer le terminal. Cela ressemble à activer/désactiver mais concentre le terminal au lieu de masquage, s’il est visible.
* `workbench.action.terminal.focusNext`: Se concentre l’instance suivante de terminal.
* `workbench.action.terminal.focusPrevious`: Se concentre l’instance précédente de terminal.
* `workbench.action.terminal.kill`: Supprimer l’instance actuelle de terminal.
* `workbench.action.terminal.runSelectedText`: Exécuter le texte sélectionné dans l’instance de terminal.
* `workbench.action.terminal.runActiveFile`: Exécutez le fichier actif dans l’instance de terminal.

### <a name="run-selected-text"></a>Exécuter le texte sélectionné

Pour utiliser le `runSelectedText` commande, sélectionner du texte dans un éditeur et exécutez la commande **Terminal : Exécuter le texte sélectionné dans le Terminal Server actives** via la **Palette de commandes** (**Ctrl + Maj + P**). Le terminal tente d’exécuter le texte sélectionné :

![Exécuter le texte sélectionné](media/integrated-terminal/terminal_run_selected.png)

Si aucun texte n’est sélectionné dans l’éditeur active, la ligne qui se trouve le curseur est exécutée dans le terminal.

### <a name="copy--paste"></a>Copier et coller

Les combinaisons de touches pour copier et coller respectez les normes de plateforme :

* Linux : **CTRL + MAJ + C** et **Ctrl + Maj + V**
* Mac : **Cmd + C** et **Cmd + V**
* Windows : **CTRL + C** et **Ctrl + V**

### <a name="find"></a>Rechercher

Le Terminal intégré a des fonctionnalités de recherche de base qui peuvent être déclenchée en **Ctrl + F**.

Si vous souhaitez **Ctrl + F** pour passer à l’interpréteur de commandes au lieu de lancer le widget de rechercher sur Linux et Windows, vous devez supprimer la combinaison de touches comme suit :

```js
{ "key": "ctrl+f", "command": "-workbench.action.terminal.focusFindWidget",
                      "when": "terminalFocus" },
```

### <a name="rename-terminal-sessions"></a>Renommer des sessions Terminal Server

Sessions Terminal intégrées peuvent maintenant être renommées à l’aide de la **Terminal : Renommer** (`workbench.action.terminal.rename`) commande. Le nouveau nom s’affiche dans la liste déroulante de sélection terminal.

### <a name="forcing-key-bindings-to-pass-through-the-terminal"></a>Combinaisons de touches forcés à traverser le terminal

Alors que le focus est dans le terminal intégré, nombreuses combinaisons de touches ne fonctionnent pas, car les séquences de touches sont passés à et consommés par le terminal lui-même. Le `terminal.integrated.commandsToSkipShell` paramètre peut être utilisé pour contourner ce problème. Il contient un tableau de noms de commande dont combinaisons de touches ignorer le traitement par l’interpréteur de commandes et à la place d’être traités par le [!INCLUDE[name-sos](../includes/name-sos-short.md)] système de liaison de clé. Par défaut, cela inclut toutes les combinaisons de touches terminal en plus une sélection combinaisons de touches quelques couramment utilisés.


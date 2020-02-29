---
title: Option preprocess (outil d’administration Distributed Replay) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 9b5012fd-233e-4a25-a2e1-585c63b70502
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 57adcc55cf7b699e5092671fc61eb83278858cb4
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177339"
---
# <a name="preprocess-option-distributed-replay-administration-tool"></a>Option preprocess (outil d'administration Distributed Replay)
  L' [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] outil d’administration Distributed Replay `DReplay.exe`,, est un outil en ligne de commande que vous pouvez utiliser pour communiquer avec le contrôleur Distributed Replay. Cette rubrique décrit l’option de ligne de commande **preprocess** et la syntaxe correspondante.

 L’option **preprocess** initialise l’étape de prétraitement. Lors de cette étape, le contrôleur prépare les données de trace d'entrée pour la relecture sur le serveur cible.

 ![Icône de lien vers une rubrique](../../database-engine/media/topic-link.gif "Icône du lien de rubrique") Pour plus d’informations sur les conventions de syntaxe utilisées par l’outil d’administration, consultez [Conventions de la syntaxe Transact-SQL &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).

## <a name="syntax"></a>Syntaxe

```

      dreplay preprocess [-mcontroller] -iinput_trace_file
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]
```

#### <a name="parameters"></a>Paramètres
 **-m** *contrôleur* spécifie le nom d’ordinateur du contrôleur. Vous pouvez utiliser «`localhost`» ou «`.`» pour désigner l'ordinateur local.

 Si le paramètre **-m** n’est pas spécifié, l’ordinateur local est utilisé.

 **-i** *input_trace_file* spécifie le chemin d’accès complet du fichier de trace d’entrée sur le `D:\Mytrace.trc`contrôleur, tel que. Le paramètre **-i** est obligatoire.

 Si des fichiers de substitution se trouvent dans le même répertoire, ils seront chargés et utilisés automatiquement. Les fichiers doivent suivre la convention d’affectation des noms de substitution de fichier, par exemple : `Mytrace.trc`, `Mytrace_1.trc`, `Mytrace_2.trc`, `Mytrace_3.trc`, ... `Mytrace_n.trc`.

> [!NOTE]
>  Si vous utilisez l'outil d'administration sur un autre ordinateur que le contrôleur, vous devrez copier les fichiers de trace d'entrée vers le contrôleur afin qu'un chemin d'accès local puisse être utilisé pour ce paramètre.

 **-d** *controller_working_dir* spécifie le répertoire sur le contrôleur où le fichier intermédiaire sera stocké. Le paramètre **-d** est obligatoire.

 Les conditions suivantes s'appliquent :

-   Le répertoire doit résider sur le contrôleur.

-   Vous devez spécifier le chemin complet, en commençant par une lettre de lecteur (par exemple, `c:\WorkingDir`).

-   Le chemin d'accès ne doit pas se terminer par une barre oblique inverse «`\`».

-   Les chemins d'accès UNC ne sont pas pris en charge.

 **-c** *Config_file* est le chemin d’accès complet du fichier de configuration de prétraitement ; utilisé pour spécifier l’emplacement du fichier de configuration de prétraitement lorsqu’il est stocké à un autre emplacement. Ce paramètre peut être un chemin d'accès UNC, ou peut résider localement sur l'ordinateur où vous exécutez l'outil d'administration.

 Le paramètre **-c** n’est pas obligatoire si aucun filtrage n’est exigé, ou si vous ne voulez pas modifier la durée d’inactivité maximale.

 Sans le paramètre **-c** , le fichier de configuration de prétraitement par défaut `DReplay.exe.preprocess.config`est utilisé.

 **-f** *status_interval* spécifie la fréquence (en secondes) d’affichage des messages d’État.

 Si **-f** n’est pas spécifié, l’intervalle par défaut est de 30 secondes.

## <a name="examples"></a>Exemples
 Dans cet exemple, l'étape de prétraitement est initialisée avec tous les paramètres par défaut. La valeur `localhost` indique que le service contrôleur s'exécute sur le même ordinateur que l'outil d'administration. Le paramètre *input_trace_file* spécifie l’emplacement des données de trace d’entrée ( `c:\mytrace.trc`). Étant donné qu’aucun filtre de fichier de trace n’est impliqué, le paramètre **-c** doit être spécifié.

```
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir
```

 Dans cet exemple, l'étape de prétraitement est initialisée et un fichier de configuration de prétraitement modifié est spécifié. Contrairement à l’exemple précédent, le paramètre **-c** est utilisé pour pointer sur le fichier de configuration modifié, si vous l’avez stocké dans un emplacement différent. Par exemple :

```
dreplay preprocess -m localhost -i c:\mytrace.trc -d c:\WorkingDir -c c:\DReplay.exe.preprocess.config
```

 Dans le fichier de configuration de prétraitement modifié, une condition de filtre est ajoutée qui exclut les sessions système pendant la relecture distribuée. Le filtre est ajouté en modifiant l'élément `<PreprocessModifiers>` dans le fichier de configuration de prétraitement, `DReplay.exe.preprocess.config`.

 L'exemple suivant montre le fichier de configuration modifié :

```
<?xml version='1.0'?>
<Options>
    <PreprocessModifiers>
        <IncSystemSession>No</IncSystemSession>
        <MaxIdleTime>-1</MaxIdleTime>
    </PreprocessModifiers>
</Options>
```

## <a name="permissions"></a>Autorisations
 Vous devez exécuter l'outil d'administration en tant qu'utilisateur interactif, comme un utilisateur local ou un compte d'utilisateur de domaine. Pour utiliser un compte d'utilisateur local, l'outil d'administration et le contrôleur doivent s'exécuter sur le même ordinateur.

 Pour plus d’informations, voir [Distributed Replay Security](distributed-replay-security.md).

## <a name="see-also"></a>Voir aussi
 [Préparez les données de trace d’entrée](prepare-the-input-trace-data.md) [SQL Server Distributed Replay](sql-server-distributed-replay.md) [configurer Distributed Replay](configure-distributed-replay.md)



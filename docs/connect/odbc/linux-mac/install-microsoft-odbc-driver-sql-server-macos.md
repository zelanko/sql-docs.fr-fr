---
title: Installer Microsoft ODBC Driver for SQL Server (macOS)
description: Découvrez comment installer Microsoft ODBC Driver for SQL Server sur des clients macOS pour permettre la connectivité de base de données.
ms.date: 03/05/2020
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver, installing
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9daa17d8619fa05ac9abf52a768740eb3e223c77
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488517"
---
# <a name="install-the-microsoft-odbc-driver-for-sql-server-macos"></a>Installer Microsoft ODBC Driver for SQL Server (macOS)

Cet article explique comment installer Microsoft ODBC Driver for SQL Server sur macOS. Il contient également des instructions pour les outils en ligne de commande facultatifs pour SQL Server (`bcp` et `sqlcmd`) et les en-têtes de développement unixODBC.

Cet article fournit des commandes pour installer le pilote ODBC à partir de l’interpréteur de commandes bash. Si vous souhaitez télécharger les packages directement, consultez [Télécharger ODBC Driver for SQL Server](../download-odbc-driver-for-sql-server.md).

## <a name="microsoft-odbc-17"></a>Microsoft ODBC 17

Pour installer le pilote Microsoft ODBC 17 pour SQL Server sur macOS, exécutez les commandes suivantes :

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
HOMEBREW_NO_ENV_FILTERING=1 ACCEPT_EULA=Y brew install msodbcsql17 mssql-tools
```

> [!IMPORTANT]
> Si vous avez installé le package `msodbcsql` v17 qui n’a pas été disponible longtemps, vous devez le supprimer avant d’installer le package `msodbcsql17`. Cette opération évitera les conflits. Le package `msodbcsql17` peut être installé côte à côte avec le package `msodbcsql` v13.

## <a name="previous-versions"></a>Versions précédentes

Les sections suivantes fournissent des instructions pour l’installation des versions précédentes du pilote Microsoft ODBC sur macOS.

## <a name="odbc-131"></a><a id="13.1"></a> ODBC 13.1

Utilisez les commandes suivantes pour installer le pilote Microsoft ODBC 13.1 pour SQL Server sur OS X 10.11 (El Capitan) et macOS 10.12 (Sierra) :

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install msodbcsql@13.1.9.2 mssql-tools@14.0.6.0
```

## <a name="driver-files"></a>Fichiers de pilote

Le pilote ODBC sur macOS est constitué des composants suivants :

|Composant|Description|  
|---------------|-----------------|  
|libmsodbcsql.17.dylib ou libmsodbcsql.13.dylib|Fichier de bibliothèque dynamique (`dylib`) contenant l’ensemble des fonctionnalités du pilote. Ce fichier est installé dans `/usr/local/lib/`.|  
|`msodbcsqlr17.rll` ou `msodbcsqlr13.rll`|Fichier de ressources qui accompagne la bibliothèque du pilote. Ce fichier est installé dans `[driver .dylib directory]../share/msodbcsql17/resources/en_US/` pour Driver 17 et dans `[driver .dylib directory]../share/msodbcsql/resources/en_US/` pour Driver 13. | 
|msodbcsql.h|Fichier d’en-tête qui contient toutes les nouvelles définitions nécessaires à l’utilisation du pilote.<br /><br /> **Remarque :**  Vous ne pouvez pas référencer msodbcsql.h et odbcss.h dans le même programme.<br /><br /> msodbcsql.h est installé dans `/usr/local/include/msodbcsql17/` pour Driver 17 et dans `/usr/local/include/msodbcsql/` pour Driver 13. |
|LICENSE.txt|Fichier texte qui contient les termes du contrat de licence utilisateur final. Ce fichier est placé dans `/usr/local/share/doc/msodbcsql17/` pour Driver 17 et dans `/usr/local/share/doc/msodbcsql/` pour Driver 13. |
|RELEASE_NOTES|Fichier texte qui contient les notes de publication. Ce fichier est placé dans `/usr/local/share/doc/msodbcsql17/` pour Driver 17 et dans `/usr/local/share/doc/msodbcsql/` pour Driver 13. |

## <a name="resource-file-loading"></a>Chargement du fichier de ressources

Le pilote doit charger le fichier de ressources pour pouvoir fonctionner. Ce fichier est appelé `msodbcsqlr17.rll` ou `msodbcsqlr13.rll` selon la version du pilote. L’emplacement du fichier `.rll` est relatif à l’emplacement du pilote lui-même (`so` ou `dylib`), comme indiqué dans le tableau ci-dessus. Depuis la version 17.1, le pilote peut aussi essayer de charger le fichier `.rll` à partir du répertoire par défaut si le chargement échoue à partir du chemin d’accès relatif. Le chemin du fichier de ressources par défaut sur macOS est `/usr/local/share/msodbcsql17/resources/en_US/`.

## <a name="troubleshooting"></a>Dépannage

Si vous ne parvenez pas à établir de connexion à SQL Server à l’aide du pilote ODBC, consultez l’article sur la [résolution des problèmes de connexion](known-issues-in-this-version-of-the-driver.md#connectivity).

## <a name="next-steps"></a>Étapes suivantes

Après avoir installé le pilote, vous pouvez essayer l’[exemple d’application ODBC C++](../../odbc/cpp-code-example-app-connect-access-sql-db.md). Pour plus d’informations sur le développement d’applications ODBC, consultez [Développement d’applications](../../../odbc/reference/develop-app/developing-applications.md).

Pour plus d’informations, consultez les [notes de publication](release-notes-odbc-sql-server-linux-mac.md) et la [configuration système requise](system-requirements.md) du pilote ODBC.

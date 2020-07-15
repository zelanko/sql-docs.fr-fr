---
title: Télécharger et installer Azure Data Studio
description: Télécharger et installer Azure Data Studio pour Windows, macOS ou Linux
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.reviewer: maghan
ms.custom: seodec18
ms.date: 6/15/2020
ms.openlocfilehash: 249dfc97acea8228eef1234a41f1510e8b223788
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774684"
---
# <a name="download-and-install-azure-data-studio"></a>Télécharger et installer Azure Data Studio

Azure Data Studio s’exécute sur Windows, macOS et Linux.

Téléchargez et installez la dernière version :

> [!NOTE]
> Si vous effectuez une mise à jour à partir de SQL Operations Studio et que vous souhaitez conserver vos paramètres, raccourcis clavier ou extraits de code, consultez [Déplacer les paramètres utilisateur](#move-user-settings).

|Plateforme|Téléchargement|Date de publication| Version |
|:---|:---|:---|:---|
| Windows | [Programme d’installation utilisateur (recommandé)](https://go.microsoft.com/fwlink/?linkid=2132348)<br>[Programme d’installation système](https://go.microsoft.com/fwlink/?linkid=2132347)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2132518) | 15 juin 2020 | 1.19.0 |
| macOS | [.zip](https://go.microsoft.com/fwlink/?linkid=2132519) | 15 juin 2020 | 1.19.0 |
| Linux | [.deb](https://go.microsoft.com/fwlink/?linkid=2132350)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2132351)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2132349) | 15 juin 2020| 1.19.0 |

Pour plus d’informations sur la dernière version, consultez les [notes de publication](release-notes.md).

## <a name="get-azure-data-studio-for-windows"></a>Obtenir Azure Data Studio pour Windows

Cette version d’Azure Data Studio comprend une expérience Windows Installer standard et un fichier .zip.

Le *programme d’installation utilisateur* est recommandé, car il ne nécessite pas de privilèges administrateur, ce qui simplifie les installations et les mises à niveau. Le programme d’installation utilisateur ne requiert pas de privilèges administrateur, car il se trouve sous votre dossier utilisateur local AppData (LOCALAPPDATA). Le programme d’installation utilisateur fournit également une expérience de mise à jour en arrière-plan plus fluide. Pour plus d’informations, consultez [Configuration utilisateur pour Windows](https://code.visualstudio.com/updates/v1_26#_user-setup-for-windows).

**Programme d' installation utilisateur** (recommandé)

1. Téléchargez et exécutez le programme d’installation *utilisateur* [[!INCLUDE[name-sos](../includes/name-sos-short.md)] pour Windows](https://go.microsoft.com/fwlink/?linkid=2132348).
2. Démarrez l’application [!INCLUDE[name-sos-short](../includes/name-sos-short.md)].

**Programme d’installation système**

1. Téléchargez et exécutez le programme d’installation *système* [[!INCLUDE[name-sos](../includes/name-sos-short.md)] pour Windows](https://go.microsoft.com/fwlink/?linkid=2132347).
2. Démarrez l’application [!INCLUDE[name-sos-short](../includes/name-sos-short.md)].

**Fichier zip**

1. Téléchargez [[!INCLUDE[name-sos](../includes/name-sos-short.md)].zip pour Windows](https://go.microsoft.com/fwlink/?linkid=2132518).
2. Accédez au fichier téléchargé et extrayez-le.
3. Exécutez `\azuredatastudio-windows\azuredatastudio.exe`

## <a name="get-azure-data-studio-for-macos"></a>Obtenir Azure Data Studio pour macOS

1. Téléchargez [[!INCLUDE[name-sos](../includes/name-sos-short.md)] pour macOS](https://go.microsoft.com/fwlink/?linkid=2132519).
2. Pour développer le contenu du fichier zip, double-cliquez dessus.
3. Pour rendre Azure Data Studio disponible dans le *Launchpad*, faites glisser *Azure Data Studio.app* vers le dossier *Applications*.

## <a name="get-azure-data-studio-for-linux"></a>Obtenir Azure Data Studio pour Linux

1. Téléchargez [!INCLUDE[name-sos](../includes/name-sos-short.md)] à l’aide d’un des programmes d’installation ou de l’archive tar.gz :
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2132350)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2132351)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2132349)
1. Pour extraire le fichier et lancer [!INCLUDE[name-sos](../includes/name-sos-short.md)], ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   **Installation Debian :**

   ```bash
   cd ~
   sudo dpkg -i ./Downloads/azuredatastudio-linux-<version string>.deb

   azuredatastudio
   ```

   **Installation rpm :**

   ```bash
   cd ~
   yum install ./Downloads/azuredatastudio-linux-<version string>.rpm

   azuredatastudio
   ```

   **Installation tar.gz :**

   ```bash
   cd ~
   cp ~/Downloads/azuredatastudio-linux-<version string>.tar.gz ~ 
   tar -xvf ~/azuredatastudio-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/azuredatastudio-linux-x64"' >> ~/.bashrc
   source ~/.bashrc
   azuredatastudio
   ```

   > [!NOTE]
   > Sur Debian, Red Hat et Ubuntu, vous pouvez avoir des dépendances manquantes. Utilisez les commandes suivantes pour installer ces dépendances selon votre version de Linux :

   **Debian :**

   ```bash
   sudo apt-get install libunwind8
   ```

   **Redhat :**

   ```bash
   yum install libXScrnSaver
   ```

   **Ubuntu :**

   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```

## <a name="download-insiders-build-of-azure-data-studio"></a>Télécharger la version Insiders d’Azure Data Studio

En général, les utilisateurs doivent télécharger la version stable de Azure Data Studio ci-dessus. Toutefois, si vous souhaitez essayer nos fonctionnalités bêta et nous faire part de vos commentaires, vous pouvez télécharger [une version Insiders de Azure Data Studio.](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-main)

## <a name="uninstall-azure-data-studio"></a>Désinstaller Azure Data Studio

Si vous avez installé [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] avec Windows Installer, désinstallez-le de la même manière que n’importe quelle application Windows.

Si vous avez installé [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] avec un fichier .zip ou une archive, supprimez simplement les fichiers.

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge

Azure Data Studio s’exécute sur Windows, macOS et Linux et est pris en charge sur les plateformes suivantes :

### <a name="windows"></a>Windows

- Windows 10 (64 bits)
- Windows 8.1 (64 bits)
- Windows 8 (64 bits)
- Windows 7 (SP1) (64 bits) - Nécessite [KB2533623](https://www.microsoft.com/download/details.aspx?id=26767)
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2 (64 bits)
- Windows Server 2012 (64 bits)
- Windows Server 2008 R2 (64 bits)

### <a name="macos"></a>macOS

- macOS 10.15 Catalina
- macOS 10.14 Mojave
- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux

- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="recommended-system-requirements"></a>Configuration système recommandée

|             | Cœurs de processeur | Mémoire/RAM |
|:-----------|:---------|:----------|
| Recommandé |     4     |      8 Go    |
|   Minimum   |     2     |      4 Go     |
|             |           |            |

## <a name="check-for-updates"></a>Rechercher les mises à jour

Pour rechercher les dernières mises à jour, cliquez sur l’icône d’engrenage dans le coin inférieur gauche de la fenêtre et cliquez sur **Rechercher les mises à jour**

## <a name="supported-sql-offerings"></a>Produits SQL pris en charge

- Cette version d’Azure Data Studio fonctionne avec toutes les [versions prises en charge de SQL Server 2014 - [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) et offre la prise en charge d’une utilisation des dernières fonctionnalités cloud d’Azure SQL Database et Azure SQL Data Warehouse. Azure Data Studio fournit également l’aperçu en préversion pour Azure SQL Managed Instance.

## <a name="upgrade-from-sql-operations-studio"></a>Mettre à niveau à partir de SQL Operations Studio

Si vous utilisez toujours SQL Operations Studio, vous devez effectuer la mise à niveau vers Azure Data Studio. SQL Operations Studio était le nom de la préversion et de la version d’évaluation d’Azure Data Studio. En septembre 2018, nous avons modifié le nom en [Azure Data Studio](https://cloudblogs.microsoft.com/sqlserver/2018/09/25/azure-data-studio-for-sql-server/) et publié la version de disponibilité générale (GA). Étant donné que SQL Operations Studio n’est plus mis à jour ni pris en charge, nous demandons à tous les utilisateurs de SQL Operations Studio de télécharger la dernière version d’Azure Data Studio pour obtenir les fonctionnalités, les mises à jour de sécurité et les correctifs les plus récents.

Lorsque vous effectuez une mise à niveau de l’ancienne préversion vers la version actuelle d’Azure Data Studio, vous perdrez vos extensions et paramètres actuels. Pour déplacer vos paramètres, suivez les instructions de la section *Déplacer les paramètres utilisateur* :

## <a name="move-user-settings"></a>Déplacer les paramètres utilisateur

Si vous souhaitez déplacer vos paramètres personnalisés, raccourcis clavier ou extraits de code, suivez les étapes ci-dessous. Il est important de le faire si vous effectuez une mise à niveau de SQL Operations Studio vers Azure Data Studio.

*Si vous avez déjà Azure Data Studio ou si vous n’avez jamais installé ou personnalisé SQL Operations Studio, vous pouvez ignorer cette section.*

1. Ouvrez les paramètres en cliquant sur l’engrenage en bas à gauche et en cliquant sur **Paramètres**.

   ![open-settings](./media/download/open-settings.png)

2. Cliquez avec le bouton droit sur l’onglet **Paramètres utilisateur** en haut, puis cliquez sur **Afficher dans l’explorateur**

   ![reveal-in-explorer](./media/download/reveal-in-explorer.png)

3. Copiez tous les fichiers de ce dossier et enregistrez-les dans un emplacement facile à trouver sur votre lecteur local, comme votre dossier Documents.

   ![copy-settings](./media/download/copy-settings.png)

4. Dans votre nouvelle version d’Azure Data Studio, suivez les étapes 1-2, puis, pour l’étape 3, collez le contenu que vous avez enregistré dans le dossier. Vous pouvez également copier manuellement les paramètres, les combinaisons de touches ou les extraits de code dans leurs emplacements respectifs.

5. Si vous remplacez une installation existante, supprimez l’ancien répertoire d’installation avant l’installation afin d’éviter les erreurs de connexion à votre compte Azure pour l’explorateur de ressources.

## <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez l’un des guides de démarrage rapide suivants :

- [Connexion & interrogation de SQL Server](quickstart-sql-server.md)
- [Connexion & interrogation d’Azure SQL Database](quickstart-sql-database.md)
- [Se connecter à et interroger Azure Data Warehouse](quickstart-sql-dw.md)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]

[Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) et [collecte des données d’utilisation](usage-data-collection.md).

---
title: Télécharger et installer Azure Data Studio
description: Téléchargez et installez Azure Data Studio pour Windows, macOS ou Linux. Cet article contient des dates de publication, des numéros de version, la configuration requise et des liens de téléchargement.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: overview
author: yualan
ms.author: alayu
ms.reviewer: maghan
ms.custom: seodec18
ms.date: 10/20/2020
ms.openlocfilehash: b3363e9b5b8872d3a78d7c5c0fa7f70a80c8d6f9
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257363"
---
# <a name="download-and-install-azure-data-studio"></a>Télécharger et installer Azure Data Studio

Azure Data Studio s’exécute sur Windows, macOS et Linux.

Téléchargez et installez la dernière version :

> [!NOTE]
> Si vous effectuez une mise à jour à partir de SQL Operations Studio et que vous souhaitez conserver vos paramètres, raccourcis clavier ou extraits de code, consultez [Déplacer les paramètres utilisateur](#move-user-settings).

|Plateforme|Téléchargement|Date de publication| Version |
|--------|--------|------------|---------|
| Windows | [Programme d’installation utilisateur (recommandé)](https://go.microsoft.com/fwlink/?linkid=2145989)<br>[Programme d’installation système](https://go.microsoft.com/fwlink/?linkid=2145990)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2145864) | 14 octobre 2020 | 1.23.0 |
| macOS | [.zip](https://go.microsoft.com/fwlink/?linkid=2145865) | 14 octobre 2020 | 1.23.0 |
| Linux | [.deb](https://go.microsoft.com/fwlink/?linkid=2146016)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2146015)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2145866) | 14 octobre 2020 | 1.23.0 |

Pour plus d’informations sur la dernière version, consultez les [notes de publication](./release-notes-azure-data-studio.md).

## <a name="get-azure-data-studio-for-windows"></a>Obtenir Azure Data Studio pour Windows

[!INCLUDE [ssms-ads-install](../includes/ssms-azure-data-studio-install.md)]

Cette version d’Azure Data Studio comprend une expérience Windows Installer standard et un fichier .zip.

Nous recommandons le *programme d’installation utilisateur*, car il ne demande pas de privilèges administrateur, ce qui simplifie les installations et les mises à niveau. Le programme d’installation utilisateur ne demande pas de privilèges administrateur, car il se trouve sous votre dossier utilisateur local AppData (LOCALAPPDATA). Le programme d’installation utilisateur fournit également une expérience de mise à jour en arrière-plan plus fluide. Pour plus d’informations, consultez [Configuration utilisateur pour Windows](https://code.visualstudio.com/updates/v1_26#_user-setup-for-windows).

**Programme d' installation utilisateur** (recommandé)

1. Téléchargez et exécutez le programme d’installation [Azure Data Studio *utilisateur* pour Windows](https://go.microsoft.com/fwlink/?linkid=2145989).
2. Démarrez l’application Azure Data Studio.

**Programme d’installation système**

1. Téléchargez et exécutez le programme d’installation [Azure Data Studio *système* pour Windows](https://go.microsoft.com/fwlink/?linkid=2145990).
2. Démarrez l’application Azure Data Studio.

**Fichier zip**

1. Téléchargez le [fichier .zip Azure Data Studio pour Windows](https://go.microsoft.com/fwlink/?linkid=2145864).
2. Accédez au fichier téléchargé et extrayez-le.
3. Exécutez `\azuredatastudio-windows\azuredatastudio.exe`

## <a name="get-azure-data-studio-for-macos"></a>Obtenir Azure Data Studio pour macOS

1. Téléchargez [Azure Data Studio pour macOS](https://go.microsoft.com/fwlink/?linkid=2145865).
2. Pour développer le contenu du fichier zip, double-cliquez dessus.
3. Pour rendre Azure Data Studio disponible dans le *Launchpad*, faites glisser *Azure Data Studio.app* vers le dossier *Applications*.

## <a name="get-azure-data-studio-for-linux"></a>Obtenir Azure Data Studio pour Linux

1. Téléchargez Azure Data Studio pour Linux en utilisant l’un des programmes d’installation ou l’archive tar.gz :
    - [.deb](https://go.microsoft.com/fwlink/?linkid=2146016)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2146015)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2145866)
1. Pour extraire le fichier et lancer Azure Data Studio, ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

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

En général, les utilisateurs doivent télécharger la version stable de Azure Data Studio ci-dessus. Toutefois, si vous souhaitez essayer les fonctionnalités bêta et envoyer vos commentaires, vous pouvez télécharger la [version Insiders d’Azure Data Studio](https://github.com/microsoft/azuredatastudio#try-out-the-latest-insiders-build-from-main).

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge

Azure Data Studio s’exécute sur Windows, macOS et Linux et est pris en charge sur les plateformes suivantes :

### <a name="windows"></a>Windows

- Windows 10 (64 bits)
- Windows 8.1 (64 bits)
- Windows 8 (64 bits)
- Windows 7 (SP1)
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

| Recommandé/Minimum | Cœurs de processeur | Mémoire/RAM |
|---------------------|-----------|------------|
| Recommandé         |     4     |   8 Go     |
|   Minimum           |     2     |   4 Go     |

## <a name="check-for-updates"></a>Rechercher les mises à jour

Pour rechercher les dernières mises à jour, sélectionnez l’icône d’engrenage située en bas à gauche de la fenêtre, puis **Rechercher les mises à jour**.

Les mises à jour d’environnement hors connexion peuvent être appliquées en [installant directement la dernière version](#download-and-install-azure-data-studio) sur une version déjà installée. La désinstallation des versions antérieures d’Azure Data Studio n’est pas nécessaire. Le programme d’installation met à jour une application actuellement installée, le cas échéant.

## <a name="supported-sql-offerings"></a>Produits SQL pris en charge

- Cette version d’Azure Data Studio fonctionne avec toutes les [versions prises en charge de SQL Server 2014 - [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) et offre la prise en charge d’une utilisation des dernières fonctionnalités cloud d’Azure SQL Database et d’Azure Synapse Analytics. Azure Data Studio fournit également l’aperçu en préversion pour Azure SQL Managed Instance.

## <a name="move-user-settings"></a>Déplacer les paramètres utilisateur

Si vous souhaitez déplacer vos paramètres personnalisés, raccourcis clavier ou extraits de code, suivez les étapes ci-dessous. Il est important de le faire si vous effectuez une mise à niveau de SQL Operations Studio vers Azure Data Studio.

*Si vous avez déjà Azure Data Studio ou si vous n’avez jamais installé ou personnalisé SQL Operations Studio, vous pouvez ignorer cette section.*

1. Ouvrez les paramètres en sélectionnant l’engrenage en bas à gauche, puis **Paramètres**.

   ![modifier les paramètres dans Azure Data Studio](./media/download/open-settings.png)

2. Cliquez avec le bouton droit sur l’onglet **Paramètres utilisateur** en haut, puis sélectionnez **Afficher dans l’explorateur**

   ![lancez l’explorateur qui vous permet d’accéder à votre système de fichiers local](./media/download/reveal-in-explorer.png)

3. Copiez tous les fichiers de ce dossier et enregistrez-les dans un emplacement facile à trouver sur votre lecteur local, comme votre dossier Documents.

   ![utilisez les fichiers et copiez-les sur votre emplacement](./media/download/copy-settings.png)

4. Dans votre nouvelle version d’Azure Data Studio, suivez les étapes 1-2, puis, pour l’étape 3, collez le contenu que vous avez enregistré dans le dossier. Vous pouvez également copier manuellement les paramètres, les combinaisons de touches ou les extraits de code dans leurs emplacements respectifs.

5. Si vous remplacez une installation existante, supprimez l’ancien répertoire d’installation avant l’installation afin d’éviter les erreurs de connexion à votre compte Azure pour l’explorateur de ressources.

## <a name="unattended-install-for-windows"></a>Installation sans assistance pour Windows

Vous pouvez également installer Azure Data Studio en utilisant un script d’invite de commandes.

Si vous souhaitez installer Azure Data Studio en arrière-plan sans aucune invite de l’interface graphique utilisateur et que vous êtes sur la plateforme Windows, suivez les étapes ci-dessous.

1. Lancez l’invite de commandes avec des privilèges élevés.

2. Tapez la commande ci-dessous dans l’invite de commandes.

    ```console
    <path where the azuredatastudio-windows-user-setup-x.xx.x.exe file is located> /VERYSILENT /MERGETASKS=!runcode>
    ```

    Exemple :

    ```console
    %systemdrive%\azuredatastudio-windows-user-setup-1.23.0.exe /VERYSILENT /MERGETASKS=!runcode
    ```

    > [!Note]
    > L’exemple fonctionne également avec le fichier du programme d’installation système.
    > 
    > ```console
    > <path where the azuredatastudio-windows-setup-x.xx.x.exe file is located> /VERYSILENT /MERGETASKS=!runcode>
    > ```

    Vous pouvez aussi passer */SILENT* au lieu de */VERYSILENT* pour voir l’interface utilisateur du programme d’installation.

3. Si tout se passe bien, vous pouvez voir Azure Data Studio installé.

## <a name="uninstall-azure-data-studio"></a>Désinstaller Azure Data Studio

Si vous avez installé Azure Data Studio avec Windows Installer, désinstallez-le de la même manière que n’importe quelle application Windows.

Si vous avez installé Azure Data Studio avec un fichier .zip ou une autre archive, supprimez les fichiers.

## <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez l’un des guides de démarrage rapide suivants :

- [Connexion & interrogation de SQL Server](quickstart-sql-server.md)
- [Connexion & interrogation d’Azure SQL Database](quickstart-sql-database.md)
- [Se connecter à et interroger Azure Data Warehouse](quickstart-sql-dw.md)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]

[Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) et [collecte des données d’utilisation](usage-data-collection.md).

---
title: Téléchargez et installez Azure Data Studio | Microsoft Docs
description: Télécharger et installer Azure Data Studio pour Windows, macOS ou Linux
ms.custom: tools|sos
ms.date: 11/06/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f177b7756a1afc7d28f4f3bd85ac46c1f7563cbe
ms.sourcegitcommit: 6c9d35d03c1c349bc82b9ed0878041d976b703c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51217807"
---
# <a name="download-and-install-azure-data-studio"></a>Téléchargez et installez Azure Data Studio

[!INCLUDE[name-sos](../includes/name-sos.md)] s’exécute sur Windows, macOS et Linux.

Téléchargez et installez la dernière version, le *novembre Release*:

> [!NOTE]
> Si vous mettez à jour à partir de SQL Operations Studio et que vous souhaitez conserver vos paramètres, raccourcis clavier ou des extraits de code, consultez [déplacer les paramètres de l’utilisateur](#move-user-settings).

|Plateforme|Télécharger|Date de publication| Version |
|:---|:---|:---|:---|
|Windows|[Programme d’installation](https://go.microsoft.com/fwlink/?linkid=2038320)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=2038323)|6 novembre 2018 |1.2.4|
|macOS|[.zip](https://go.microsoft.com/fwlink/?linkid=2038327)|6 novembre 2018 |1.2.4|
|Linux|[.DEB](https://go.microsoft.com/fwlink/?linkid=2038405)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=2038401)<br>[.tar.gz](https://go.microsoft.com/fwlink/?linkid=2038332)|6 novembre 2018 |1.2.4|

Pour plus d’informations sur la dernière version, consultez le [notes de version](release-notes.md).

## <a name="get-azure-data-studio-for-windows"></a>Obtenir des données Azure Studio pour Windows

Cette version de [!INCLUDE[name-sos](../includes/name-sos-short.md)] inclut une expérience de programme d’installation Windows standard et un fichier zip : 

**Programme d’installation**

1. Téléchargez et exécutez le [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] programme d’installation pour Windows](https://go.microsoft.com/fwlink/?linkid=2038320).
1. Démarrer le [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] application.


**Fichier zip**

1. Télécharger [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] .zip pour Windows](https://go.microsoft.com/fwlink/?linkid=2038323).
2. Recherchez le fichier téléchargé et extrayez-le.
3. Exécutez `\azuredatastudio-windows\azuredatastudio.exe`


## <a name="get-azure-data-studio-for-macos"></a>Obtenir un Studio de données Azure pour macOS

1. Télécharger [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour macOS](https://go.microsoft.com/fwlink/?linkid=2038327).
2. Pour développer le contenu du fichier zip, double-cliquez dessus.
3. Pour rendre [!INCLUDE[name-sos](../includes/name-sos-short.md)] disponibles dans le *Launchpad*, faites glisser *Studio.app de données Azure* à la *Applications* dossier.


## <a name="get-azure-data-studio-for-linux"></a>Obtenir un Studio de données Azure pour Linux

1. Télécharger [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour Linux à l’aide d’un des programmes d’installation ou de l’archive tar.gz :
    - [.DEB](https://go.microsoft.com/fwlink/?linkid=2038405)
    - [.rpm](https://go.microsoft.com/fwlink/?linkid=2038401)
    - [.tar.gz](https://go.microsoft.com/fwlink/?linkid=2038332)
1. Pour extraire le fichier et le lancement [!INCLUDE[name-sos](../includes/name-sos-short.md)], ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   **Installation de Debian :**
   ```bash
   cd ~
   sudo dpkg -i ./Downloads/azuredatastudio-linux-<version string>.deb

   azuredatastudio
   ```

   **tours/minute d’Installation :**
   ```bash
   cd ~
   yum install ./Downloads/azuredatastudio-linux-<version string>.rpm

   azuredatastudio
   ```

   **TAR.gz Installation :**
   ```bash 
   cd ~ 
   cp ~/Downloads/azuredatastudio-linux-<version string>.tar.gz ~ 
   tar -xvf ~/azuredatastudio-linux-<version string>.tar.gz 
   echo 'export PATH="$PATH:~/azuredatastudio-linux-x64"' >> ~/.bashrc
   source ~/.bashrc 
   azuredatastudio 
   ``` 

   > [!NOTE]
   > Sur Ubuntu, Red Hat et Debian, vous pouvez avoir de dépendances manquantes. Utilisez les commandes suivantes pour installer ces dépendances selon votre version de Linux :
   

   **Debian :** 
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


## <a name="uninstall-azure-data-studio"></a>Désinstaller Studio de données Azure

Si vous avez installé [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] à l’aide du programme d’installation de Windows, puis désinstaller de la même manière que n’importe quelle application Windows.

Si vous avez installé [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] avec un fichier ZIP ou autres archive, puis supprimez simplement les fichiers.

## <a name="supported-operating-systems"></a>Systèmes d'exploitation pris en charge

[!INCLUDE[name-sos](../includes/name-sos-short.md)] s’exécute sur Windows, macOS et Linux et est pris en charge sur les plateformes suivantes :

### <a name="windows"></a>Windows
- Windows 10 (64 bits)
- Windows 8.1 (64 bits)
- Windows 8 (64 bits)
- Nécessite Windows 7 (SP1) (64 bits) - [KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767)
- Windows Server 2016
- Windows Server 2012 R2 (64 bits)
- Windows Server 2012 (64 bits)
- Windows Server 2008 R2 (64 bits)

### <a name="macos"></a>macOS
- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04

## <a name="recommended-system-requirements"></a>Configuration système recommandée
Pour une expérience optimale, utilisez la configuration système recommandée.

|             | Cœurs de processeur | Mémoire/RAM |
|:-----------:|:---------:|:----------:|
| Recommandation |     4     |      8     |
|   Minimum   |     2     |      4     |
|             |           |            |

## <a name="check-for-updates"></a>Rechercher des mises à jour
Pour vérifier les dernières mises à jour, cliquez sur l’icône d’engrenage dans la coin inférieur gauche de la fenêtre et cliquez sur **vérifier les mises à jour**

## <a name="supported-sql-offerings"></a>Produits SQL pris en charge

* Cette version de Azure Data Studio fonctionne avec toutes les [prise en charge des versions de SQL Server 2014 - [!INCLUDE [sql-server-2019](..\includes\sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) et prend en charge pour l’utilisation avec les dernières fonctionnalités de cloud dans Azure SQL Database et Azure SQL Data Warehouse. Azure Data Studio offre également la prise en charge de la version préliminaire de Azure SQL Managed Instance.

## <a name="move-user-settings"></a>Déplacer les paramètres de l’utilisateur

Si vous souhaitez déplacer vos paramètres personnalisés, les raccourcis clavier ou les extraits de code, suivez les étapes ci-dessous. Il est important de faire si vous mettez à niveau à partir de la version de SQL Operations Studio à Azure Data Studio.

*Si vous avez déjà Azure Data Studio, ou vous n’avez jamais installé ou personnalisé SQL Operations Studio, vous pouvez ignorer cette section.*


1. Ouvrir les paramètres en cliquant sur l’engrenage en bas à gauche sur **paramètres.**

   ![Open-paramètres](./media/download/open-settings.png)

2. Cliquez sur le **paramètres utilisateur** onglet en haut et cliquez sur **révéler dans l’Explorateur**

   ![révéler dans l’Explorateur](./media/download/reveal-in-explorer.png)

3. Copiez tous les fichiers dans ce dossier et enregistrez dans un facile à trouver un emplacement sur votre disque local, comme votre dossier Documents.

   ![paramètres de copie](./media/download/copy-settings.png)

4. Dans la nouvelle version d’Azure Data Studio, suivez les étapes 1-2, puis dans l’étape 3 coller le contenu que vous avez enregistré dans le dossier. Vous pouvez également copier manuellement sur les paramètres, combinaisons de touches ou des extraits de code dans leurs emplacements respectifs.

5. Si vous remplacez une installation existante, supprimez l’ancien répertoire d’installation avant l’installation afin d’éviter les erreurs de connexion à votre compte Azure pour l’Explorateur de ressources.

## <a name="next-steps"></a>Étapes suivantes

Consultez les Démarrages rapides suivants pour commencer :
- [Connexion & interrogation de SQL Server](quickstart-sql-server.md)
- [Connexion & interrogation de base de données SQL Azure](quickstart-sql-database.md)
- [Connexion & interrogation d’entrepôt de données Azure](quickstart-sql-dw.md)

Contribuer à [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/azuredatastudio](https://github.com/Microsoft/azuredatastudio) 

[Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) et [collecte des données d’utilisation](usage-data-collection.md).

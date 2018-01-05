---
title: "Téléchargez et installez Microsoft SQL Studio Operations (version préliminaire) | Documents Microsoft"
description: "Téléchargez et installez Microsoft SQL opérations Studio (version préliminaire) pour Windows, Mac OS ou Linux"
ms.custom: tools|sos
ms.date: 12/19/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3a34a03b447e26f072b6c8064cd115333600fef4
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="download-and-install-sql-operations-studio-preview"></a>Téléchargez et installez Studio des opérations SQL (version préliminaire)

[!INCLUDE[name-sos](../includes/name-sos.md)]s’exécute sur Windows, Mac OS et Linux.

Téléchargez et installez la dernière version, le *préliminaire de décembre*:

|Plateforme|Télécharger|Date de publication|
|:---|:---|:---|
|Windows|[Programme d’installation](https://go.microsoft.com/fwlink/?linkid=865305)<br>[.zip](https://go.microsoft.com/fwlink/?linkid=865304)|19 décembre 2017 |
|MacOS|[.zip](https://go.microsoft.com/fwlink/?linkid=865306)|19 décembre 2017 |
|Linux|[.DEB](https://go.microsoft.com/fwlink/?linkid=865308)<br>[.rpm](https://go.microsoft.com/fwlink/?linkid=865309)<br>[. tar.gz](https://go.microsoft.com/fwlink/?linkid=865307)|19 décembre 2017|

Pour plus d’informations sur la dernière version, consultez le [notes de publication](release-notes.md).

## <a name="get-sql-operations-studio-preview-for-windows"></a>Obtenir des opérations de SQL Studio (version préliminaire) pour Windows

Cette version de [!INCLUDE[name-sos](../includes/name-sos-short.md)] inclut une expérience de programme d’installation Windows standard et un fichier zip : 

**Programme d’installation**

1. Téléchargez et exécutez le [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] programme d’installation de Windows](https://go.microsoft.com/fwlink/?linkid=865305).
1. Démarrer le [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] application.


**fichier .zip**

1. Télécharger [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] .zip pour Windows](https://go.microsoft.com/fwlink/?linkid=865304).
2. Recherchez le fichier téléchargé et extrayez-le.
3. Exécutez `\sqlops-windows\sqlops.exe`


## <a name="get-sql-operations-studio-preview-for-macos"></a>Obtenir des opérations de SQL Studio (version préliminaire) pour Mac OS

1. Télécharger [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour macOS](https://go.microsoft.com/fwlink/?linkid=865306).
2. Pour développer le contenu du fichier zip, double-cliquez dessus.
3. Pour rendre [!INCLUDE[name-sos](../includes/name-sos-short.md)] disponibles dans le *Launchpad*, faites glisser *sqlops.app* à la *Applications* dossier.


## <a name="get-sql-operations-studio-preview-for-linux"></a>Obtenir des opérations de SQL Studio (version préliminaire) pour Linux

1. Télécharger [ [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour Linux](https://go.microsoft.com/fwlink/?linkid=865307).
1. Pour extraire le fichier et le lancement [!INCLUDE[name-sos](../includes/name-sos-short.md)], ouvrez une nouvelle fenêtre de Terminal et tapez les commandes suivantes :

   ```bash
   cd ~
   cp ~/Downloads/sqlops-linux-<version string>.tar.gz ~
   tar -xvf ~/sqlops-linux-<version string>.tar.gz
   echo 'export PATH="$PATH:~/sqlops-linux-x64"' >> ~/.bashrc
   source ~/.bashrc
   sqlops
   ```

   > [!NOTE]
   > Sur Ubuntu et Redhat, vous pouvez avoir de dépendances manquantes. Pour installer ces dépendances selon votre version de Linux, utilisez les commandes suivantes :
   
   **Ubuntu :** 
   ```bash
   sudo apt-get install libxss1

   sudo apt-get install libgconf-2-4

   sudo apt-get install libunwind8
   ```

   **Redhat :** 
   ```bash
   yum install libXScrnSaver
   ```

## <a name="uninstall-sql-operations-studio-preview"></a>Désinstaller SQL opérations Studio (version préliminaire)

Si vous avez installé [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] à l’aide de Windows installer, désinstaller puis de la même manière que n’importe quelle application Windows.

Si vous avez installé [!INCLUDE[name-sos-short](../includes/name-sos-short.md)] avec un fichier ZIP ou autre archive, puis supprimez simplement les fichiers.

## <a name="supported-operating-systems"></a>Systèmes d'exploitation pris en charge

[!INCLUDE[name-sos](../includes/name-sos-short.md)]s’exécute sur Windows, Mac OS et Linux et est pris en charge sur les plateformes suivantes :

### <a name="windows"></a>Windows
- Windows 10 (64 bits)
- Windows 8.1 (64 bits)
- Windows 8 (64 bits)
- Windows 7 (SP1) (64 bits) - nécessite [KB2533623](https://www.microsoft.com/en-us/download/details.aspx?id=26767)
- Windows Server 2016
- Windows Server 2012 R2 (64 bits)
- Windows Server 2012 (64 bits)
- Windows Server 2008 R2 (64 bits)

### <a name="macos"></a>MacOS
- macOS 10.13 High Sierra
- macOS 10.12 Sierra

### <a name="linux"></a>Linux
- Red Hat Enterprise Linux 7.4
- Red Hat Enterprise Linux 7.3
- SUSE Linux Enterprise Server v12 SP2
- Ubuntu 16.04



## <a name="next-steps"></a>Next Steps

Consultez une des Démarrages rapides suivants pour commencer :
- [Se connecter et de requêtes SQL Server](quickstart-sql-server.md)
- [Se connecter et interroger la base de données SQL Azure](quickstart-sql-database.md)
- [Connecter la re & quête d’entrepôt de données Azure](quickstart-sql-dw.md)

Contribuer à [!INCLUDE[name-sos](../includes/name-sos-short.md)]:
- [https://github.com/Microsoft/sqlopsstudio](https://github.com/Microsoft/sqlopsstudio) 

[Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839) et [collecte des données d’utilisation](usage-data-collection.md).

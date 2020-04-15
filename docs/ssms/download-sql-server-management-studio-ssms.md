---
title: Télécharger SQL Server Management Studio (SSMS)
description: Télécharger la dernière version de SQL Server Management Studio (SSMS)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
keywords:
- installer ssms, télécharger ssms, dernière version de ssms
- SQL Server Management Studio
- ssms.exe
- sql man studio
- sql management studio
- installation de sql management studio
- télécharger sql management studio
- ms sql management studio
- installer sql management studio
- ssms download
- sql server ssms
- ssms express
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
author: dnethi
ms.author: dinethi
ms.reviewer: sstein, maghan
ms.custom: seo-lt-2019
ms.date: 04/07/2020
ms.openlocfilehash: 5eb94f5755ee0f707ed753140633f923fad4d61b
ms.sourcegitcommit: 7ed12a64f7f76d47f5519bf1015d19481dd4b33a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80873145"
---
# <a name="download-sql-server-management-studio-ssms"></a>Télécharger SQL Server Management Studio (SSMS)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md.md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

SQL Server Management Studio (SSMS) est un environnement intégré pour la gestion des infrastructures SQL, de SQL Server à Azure SQL Database. SSMS fournit des outils permettant de configurer, de superviser et d’administrer des instances de SQL Server et des bases de données. Utilisez SSMS pour déployer, superviser et mettre à niveau les composants de la couche Données utilisés par vos applications, ainsi que pour créer des requêtes et des scripts.

Utilisez SSMS pour interroger, concevoir et gérer vos bases de données et entrepôts de données, où qu’ils se trouvent (sur votre ordinateur local ou dans le cloud).

SSMS est gratuit !

## <a name="download-ssms"></a>Télécharger SSMS

**[![télécharger](media/download-icon.png) Télécharger SQL Server Management Studio (SSMS)](https://aka.ms/ssmsfullsetup)**

SSMS 18.5 est la dernière version en disponibilité générale de SSMS. Si une version précédente de SSMS 18 en disponibilité générale est déjà installée, l’installation de SSMS 18.5 la met à niveau vers 18.5.

### <a name="version-information"></a>Informations sur la version

- Numéro de version : 18.5  
- Numéro de build : 15.0.18330.0  
- Date de publication : 7 avril 2020  

Si vous avez des commentaires ou des suggestions, ou si vous souhaitez signaler des problèmes, la meilleure façon de contacter l’équipe SSMS est de passer par [UserVoice](https://aka.ms/sqlfeedback).

L’installation de SSMS 18.x ne met pas à niveau ni ne remplace les versions 17.x ou antérieures de SSMS. SSMS 18.x s’installe côte à côte avec les versions précédentes pour que vous puissiez utiliser les deux versions. Toutefois, si vous disposez d’une ***préversion*** de SSMS 18.x, vous devez la **désinstaller** avant d’installer SSMS 18.5. Pour savoir si vous disposez de la *préversion*, accédez à la fenêtre À propos sous Aide.

Si un ordinateur contient des installations côte à côte de SSMS, vérifiez que vous démarrez la version correcte adaptée à vos besoins spécifiques. La version la plus récente s’intitule **Microsoft SQL Server Management Studio 18**

> [!Note]
> Si vous accédez à cette page à partir d’une version autre que l’anglais et que vous souhaitez voir le contenu le plus à jour, consultez la [version anglaise (États-Unis) du site](https://aka.ms/downloadssmsusenglish). Vous pouvez télécharger différentes langues à partir du site en version anglaise (États-Unis) en sélectionnant [Langues disponibles](#available-languages).

## <a name="available-languages"></a>Langues disponibles

Cette version de SSMS peut être installée dans les langues suivantes :

SQL Server Management Studio 18.5 :  
[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2125901&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2125901&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2125901&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2125901&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2125901&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2125901&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2125901&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2125901&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2125901&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2125901&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2125901&clcid=0x40a)

> [!NOTE]
> Le module SQL Server PowerShell est une installation distincte que vous pouvez effectuer via PowerShell Gallery. Pour plus d'informations, consultez la page [Télécharger le module SQL Server PowerShell](download-sql-server-ps-module.md).

## <a name="whats-new"></a>Nouveautés

Pour plus d’informations, notamment sur les nouveautés de cette version, consultez les [notes de publication de SSMS](release-notes-ssms.md).

Il existe quelques [problèmes connus](release-notes-ssms.md#known-issues-185) dans cette version.

## <a name="previous-versions"></a>Versions précédentes

Cet article s’applique à la dernière version de SSMS uniquement. Pour télécharger des versions précédentes de SSMS, consultez [Versions précédentes de SSMS](../ssms/release-notes-ssms.md#previous-ssms-releases).

## <a name="unattended-install"></a>Installation sans assistance

Vous pouvez également installer SSMS en utilisant un script d’invite de commandes.

Si vous voulez installer SSMS en arrière-plan sans invite de l’interface utilisateur graphique, suivez les étapes ci-dessous.

1. Lancez l’invite de commandes avec des privilèges élevés.

2. Tapez la commande ci-dessous dans l’invite de commandes.

    ```console
    start "" <path where SSMS-ENU.exe file is located> /Quiet SSMSInstallRoot=<path where you want to install SSMS>
    ```

    Exemple :

    ```console
    start "" %systemdrive%\SSMSfrom\SSMS-Setup-ENU.exe /Quiet SSMSInstallRoot=%systemdrive%\SSMSto
    ```

    Vous pouvez aussi passer */Passive* au lieu de */Quiet* pour voir l’interface utilisateur du programme d’installation.

3. Si tout se passe bien, d’après l’exemple, vous pouvez voir SSMS installé sur « %systemdrive%\SSMSto\Common7\IDE\Ssms.exe ». Si un problème s’est produit, vous pouvez inspecter le code d’erreur retourné et examiner le fichier journal %TEMP%\SSMSSetup.

## <a name="supported-sql-offerings-ssms-185"></a>Offres SQL prises en charge (SSMS 18.5)

- Cette version de SSMS fonctionne avec toutes les [versions prises en charge de SQL Server 2008 - [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) et offre le meilleur niveau de prise en charge pour une utilisation des dernières fonctionnalités cloud d’Azure SQL Database et Azure SQL Data Warehouse.
- Par ailleurs, SSMS 18.x peut être installé côte à côte avec SSMS 17.x, SSMS 16.x ou SSMS SQL Server 2014 et versions antérieures.
- SQL Server Integration Services (SSIS) : SSMS version 17.x ou ultérieure ne prend pas en charge la connexion au service SQL Server Integration Services hérité. Pour vous connecter à une version antérieure du service Integration Services hérité, utilisez la version de SSMS alignée sur la version de SQL Server. Par exemple, utilisez SSMS 16.x pour vous connecter au service SQL Server 2016 Integration Services hérité. SSMS 17.x et SSMS 16.x peuvent être installés côte à côte sur le même ordinateur. Depuis la version de SQL Server 2012, la base de données du catalogue SSIS, SSISDB, est la méthode recommandée pour stocker, gérer, exécuter et surveiller des packages Integration Services. Pour plus d’informations, consultez [Catalogue SSIS](../integration-services/catalog/ssis-catalog.md).

## <a name="supported-operating-systems-ssms-185"></a>Systèmes d’exploitation pris en charge (SSMS 18.5)

Cette version de SSMS prend en charge les plateformes 64 bits suivantes quand elle est utilisée avec le dernier Service Pack :

- Windows 10 (64 bits) <sup>*</sup>
- Windows 8.1 (64 bits)
- Windows Server 2019 (64 bits)
- Windows Server 2016 (64 bits) <sup>*</sup>
- Windows Server 2012 R2 (64 bits)
- Windows Server 2012 (64 bits)
- Windows Server 2008 R2 (64 bits)

<sup>*</sup> Nécessite la version 1607 (10.0.14393) ou ultérieure

> [!NOTE]
> SSMS s’exécute uniquement sur Windows (AMD ou Intel). Si vous avez besoin d’un outil qui s’exécute sur d’autres plateformes que Windows, envisagez Azure Data Studio. Azure Data Studio est un nouvel outil multiplateforme qui s’exécute sur macOS, Linux, ainsi que Windows. Pour plus d’informations, consultez [Azure Data Studio](../azure-data-studio/what-is.md).

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

## <a name="see-also"></a>Voir aussi

- [Tutoriel : SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [Documentation de SQL Server Management Studio](sql-server-management-studio-ssms.md)
- [Dernières mises à jour](../database-engine/install-windows/latest-updates-for-microsoft-sql-server.md)
- [Azure Data Studio](../azure-data-studio/what-is.md)
- [Télécharger la dernière version de SQL Server Data Tools](../ssdt/download-sql-server-data-tools-ssdt.md)
- [Guide d’architecture des données Azure](https://docs.microsoft.com/azure/architecture/data-guide/)

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
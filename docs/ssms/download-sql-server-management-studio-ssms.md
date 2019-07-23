---
title: Télécharger SQL Server Management Studio (SSMS) | Microsoft Docs
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
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
ms.custom: ''
ms.date: 06/12/2019
ms.openlocfilehash: 0841379b0b64ebe81e4a23f76b21f6cf6abe0ec3
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265161"
---
# <a name="download-sql-server-management-studio-ssms"></a>Télécharger SQL Server Management Studio (SSMS)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md.md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

SQL Server Management Studio (SSMS) est un environnement intégré pour la gestion des infrastructures SQL, de SQL Server à Azure SQL Database. SSMS fournit des outils permettant de configurer, de superviser et d’administrer des instances de SQL Server et des bases de données. Utilisez SSMS pour déployer, surveiller et mettre à niveau les composants de la couche Données utilisés par vos applications, mais aussi pour créer des requêtes et des scripts.

Utilisez SSMS pour interroger, concevoir et gérer vos bases de données et entrepôts de données, où qu’ils se trouvent (sur votre ordinateur local ou dans le cloud).

SSMS est gratuit !

## <a name="download-ssms-181"></a>Télécharger SSMS 18.1

**SSMS 18.1 est maintenant disponible, et il s’agit de la nouvelle version de *SQL Server Management Studio* en disponibilité générale (GA), prenant en charge [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]!**

**[![télécharger](../ssdt/media/download.png) Télécharger SQL Server Management Studio 18.1](https://go.microsoft.com/fwlink/?linkid=2094583)**

SSMS 18.1 est la dernière version en disponibilité générale (GA) de SSMS. Si SSMS 18.0 (GA) est installé, l’installation de SSMS 18.1 installe la version 18.1. Si une *préversion* antérieure de SSMS 18.0 est installée, vous devez la désinstaller avant d’installer SSMS 18.1.

**Informations sur la version**

- Numéro de version : 18.1<br>
- Numéro de build : 15.0.18131.0<br>
- Date de publication : 11 juin 2019

Si vous avez des commentaires ou des suggestions, ou si vous souhaitez signaler des problèmes, la meilleure façon de contacter l’équipe SSMS est de passer par [UserVoice](https://aka.ms/sqlfeedback).

L’installation de SSMS 18.x ne met pas à niveau ni ne remplace les versions 17.x ou antérieures de SSMS. SSMS 18.x s’installe côte à côte avec les versions précédentes pour que vous puissiez utiliser les deux versions.

Si un ordinateur contient des installations côte à côte de SSMS, vérifiez que vous démarrez la version adaptée à vos besoins spécifiques. La version la plus récente s’intitule **Microsoft SQL Server Management Studio 18**

## <a name="available-languages-ssms-181"></a>Langues disponibles (SSMS 18.1)

Cette version de SSMS peut être installée dans les langues suivantes :

SQL Server Management Studio 18.1 :<br>
[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2094583&clcid=0x40a)

> [!NOTE]
> Le module SQL Server PowerShell est une installation distincte que vous pouvez effectuer via PowerShell Gallery. Pour plus d'informations, consultez la page [Télécharger le module SQL Server PowerShell](download-sql-server-ps-module.md).

## <a name="new-in-this-release-ssms-181"></a>Nouveautés de cette version (SSMS 18.1)

- **Diagramme de base de données** : les diagrammes de base de données ont été ajoutés dans SSMS. Pour plus d’informations, consultez [Diagrammes de base de données](https://feedback.azure.com/forums/908035/suggestions/37507828).
- **SSBDIAGNOSE. EXE** : l’outil de ligne de commande SQL Server Diagnose a été ajouté dans le package SSMS.
- **Integration Services (SSIS)**  : prise en charge pour la planification du package SSIS, situé dans le catalogue SSIS dans Azure ou le système de fichiers, dans Azure. Il existe trois entrées pour le lancement de la boîte de dialogue Nouvelle planification, l’élément de menu *Nouvelle planification...* affiché lors d’un clic droit sur la package SSIS dans le catalogue SSIS au sein d’Azure, l’élément de menu *Planifier un package SSIS dans Azure* sous l’élément de menu *Migrer vers Azure* sous l’élément de menu *Outils* et « Planifier SSIS dans Azure » affiché lors d’un clic droit sur le dossier Travaux sous l’agent SQL Server de Azure SQL Database Managed Instance.

Pour plus d’informations sur les nouveautés de cette version, voir les [notes de publication de SSMS](release-notes-ssms.md).

## <a name="supported-sql-offerings-ssms-181"></a>Offres SQL prises en charge (SSMS 18.1)

* Cette version de SSMS fonctionne avec toutes les [versions prises en charge de SQL Server 2008 - [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) et offre le meilleur niveau de prise en charge pour une utilisation des dernières fonctionnalités cloud d’Azure SQL Database et Azure SQL Data Warehouse.
* Par ailleurs, SSMS 18.x peut être installé côte à côte avec SSMS 17.x, SSMS 16.x ou SSMS SQL Server 2014 et versions antérieures.
* SQL Server Integration Services (SSIS) : SSMS version 17.x ou ultérieure ne prend pas en charge la connexion au service SQL Server Integration Services hérité. Pour vous connecter à une version antérieure du service Integration Services hérité, utilisez la version de SSMS alignée sur la version de SQL Server. Par exemple, utilisez SSMS 16.x pour vous connecter au service SQL Server 2016 Integration Services hérité. SSMS 17.x et SSMS 16.x peuvent être installés côte à côte sur le même ordinateur. Depuis la version de SQL Server 2012, la base de données du catalogue SSIS, SSISDB, est la méthode recommandée pour stocker, gérer, exécuter et surveiller des packages Integration Services. Pour plus d’informations, consultez [Catalogue SSIS](../integration-services/catalog/ssis-catalog.md).

## <a name="supported-operating-systems-ssms-181"></a>Systèmes d’exploitation pris en charge (SSMS 18.1)

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
> SSMS s’exécute sur Windows uniquement. Si vous avez besoin d’un outil qui s’exécute sur d’autres plateformes que Windows, envisagez Azure Data Studio. Azure Data Studio est un nouvel outil multiplateforme qui s’exécute sur macOS, Linux, ainsi que Windows. Pour plus d’informations, consultez [Azure Data Studio](../azure-data-studio/what-is.md).

## <a name="release-notes-ssms-181"></a>Notes de publication (SSMS 18.1)

Il existe quelques [problèmes connus](release-notes-ssms.md#known-issues-181) dans cette version.

Pour plus d’informations sur cette version, voir les [notes de publication de SSMS](release-notes-ssms.md).

## <a name="previous-ssms-releases"></a>Versions précédentes de SSMS

[Versions antérieures de SQL Server Management Studio](../ssms/release-notes-ssms.md#previous-ssms-releases)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

## <a name="see-also"></a>Voir aussi

- [Tutoriel : SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [Documentation de SQL Server Management Studio](sql-server-management-studio-ssms.md)
- [Service Packs et mises à jour supplémentaires](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [Télécharger SSDT (SQL Server Data Tools)](../ssdt/download-sql-server-data-tools-ssdt.md)

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]

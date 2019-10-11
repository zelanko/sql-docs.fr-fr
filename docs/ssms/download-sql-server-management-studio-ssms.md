---
title: Télécharger SQL Server Management Studio (SSMS) | Microsoft Docs
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: sstein, maghan
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
ms.date: 10/03/2019
ms.openlocfilehash: 3f5b4cbe56d395b88dc756d823b526b05b2fde74
ms.sourcegitcommit: ffb87aa292fc9b545c4258749c28df1bd88d7342
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816803"
---
# <a name="download-sql-server-management-studio-ssms"></a>Télécharger SQL Server Management Studio (SSMS)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md.md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

SQL Server Management Studio (SSMS) est un environnement intégré pour la gestion des infrastructures SQL, de SQL Server à Azure SQL Database. SSMS fournit des outils permettant de configurer, de superviser et d’administrer des instances de SQL Server et des bases de données. Utilisez SSMS pour déployer, superviser et mettre à niveau les composants de la couche Données utilisés par vos applications, ainsi que pour créer des requêtes et des scripts.

Utilisez SSMS pour interroger, concevoir et gérer vos bases de données et entrepôts de données, où qu’ils se trouvent (sur votre ordinateur local ou dans le cloud).

SSMS est gratuit !

## <a name="download-ssms-1831"></a>Télécharger SSMS 18.3.1

**SSMS 18.3.1 est maintenant disponible. Il s’agit de la dernière version de *SQL Server Management Studio* en disponibilité générale qui prend en charge [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].**

**[![Télécharger](../ssdt/media/download.png) Télécharger SQL Server Management Studio 18.3.1](https://go.microsoft.com/fwlink/?linkid=2105412)**

SSMS 18.3.1 est la dernière version en disponibilité générale de SSMS. Si vous avez une précédente version de SSMS 18 en disponibilité générale, l’installation de SSMS 18.3.1 la met à niveau vers 18.3.1. Si vous avez une ancienne version *en préversion* de SSMS 18.x, vous devez la désinstaller avant d’installer SSMS 18.3.1.

**Informations sur la version**

- Numéro de version : 18.3.1  
- Numéro de build : 15.0.18183.0  
- Date de publication : 2 octobre 2019  

Si vous avez des commentaires ou des suggestions, ou si vous souhaitez signaler des problèmes, la meilleure façon de contacter l’équipe SSMS est de passer par [UserVoice](https://aka.ms/sqlfeedback).

L’installation de SSMS 18.x ne met pas à niveau ni ne remplace les versions 17.x ou antérieures de SSMS. SSMS 18.x s’installe côte à côte avec les versions précédentes pour que vous puissiez utiliser les deux versions.

Si un ordinateur contient des installations côte à côte de SSMS, vérifiez que vous démarrez la version correcte adaptée à vos besoins spécifiques. La version la plus récente s’intitule **Microsoft SQL Server Management Studio 18**

## <a name="available-languages-ssms-1831"></a>Langues disponibles (SSMS 18.3.1)

Cette version de SSMS peut être installée dans les langues suivantes :

SQL Server Management Studio 18.3.1 :  
[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2105412&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2105412&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2105412&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2105412&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2105412&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2105412&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2105412&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2105412&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2105412&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2105412&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2105412&clcid=0x40a)

> [!NOTE]
> Le module SQL Server PowerShell est une installation distincte que vous pouvez effectuer via PowerShell Gallery. Pour plus d'informations, consultez la page [Télécharger le module SQL Server PowerShell](download-sql-server-ps-module.md).

## <a name="new-in-this-release-ssms-1831"></a>Nouveautés de cette version (SSMS 18.3.1)

| Nouvel élément | Détails |
|---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Classification des données | Ajout des informations de classification des données à l’interface utilisateur des propriétés de colonne (*Type d’informations*, *ID du type d’informations*, *Étiquette de sensibilité* et *ID de l’étiquette de sensibilité* ne sont pas exposés dans l’interface utilisateur de SSMS). |
| IntelliSense/Éditeur | Mise à jour de la prise en charge des fonctionnalités récemment ajoutées à SQL Server 2019 (par exemple « ALTER SERVER CONFIGURATION »). |
| Integration Services | Ajout d’un nouvel élément du menu de sélection, `Tools > Migrate to Azure > Configure Azure-enabled DTExec`, qui appelle des exécutions de packages SSIS sur Azure-SSIS Integration Runtime en tant qu’activités Exécuter le package SSIS dans des pipelines ADF. |
| SMO/Création de scripts | Ajout de la prise en charge des scripts de contrainte unique Azure SQL DW. |
| SMO/Création de scripts | Classification des données - Ajout de la prise en charge de SQL version 10 (SQL 2008) et ultérieur.  - Ajout d’un nouvel attribut de sensibilité « rang » pour SQL version 15 (SQL 2019) et ultérieur et Azure SQL DB. |

Pour plus d’informations sur les nouveautés de cette version, voir les [notes de publication de SSMS](release-notes-ssms.md).

## <a name="supported-sql-offerings-ssms-1831"></a>Offres SQL prises en charge (SSMS 18.3.1)

- Cette version de SSMS fonctionne avec toutes les [versions prises en charge de SQL Server 2008 - [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) et offre le meilleur niveau de prise en charge pour une utilisation des dernières fonctionnalités cloud d’Azure SQL Database et Azure SQL Data Warehouse.
- Par ailleurs, SSMS 18.x peut être installé côte à côte avec SSMS 17.x, SSMS 16.x ou SSMS SQL Server 2014 et versions antérieures.
- SQL Server Integration Services (SSIS) : SSMS version 17.x ou ultérieure ne prend pas en charge la connexion au service SQL Server Integration Services hérité. Pour vous connecter à une version antérieure du service Integration Services hérité, utilisez la version de SSMS alignée sur la version de SQL Server. Par exemple, utilisez SSMS 16.x pour vous connecter au service SQL Server 2016 Integration Services hérité. SSMS 17.x et SSMS 16.x peuvent être installés côte à côte sur le même ordinateur. Depuis la version de SQL Server 2012, la base de données du catalogue SSIS, SSISDB, est la méthode recommandée pour stocker, gérer, exécuter et surveiller des packages Integration Services. Pour plus d’informations, consultez [Catalogue SSIS](../integration-services/catalog/ssis-catalog.md).

## <a name="supported-operating-systems-ssms-1831"></a>Systèmes d’exploitation pris en charge (SSMS 18.3.1)

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

## <a name="release-notes-ssms-1831"></a>Notes de publication (SSMS 18.3.1)

Il existe quelques [problèmes connus](release-notes-ssms.md#known-issues-1831) dans cette version.

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

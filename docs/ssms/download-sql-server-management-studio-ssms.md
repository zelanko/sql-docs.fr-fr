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
ms.date: 07/26/2019
ms.openlocfilehash: 46174db6dc0008dbeb9490cc96cf41cdef1bc3ed
ms.sourcegitcommit: a1ddeabe94cd9555f3afdc210aec5728f0315b14
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70123106"
---
# <a name="download-sql-server-management-studio-ssms"></a>Télécharger SQL Server Management Studio (SSMS)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md.md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

SQL Server Management Studio (SSMS) est un environnement intégré pour la gestion des infrastructures SQL, de SQL Server à Azure SQL Database. SSMS fournit des outils permettant de configurer, de superviser et d’administrer des instances de SQL Server et des bases de données. Utilisez SSMS pour déployer, superviser et mettre à niveau les composants de la couche Données utilisés par vos applications, ainsi que pour créer des requêtes et des scripts.

Utilisez SSMS pour interroger, concevoir et gérer vos bases de données et entrepôts de données, où qu’ils se trouvent (sur votre ordinateur local ou dans le cloud).

SSMS est gratuit !

## <a name="download-ssms-182"></a>Télécharger SSMS 18.2

**SSMS 18.2 est maintenant disponible. Il s’agit de la nouvelle version de *SQL Server Management Studio* en disponibilité générale (GA) qui prend en charge [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)].**

**[![Télécharger](../ssdt/media/download.png) Télécharger SQL Server Management Studio 18.2](https://go.microsoft.com/fwlink/?linkid=2099720)**

SSMS 18.2 est la dernière version en disponibilité générale (GA) de SSMS. Si une version précédente de SSMS 18 en disponibilité générale est déjà installée, l’installation de SSMS 18.2 entraîne une mise à niveau. Si vous disposez d’une *préversion* antérieure à SSMS 18.x, vous devez la désinstaller avant d’installer SSMS 18.2.

**Informations sur la version**

- Numéro de version : 18.2  
- Numéro de build : 15.0.18142.0  
- Date de publication : 25 juillet 2019  

Si vous avez des commentaires ou des suggestions, ou si vous souhaitez signaler des problèmes, la meilleure façon de contacter l’équipe SSMS est de passer par [UserVoice](https://aka.ms/sqlfeedback).

L’installation de SSMS 18.x ne met pas à niveau ni ne remplace les versions 17.x ou antérieures de SSMS. SSMS 18.x s’installe côte à côte avec les versions précédentes pour que vous puissiez utiliser les deux versions.

Si un ordinateur contient des installations côte à côte de SSMS, vérifiez que vous démarrez la version correcte adaptée à vos besoins spécifiques. La version la plus récente s’intitule **Microsoft SQL Server Management Studio 18**

## <a name="available-languages-ssms-182"></a>Langues disponibles (SSMS 18.2)

Cette version de SSMS peut être installée dans les langues suivantes :

SQL Server Management Studio 18.2 :  
[Chinois (simplifié)](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x804) | [Chinois (traditionnel)](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x404) | [Anglais (États-Unis)](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x409) | [Français](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x40c) | [Allemand](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x407) | [Italien](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x410) | [Japonais](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x411) | [Coréen](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x412) | [Portugais (Brésil)](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x416) | [Russe](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x419) | [Espagnol](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x40a)

> [!NOTE]
> Le module SQL Server PowerShell est une installation distincte que vous pouvez effectuer via PowerShell Gallery. Pour plus d'informations, consultez la page [Télécharger le module SQL Server PowerShell](download-sql-server-ps-module.md).

## <a name="new-in-this-release-ssms-182"></a>Nouveautés de cette version (SSMS 18.2)

|  Nouvel élément  |  Détails  |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Always Encrypted | Mise à jour du fournisseur d’enclave pour prendre en charge l’attestation Azure. |
| IntelliSense/Éditeur | Ajout de la prise en charge de la classification des données  |
| OPTIMIZE_FOR_SEQUENTIAL_KEY | Boîte de dialogue Index SSMS - Ajout d’une nouvelle option d’index OPTIMIZE_FOR_SEQUENTIAL_KEY |
| OPTIMIZE_FOR_SEQUENTIAL_KEY | Ajout de la prise en charge IntelliSense |
| Exécution ou résultats des requêtes | Ajout d’un délai d’achèvement dans les messages à suivre lorsque l’exécution d’une requête donnée est terminée. |
| Exécution ou résultats des requêtes  | Permet d’afficher plus de données (Résultats dans du texte) et d’en stocker davantage dans des cellules (Résultats dans des grilles). SSMS autorise désormais jusqu’à 2 millions de caractères pour ces deux options (auparavant, les limites étaient fixées à 256 000 caractères pour l’affichage et à 64 000 caractères pour le stockage dans des grilles). Cela règle également le problème des utilisateurs qui ne parvenaient pas à extraire plus de 43 680 caractères des cellules d’une grille. |
| ShowPlan | Ajout d’un nouvel attribut dans QueryPlan quand la fonctionnalité UDF scalaire Inline est activée (ContainsInlineScalarTsqlUdfs). |
| Integration Services (SSIS) | Optimisation des performances pour le planificateur de packages SSIS dans Azure. |
|  |  |

Pour plus d’informations sur les nouveautés de cette version, voir les [notes de publication de SSMS](release-notes-ssms.md).

## <a name="supported-sql-offerings-ssms-182"></a>Offres SQL prises en charge (SSMS 18.2)

* Cette version de SSMS fonctionne avec toutes les [versions prises en charge de SQL Server 2008 - [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) et offre le meilleur niveau de prise en charge pour une utilisation des dernières fonctionnalités cloud d’Azure SQL Database et Azure SQL Data Warehouse.
* Par ailleurs, SSMS 18.x peut être installé côte à côte avec SSMS 17.x, SSMS 16.x ou SSMS SQL Server 2014 et versions antérieures.
* SQL Server Integration Services (SSIS) : SSMS version 17.x ou ultérieure ne prend pas en charge la connexion au service SQL Server Integration Services hérité. Pour vous connecter à une version antérieure du service Integration Services hérité, utilisez la version de SSMS alignée sur la version de SQL Server. Par exemple, utilisez SSMS 16.x pour vous connecter au service SQL Server 2016 Integration Services hérité. SSMS 17.x et SSMS 16.x peuvent être installés côte à côte sur le même ordinateur. Depuis la version de SQL Server 2012, la base de données du catalogue SSIS, SSISDB, est la méthode recommandée pour stocker, gérer, exécuter et surveiller des packages Integration Services. Pour plus d’informations, consultez [Catalogue SSIS](../integration-services/catalog/ssis-catalog.md).

## <a name="supported-operating-systems-ssms-182"></a>Systèmes d’exploitation pris en charge (SSMS 18.2)

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

## <a name="release-notes-ssms-182"></a>Notes de publication (SSMS 18.2)

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

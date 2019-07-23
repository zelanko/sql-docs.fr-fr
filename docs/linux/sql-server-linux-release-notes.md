---
title: Notes de publication pour 2017 de SQL Server sur Linux
description: Cette rubrique contient les notes de publication et les fonctionnalités prises en charge pour SQL Server 2017 fonctionnant sous Linux. Les notes de publication sont incluses dans la version la plus récente et plusieurs versions précédentes.
author: VanMSFT
ms.author: vanto
ms.date: 06/25/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.openlocfilehash: 5b6fce0bdde7e320eea0371125a61627652de80d
ms.sourcegitcommit: d667fa9d6f1c8035f15fdb861882bd514be020d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68388412"
---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Notes de publication pour 2017 de SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Les notes de publication suivantes s' [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] appliquent à l’exécution sur Linux. Cet article est divisé en sections pour chaque version. La version GA offre une prise en charge détaillée et des problèmes connus répertoriés. Chaque mise à jour cumulative (CU) ou version de distribution générale (GDR) a un lien vers un article de support décrivant les modifications de CU, ainsi que des liens vers les téléchargements de packages Linux.

> [!TIP]
> Ces notes de publication sont spécifiques [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] aux versions. Pour plus d’informations sur le [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]nouveau, consultez [notes de publication pour SQL Server 2019 Preview sur Linux](sql-server-linux-release-notes-2019.md?view=sql-server-ver15).

## <a name="supported-platforms"></a>Plateformes prises en charge

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Red Hat Enterprise Linux serveur 7,3, 7,4, 7,5 ou 7,6 | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server V12 SP2 | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-suse.md) |
| Ubuntu 16.04 LTS | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-ubuntu.md) | 
| Moteur de l’ordinateur de station d’accueil 1,8 + sur Windows, Mac ou Linux | N/A | [Guide d’installation](quickstart-install-connect-docker.md) | 

> [!TIP]
> Pour plus d’informations, consultez la [Configuration système requise](sql-server-linux-setup.md#system) pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur Linux. Pour obtenir la dernière stratégie de [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]prise en charge pour, consultez la [stratégie de support technique pour Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Outils

La plupart des outils clients existants [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] qui ciblent peuvent [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cibler en toute transparence l’exécution sur Linux. Certains outils peuvent avoir une exigence de version spécifique pour fonctionner correctement avec Linux. Pour obtenir la liste complète [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] des outils, consultez [Outils et utilitaires SQL pour SQL Server](../tools/overview-sql-tools.md).

## <a name="release-history"></a>Historique des versions

Le tableau suivant répertorie l’historique des [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]versions de.

| Libérer               | Version       | Date de publication |
|-----------------------|---------------|--------------|
| [CU15](#CU15)         | 14.0.3162.1   | 2019-05-23   |
| [CU14](#CU14)         | 14.0.3076.1   | 2019-03-25   |
| [CU13](#CU13)         | 14.0.3048.4   | 2018-12-18   |
| [CU12](#CU12)         | 14.0.3045.24  | 2018-10-24   |
| [CU11](#CU11)         | 14.0.3038.14  | 2018-09-20   |
| [CU10](#CU10)         | 14.0.3037.1   | 2018-08-27   |
| [CU9-GDR2](#CU9-GDR2) | 14.0.3035.2   | 2018-08-18   |
| [GDR2](#GDR2)         | 14.0.2002.14  | 2018-08-18   |
| [CU9](#CU9)           | 14.0.3030.27  | 2018-07-18   |
| [CU8](#CU8)           | 14.0.3029.16  | 2018-06-21   |
| [CU7](#CU7)           | 14.0.3026.27  | 2018-05-24   |
| [CU6](#CU6)           | 14.0.3025.34  | 2018-04-19   |
| [CU5](#CU5)           | 14.0.3023.8   | 2018-03-20   |
| [CU4](#CU4)           | 14.0.3022.28  | 2018-02-20   |
| [CU3](#CU3)           | 14.0.3015.40  | 2018-01-03   |
| [GDR1](#GDR1)         | 14.0.2000.63  | 2018-01-03   |
| [CU2](#CU2)           | 14.0.3008.27  | 2017-11-28   |
| [CU1](#CU1)           | 14.0.3006.16  | 2017-10-24   |
| [DISPONIBLE](#GA)             | 14.0.1000.169 | 2017-10-02   |

## <a id="cuinstall"></a>Comment installer des mises à jour

Si vous avez configuré le référentiel Cu (**MSSQL-Server-2017**), vous obtiendrez le dernier cu des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] packages lorsque vous effectuerez de nouvelles installations. Le référentiel cu est la valeur par défaut pour tous les articles d’installation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] de package pour sur Linux. Si vous avez configuré le référentiel GDR (**MSSQL-Server-2017-GDR**), vous obtiendrez uniquement les mises à jour de sécurité critiques publiées depuis la disponibilité générale. Si vous avez besoin de mises à jour du conteneur ou du GDR de l’ancrage, consultez les images officielles pour [Microsoft SQL Server sur Linux pour le moteur de l’ancrage](https://hub.docker.com/r/microsoft/mssql-server). Pour plus d’informations sur la configuration du référentiel, consultez [Source référentiels](sql-server-linux-change-repo.md).

Si vous mettez à jour des [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] packages existants, exécutez la commande de mise à jour appropriée pour chaque package afin d’obtenir le dernier cu. Pour obtenir des instructions de mise à jour spécifiques pour chaque package, consultez les guides d’installation suivants:

- [Installer le package SQL Server](sql-server-linux-setup.md#upgrade)
- [Installer le package de recherche en texte intégral](sql-server-linux-setup-full-text-search.md)
- [Installer SQL Server Integration Services](sql-server-linux-setup-ssis.md)
- [Activer SQL Server Agent](sql-server-linux-setup-sql-agent.md)

## <a id="CU15"></a>CU15 (mai 2019)

Il s’agit de la version de mise à jour cumulative [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]15 (CU15) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3162.1. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/en-us/help/4498951](https://support.microsoft.com/en-us/help/4498951)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3162.1-1 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3162.1-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3162.1-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3162.1-1.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3162.1-1 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3162.1-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3162.1-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3162.1-1.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3162.1-1 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3162.1-1_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3162.1-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3162.1-1_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU14"></a>CU14 (Mar 2019)

Il s’agit de la version de la mise à jour [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]cumulative 14 (CU14) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3076.1. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4484710](https://support.microsoft.com/help/4484710)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3076.1-2 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3076.1-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3076.1-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3076.1-2.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3076.1-2 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3076.1-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3076.1-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3076.1-2.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3076.1-2 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3076.1-2_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3076.1-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3076.1-2_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU13"></a>CU13 (DEC 2018)

Il s’agit de la version de la mise à jour [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]cumulative 13 (CU13) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3048.4. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4466404](https://support.microsoft.com/help/4466404)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3048.4-1 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3048.4-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3048.4-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3048.4-1.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3048.4-1 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3048.4-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3048.4-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3048.4-1.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3048.4-1 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3048.4-1_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3048.4-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3048.4-1_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU12"></a>CU12 (octobre 2018)

Il s’agit de la version de la mise à jour [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]cumulative 12 (CU12) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3045.24. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4464082](https://support.microsoft.com/help/4464082)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3045.24-1 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3045.24-1 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3045.24-1 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3045.24-1_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3045.24-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3045.24-1_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU11"></a>CU11 (septembre 2018)

Il s’agit de la version de la mise à jour [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]cumulative 11 (Cu11) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3038.14. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4462262](https://support.microsoft.com/help/4462262)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3038.14-2 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3038.14-2 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3038.14-2 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3038.14-2_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3038.14-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3038.14-2_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU10"></a>CU10 (août 2018)

Il s’agit de la version mise à jour cumulative 10 [!INCLUDE[ssSQL17](../includes/sssql17-md.md)](CU10) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3037.1. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4342123](https://support.microsoft.com/help/4342123)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3037.1-2 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3037.1-2 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3037.1-2 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3037.1-2_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3037.1-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3037.1-2_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU9-GDR2"></a>CU9-GDR2 (août 2018)

Il s’agit d’une mise à jour de sécurité qui comprend également le CU précédemment [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]publié (CU9) pour. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3035.2. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4293805](https://support.microsoft.com/help/4293805)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3035.2-1 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm)| 
| Package SLES RPM | 14.0.3035.2-1 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3035.2-1 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3035.2-1_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3035.2-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3035.2-1_amd64.deb)<br/> |

## <a id="GDR2"></a>GDR2 (août 2018)

Il s’agit d’une mise à jour de sécurité qui comprend uniquement les correctifs de [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]sécurité GDR2 (et GDR1) pour.  La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.2002.14. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4293803](https://support.microsoft.com/help/4293803)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.2002.14-1 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.2002.14-1 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.2002.14-1 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2002.14-1_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2002.14-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2002.14-1_amd64.deb) |

## <a id="CU9"></a>CU9 (juil 2018)

Il s’agit de la version de la mise à jour [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]cumulative 9 (CU9) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3030.27. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4341265](https://support.microsoft.com/help/4341265)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3030.27-1 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3030.27-1 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3030.27-1 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3030.27-1_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3030.27-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3030.27-1_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU8"></a>CU8 (juin 2018)

Il s’agit de la version de la mise à jour [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]cumulative 8 (CU8) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3029.16. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4338363](https://support.microsoft.com/help/4338363)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3029.16-1 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3029.16-1 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3029.16-1 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3029.16-1_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3029.16-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3029.16-1_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU7"></a>CU7 (mai 2018)

Il s’agit de la version de la mise à jour [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]cumulative 7 (CU7) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3026.27. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4229789](https://support.microsoft.com/help/4229789)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3026.27-2 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3026.27-2 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3026.27-2 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3026.27-2_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3026.27-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3026.27-2_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU6"></a>CU6 (Apr 2018)

Il s’agit de la version de la mise à jour [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]cumulative 6 (CU6) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3025.34. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4101464](https://support.microsoft.com/help/4101464)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3025.34-3 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3025.34-3 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3025.34-3 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU5"></a>CU5 (Mar 2018)

Il s’agit de la version cumulative Update 5 (CU5 [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3023.8. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4092643](https://support.microsoft.com/help/4092643)cette version, consultez.

### <a name="known-upgrade-issue"></a>Problème de mise à niveau connu

Lorsque vous effectuez une mise à niveau à partir d' [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] une version précédente vers CU5, risque de ne pas démarrer avec l’erreur suivante:

```
Error: 4860, Severity: 16, State: 1.
Cannot bulk load. The file "C:\Install\SqlTraceCollect.dtsx" does not exist or you don't have file access rights.
Error: 912, Severity: 21, State: 2.
Script level upgrade for database 'master' failed because upgrade step 'msdb110_upgrade.sql' encountered error 200, state
```

Pour résoudre cette erreur, activez SQL Server agent et redémarrez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec les commandes suivantes:

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
sudo systemctl start mssql-server
```

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3023.8-5 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3023.8-5 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3023.8-5 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3023.8-5_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3023.8-5_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3023.8-5_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU4"></a>CU4 (février 2018)

Il s’agit de la version cumulative Update 4 (CU4 [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3022.28. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4056498](https://support.microsoft.com/help/4056498)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

> [!NOTE]
> À partir de CU4, SQL Server Agent n’est plus installé en tant que package distinct. Il est installé avec le package du moteur et doit être activé pour pouvoir utiliser.

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3022.28-2 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3022.28-2 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3022.28-2 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3022.28-2_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3022.28-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3022.28-2_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GDR1"></a>GDR1 (Jan 2018)

Il s’agit d’une mise à jour de sécurité qui comprend uniquement [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]les correctifs de sécurité GDR1 pour. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.2000.63. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4057122](https://support.microsoft.com/help/4057122)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.2000.63-3 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Package SLES RPM | 14.0.2000.63-3 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.2000.63-3 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2000.63-3_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2000.63-3_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2000.63-3_amd64.deb) |

## <a id="CU3"></a>CU3 (Jan 2018)

Il s’agit de la version cumulative Update 3 (CU3 [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3015.40. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4052987](https://support.microsoft.com/help/4052987)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3015.40-1 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[Package SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3015.40-1 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[Package SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3015.40-1 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3015.40-1_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3015.40-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3015.40-1_amd64.deb)</br>[Package SQL Server Agent Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3015.40-1_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU2"></a>CU2 (novembre 2017)

Il s’agit de la version de la mise à jour [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]cumulative 2 (Cu2) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3008.27. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/4052574](https://support.microsoft.com/help/4052574)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3008.27-1 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Package SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3008.27-1 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Package SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3008.27-1 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3008.27-1_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3008.27-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3008.27-1_amd64.deb)</br>[Package SQL Server Agent Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3008.27-1_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU1"></a>CU1 (octobre 2017)

Il s’agit de la version cumulative update 1 (CU1 [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.3006.16. Pour plus d’informations sur les correctifs et les améliorations de [https://support.microsoft.com/help/KB4053439](https://support.microsoft.com/help/4038634)cette version, consultez.

### <a name="package-details"></a>Détails du package

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant:

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3006.16-3 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Package SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.3006.16-3 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Package SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.3006.16-3 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3006.16-3_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3006.16-3_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3006.16-3_amd64.deb)</br>[Package SQL Server Agent Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3006.16-3_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GA"></a>GA (octobre 2017)

Il s’agit de la version de disponibilité générale ( [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]GA) de. La [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] version de cette version est 14.0.1000.169.

### <a name="package-details"></a>Détails du package

Les détails du package et les emplacements de téléchargement des packages RPM et Debian sont répertoriés dans le tableau suivant. Notez que vous n’avez pas besoin de télécharger ces packages directement si vous suivez les étapes décrites dans les guides d’installation suivants:

- [Installer le package SQL Server](sql-server-linux-setup.md)
- [Installer le package de recherche en texte intégral](sql-server-linux-setup-full-text-search.md)
- [Installer le package SQL Server Agent](sql-server-linux-setup-sql-agent.md)
- [Installer SQL Server Integration Services](sql-server-linux-setup-ssis.md)

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.1000.169-2 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Package SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package SLES RPM | 14.0.1000.169-2 | [package RPM du moteur MSSQL-serveur](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Package SQL Server Agent RPM](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Package Ubuntu 16,04 Debian | 14.0.1000.169-2 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[Package Debian à haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[Package SQL Server Agent Debian](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a name="Unsupported"></a>Fonctionnalités non prises en charge & services

Les fonctionnalités et services suivants ne sont pas disponibles sur Linux au moment de la publication de la mise à la disposition générale. La prise en charge de ces fonctionnalités sera de plus en plus activée dans le temps.

| Domaine | Fonctionnalité ou service non pris en charge |
|-----|-----|
| **Moteur de base de données** | Réplication transactionnelle |
| &nbsp; | Réplication de fusion |
| &nbsp; | Capture de données modifiées (voir SQL Server Agent) |
| &nbsp; | Stretch BD |
| &nbsp; | PolyBase |
| &nbsp; | Requête distribuée avec connexions tierces |
| &nbsp; | Serveurs liés à des sources de données autres que[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  |
| &nbsp; | Procédures stockées étendues système (XP_CMDSHELL, etc.) |
| &nbsp; | Filetable, FILESTREAM |
| &nbsp; | Assemblys CLR avec le jeu d’autorisations EXTERNAL_ACCESS ou unsafe |
| &nbsp; | Buffer Pool Extension |
| **SQL Server Agent** |  Sous-systèmes CmdExec, PowerShell, lecteur de file d’attente, SSIS, SSAS, SSRS |
| &nbsp; | Alertes |
| &nbsp; | l'Agent de lecture du journal ; |
| &nbsp; | Capture de données modifiées (CDC) |
| &nbsp; | Sauvegarde managée |
| **Haute disponibilité** | Mise en miroir de bases de données  |
| **Sécurité** | Gestion de clés extensible |
| &nbsp; | Authentification Active Directory pour les serveurs liés | 
| &nbsp; | Authentification Active Directory pour les groupes de disponibilité (groupes) | 
| &nbsp; | outils AD tiers (Centrify, Vintela, Powerbroker) | 
| **Services** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |
| &nbsp; | Distributed Transaction Coordinator (DTC) |

## <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus avec la version mise à la disposition [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] générale de sur Linux.

#### <a name="general"></a>Généralités

- La longueur du nom d’hôte [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dans lequel est installé doit être inférieure ou égale à 15 caractères. 

    - **Résolution** : Modifiez le nom dans/etc/hostname en lui attribuant une longueur de 15 caractères ou moins.

- La définition manuelle de l’heure système en arrière dans le temps [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] entraînera l’arrêt de la mise à jour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]de l’heure système interne dans.

    - **Résolution** : Redémarrez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].

- Seules les installations d’instance unique sont prises en charge.

    - **Résolution** : Si vous souhaitez avoir plusieurs instances sur un hôte donné, envisagez d’utiliser des machines virtuelles ou des conteneurs d’ancrage. 

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Configuration Manager ne peut pas [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] se connecter à sur Linux.

- La langue par défaut de la connexion **sa** est l’anglais.

    - **Résolution** : Modifiez la langue de la connexion **sa** à l’aide de l’instruction **ALTER LOGIN** .

#### <a name="databases"></a>Bases de données

- Impossible de déplacer la base de données master avec l’utilitaire mssql-conf. Les autres bases de données système peuvent être déplacées avec mssql-conf.

- Lors de la restauration d’une base de données qui [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] a été sauvegardée sur Windows, vous devez utiliser la clause **with Move** dans l’instruction Transact-SQL.

- Les transactions distribuées qui requièrent le service Microsoft Distributed Transaction Coordinator [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ne sont pas prises en charge sur l’exécution sur Linux. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]les [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] serveurs liés sont pris en charge, sauf s’ils impliquent le DTC. Pour plus d’informations, consultez [les transactions distribuées nécessitant le service Microsoft Distributed Transaction Coordinator ne sont pas prises en charge sur les SQL Server s’exécutant sur Linux](https://blogs.msdn.microsoft.com/bobsql/2017/12/11/sql-server-linux-distributed-transactions-requiring-the-microsoft-distributed-transaction-coordinator-service-are-not-supported-on-sql-server-running-on-linux-sql-server-to-sql-server-distributed-tr/).

- Certains algorithmes (suites de chiffrement) pour le protocole TLS (Transport Layer Security) ne [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] fonctionnent pas correctement avec sur Linux. Cela entraîne des échecs de connexion lors d’une tentative [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]de connexion à, ainsi que des problèmes lors de l’établissement de connexions entre les réplicas dans des groupes à haut niveau de disponibilité.

   - **Résolution** : Modifiez le script de configuration **MSSQL. conf** pour [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur Linux afin de désactiver les suites de chiffrement problématiques, en procédant comme suit:

      1. Ajoutez le code suivant à/var/opt/MSSQL/MSSQL.conf.

      ```
      [network]
      tlsciphers= AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-RSA-AES128-GCM-SHA256:!ECDHE-RSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

         >[!NOTE]
         >In the preceding code, `!` negates the expression. This tells OpenSSL to not use the following cipher suite.  

      1. Redémarrez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à l’aide de la commande suivante.

      ```bash
      sudo systemctl restart mssql-server
      ```

- [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]les bases de données sur Windows qui utilisent l’OLTP en mémoire ne peuvent [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] pas être restaurées sur Linux. Pour restaurer une [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] base de données qui utilise l’OLTP en mémoire, commencez par mettre à [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] niveau les bases de données vers ou [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSQL17](../includes/sssql17-md.md)] sur Windows avant de les déplacer vers Linux via la sauvegarde/restauration ou le détachement/attachement.

- L’autorisation User administrer les **opérations en bloc** n’est pas prise en charge sur Linux pour l’instant.

#### <a name="networking"></a>Mise en réseau

Les fonctionnalités qui impliquent des connexions TCP sortantes à partir du processus sqlservr, telles que les serveurs liés ou les groupes de disponibilité, peuvent ne pas fonctionner si les deux conditions suivantes sont réunies:

1. Le serveur cible est spécifié sous la forme d’un nom d’hôte et non d’une adresse IP.

1. L’instance source a IPv6 désactivée dans le noyau. Pour vérifier si votre système a IPv6 activée dans le noyau, les tests suivants doivent être validés :

   - `cat /proc/cmdline`imprime le cmdline de démarrage du noyau actuel. La sortie ne doit pas `ipv6.disable=1`contenir.
   - Le répertoire /proc/sys/net/ipv6/ doit exister.
   - Un programme C qui appelle `socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)` doit fonctionner - syscall doit retourner un fd ! = -1 et n’échoue pas avec EAFNOSUPPORT.

L’erreur exacte dépend de la fonctionnalité Pour les serveurs liés, cela se manifeste en tant qu’une erreur de délai d’attente de connexion. Pour les groupes de disponibilité, le DDL `ALTER AVAILABILITY GROUP JOIN` sur le serveur secondaire échoue après 5 minutes avec une erreur de délai d’attente de téléchargement de la configuration.

Pour contourner ce problème, effectuez l’une des opérations suivantes:

1. Utilisez des adresses IP au lieu de noms d’hôtes pour spécifier la cible de la connexion TCP.

1. Activez IPv6 dans le noyau en supprimant `ipv6.disable=1` de la cmdline de démarrage. La façon de procéder dépend de la distribution Linux et du chargeur de l’appel de procédure, par exemple grub. Si vous ne souhaitez pas que IPv6 soit désactivé, vous pouvez toujours le désactiver en `net.ipv6.conf.all.disable_ipv6 = 1` définissant `sysctl` dans la configuration `/etc/sysctl.conf`(par exemple,). Cela empêchera toujours la carte réseau du système d’obtenir une adresse IPv6, tout en autorisant le fonctionnement des fonctionnalités de sqlservr.

#### <a name="network-file-system-nfs"></a>Network File System (NFS)
Si vous utilisez les partages distants **Network File System (NFS)** en production, notez les exigences de prise en charge suivantes :

- Utiliser la version NFS **4.2 ou ultérieure**. Les versions antérieures de NFS ne gèrent pas les fonctionnalités requises, telles que fallocate et la création de fichier sparse, courantes avec les systèmes de fichiers modernes.
- Positionnez uniquement les répertoires **/var/opt/mssql** sur le montage NFS. D’autres fichiers, tels que [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] les binaires système, ne sont pas pris en charge.
- Assurez-vous que les clients NFS utilisent l’option 'nolock' lorsque qu'ils montent le partage distant.

#### <a name="localization"></a>Localisation

- Si vos paramètres régionaux ne sont pas anglais (fr_FR) lors de l’installation, vous devez utiliser l’encodage UTF-8 dans votre session d’interpréteur de commandes/terminal. Si vous utilisez l’encodage ASCII, vous pouvez voir une erreur semblable au suivant :

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Si vous ne pouvez pas utiliser l’encodage UTF-8, exécutez le programme d’installation à l’aide de la variable d’environnement MSSQL_LCID pour spécifier votre choix de langue.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- Quand vous exécutez le programme d’installation de MSSQL-conf et que vous effectuez [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]une installation non anglaise de, les caractères étendus incorrects sont affichés après le texte localisé «configuration de SQL Server...». Ou, pour les installations non latines, la phrase peut manquer complètement. La phrase manquante doit afficher la chaîne localisée suivante: «Le PID du contrat de licence a été traité avec succès. La nouvelle édition est [\<nom\> édition]». Cette chaîne est générée à titre d’information uniquement et la mise [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] à jour cumulative suivante répond à toutes les langues. Cela n’affecte en rien la réussite de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] l’installation de. 

#### <a name="full-text-search"></a>Recherche en texte intégral

- Tous les filtres ne sont pas disponibles dans cette version, y compris les filtres pour les documents Office. Pour obtenir la liste des filtres pris en charge, consultez [installer SQL Server la recherche en texte intégral sur Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a id="ssis"></a> SQL Server Integration Services (SSIS)

- Le package **MSSQL-Server-is** n’est pas pris en charge sur SUSE dans cette version. Il est actuellement pris en charge sur Ubuntu et sur Red Hat Enterprise Linux (RHEL).

- Avec [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur Linux CTP 2,1 Refresh et versions ultérieures, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] les packages peuvent utiliser des connexions ODBC sur Linux. Cette fonctionnalité a été testée avec [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les pilotes ODBC MySQL, mais elle est également censée fonctionner avec n’importe quel pilote ODBC Unicode qui respecte la spécification ODBC. Au moment de la conception, vous pouvez fournir un nom de source de données ou une chaîne de connexion pour vous connecter aux données ODBC. vous pouvez également utiliser l’authentification Windows. Pour plus d’informations, consultez le billet de [blog annonçant la prise en charge d’ODBC sur Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

- Les fonctionnalités suivantes ne sont pas prises en charge dans cette version lorsque vous exécutez des packages SSIS sur Linux:
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]Base de données de catalogue
  - Exécution de package planifié par l’Agent SQL
  - Authentification Windows
  - Composants tiers
  - Capture de données modifiées (CDC)
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]Scale Out
  - Feature Pack Azure pour SSIS
  - Prise en charge de Hadoop et HDFS
  - Microsoft Connector pour SAP BW

Pour obtenir la liste des composants SSIS intégrés qui ne sont pas actuellement pris en charge, ou qui sont pris en charge avec les limitations, consultez [limitations et problèmes connus pour SSIS sur Linux](sql-server-linux-ssis-known-issues.md#components).

Pour plus d’informations sur SSIS sur Linux, consultez les articles suivants:
-   Billet [de blog annonçant la prise en charge de SSIS pour Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
-   [Installer SQL Server Integration Services (SSIS) sur Linux](sql-server-linux-setup-ssis.md)
-   [Extraire, transformer et charger des données sur Linux avec SSIS](sql-server-linux-migrate-ssis.md)

#### <a id="ssms"></a> SQL Server Management Studio (SSMS)

Les limitations suivantes s’appliquent à [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] sur Windows connecté à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur Linux.

- Les plans de maintenance ne sont pas pris en charge.

- Management Data Warehouse (MDW) et le collecteur de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] données dans ne sont pas pris en charge. 

- [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]Les composants d’interface utilisateur qui ont des options d’authentification Windows ou de journal des événements Windows ne fonctionnent pas avec Linux. Vous pouvez toujours utiliser ces fonctionnalités avec d’autres options, telles que des connexions SQL. 

- Impossible de modifier le nombre de fichiers journaux à conserver.

## <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez les Démarrages rapides suivants:

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécuter sur Docker](quickstart-install-connect-ubuntu.md)
- [Approvisionner une machine virtuelle SQL dans Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)
- [Exécuter et connecter - Cloud](quickstart-install-connect-clouds.md)

Pour obtenir des réponses aux questions fréquemment posées, consultez le [Forum aux questions SQL Server sur Linux](sql-server-linux-faq.md).

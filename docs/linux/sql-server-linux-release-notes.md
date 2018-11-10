---
title: Notes de publication pour 2017 de SQL Server sur Linux | Documents Microsoft
description: Cette rubrique contient les notes de publication et les fonctionnalités prises en charge pour SQL Server 2017 fonctionnant sous Linux. Les notes de publication sont incluses dans la version la plus récente et plusieurs versions précédentes.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/29/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.openlocfilehash: d1163c58933ab4d2b6d7faa8b643a3401d87d530
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51270132"
---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Notes de publication pour 2017 de SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Les notes de publication suivantes s’appliquent à SQL Server 2017 exécuté sur Linux. Cet article est divisé en sections pour chaque version. La disponibilité générale a détaillées prise en charge et problèmes répertoriés connus. Chaque mise à jour cumulative (CU) ou le correctif logiciel grand public (GDR) a un lien vers un article du support technique décrivant les modifications CU, ainsi que des liens vers les téléchargements du package de Linux.

> [!TIP]
> Ces notes de publication sont spécifiquement pour les versions de SQL Server 2017. Pour plus d’informations sur la version préliminaire de SQL Server 2019 nouvelle, consultez [notes de version préliminaire de SQL Server 2019 sur Linux](sql-server-linux-release-notes-2019.md?view=sql-server-ver15).

## <a name="supported-platforms"></a>Plateformes prises en charge

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 ou 7.4 Workstation, Server, et Desktop | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server version 12 SP2 | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-ubuntu.md) | 
| Docker Engine 1.8 + sur Windows, Mac ou Linux | Néant | [Guide d’installation](quickstart-install-connect-docker.md) | 

> [!TIP]
> Pour plus d’informations, consultez le [requise](sql-server-linux-setup.md#system) pour SQL Server sur Linux. Pour la dernière stratégie de prise en charge pour SQL Server 2017, consultez le [politique de support technique pour Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Outils

La plupart des outils clients existants qui ciblent SQL Server peuvent en toute transparence ciblant SQL Server en cours d’exécution sur Linux. Certains outils peuvent avoir une exigence de version spécifique pour fonctionner avec Linux. Pour obtenir une liste complète des outils SQL Server, consultez [SQL outils et utilitaires pour SQL Server](../tools/overview-sql-tools.md).

## <a name="release-history"></a>Historique des versions

Le tableau suivant répertorie l’historique des versions de SQL Server 2017.

| Version               | Version       | Date de publication |
|-----------------------|---------------|--------------|
| [CU12](#CU12)         | 14.0.3045.24  | 2018-10-24   |
| [CU11](#CU11)         | 14.0.3038.14  | 2018-09-20   |
| [CU10](#CU10)         | 14.0.3037.1   | 2018-08-27   |
| [CU9-GDR2](#CU9-GDR2) | 14.0.3035.2   | 2018-08-18   |
| [GDR2](#GDR2)         | 14.0.2002.14  | 2018-08-18   |
| [CU9](#CU9)           | 14.0.3030.27  | 18-07-2018   |
| [CU8](#CU8)           | 14.0.3029.16  | 21-06-2018   |
| [CU7](#CU7)           | 14.0.3026.27  | 2018-05-24   |
| [CU6](#CU6)           | 14.0.3025.34  | 2018-04-19   |
| [CU5](#CU5)           | 14.0.3023.8   | 2018-03-20   |
| [CU4](#CU4)           | 14.0.3022.28  | 2018-02-20   |
| [CU3](#CU3)           | 14.0.3015.40  | 03-01-2018   |
| [GDR1](#GDR1)         | 14.0.2000.63  | 03-01-2018   |
| [CU2](#CU2)           | 14.0.3008.27  | 28 / 11 / 2017   |
| [CU1](#CU1)           | 14.0.3006.16  | 2017-10-24   |
| [DISPONIBILITÉ GÉNÉRALE](#GA)             | 14.0.1000.169 | 2017-10-02   |

## <a id="cuinstall"></a> Comment installer des mises à jour

Si vous avez configuré le référentiel CU (**mssql-server-2017**), vous obtenez les derniers packages CU de SQL Server lorsque vous effectuez de nouvelles installations. Le référentiel CU est la valeur par défaut pour tous les articles d’installation de package pour SQL Server sur Linux. Si vous avez configuré le référentiel GDR (**mssql-server-2017-gdr**), vous obtiendrez uniquement les mises à jour de sécurité critiques publiées depuis la disponibilité générale. Si vous avez besoin de conteneur Docker CU ou mises à jour GDR, consultez les images officielles pour [Microsoft SQL Server sur Linux pour le moteur Docker](https://hub.docker.com/r/microsoft/mssql-server). Pour plus d’informations sur la configuration du référentiel, consultez [Source référentiels](sql-server-linux-change-repo.md).

Si vous mettez à jour des packages SQL Server existants, exécutez la commande de mise à jour appropriée pour chaque package obtenir la dernière version CU. Pour obtenir des instructions de mise à jour spécifique pour chaque package, consultez les guides d’installation suivants :

- [Installer le package SQL Server](sql-server-linux-setup.md#upgrade)
- [Installer le package de recherche en texte intégral](sql-server-linux-setup-full-text-search.md)
- [Installer SQL Server Integration Services](sql-server-linux-setup-ssis.md)
- [Activer l’Agent SQL Server](sql-server-linux-setup-sql-agent.md)

## <a id="CU12"></a> CU12 (octobre 2018)

Il s’agit de la version 12 de mise à jour Cumulative (CU12) de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3045.24. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/en-us/help/4464082 ](https://support.microsoft.com/en-us/help/4464082).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3045.24-1 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.3045.24-1 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.3045.24-1 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3045.24-1_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3045.24-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3045.24-1_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU11"></a> CU11 (septembre 2018)

Il s’agit de la version 11 de mise à jour Cumulative (CU11) de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3038.14. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/en-us/help/4462262 ](https://support.microsoft.com/en-us/help/4462262).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3038.14-2 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.3038.14-2 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.3038.14-2 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3038.14-2_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3038.14-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3038.14-2_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU10"></a> CU10 (août 2018)

Il s’agit de la version à jour Cumulative 10 (CU10) de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3037.1. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/en-us/help/4342123 ](https://support.microsoft.com/en-us/help/4342123).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3037.1-2 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.3037.1-2 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.3037.1-2 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3037.1-2_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3037.1-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3037.1-2_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU9-GDR2"></a> CU9-GDR2 (août 2018)

Il s’agit d’une mise à jour de sécurité qui inclut également le CU précédemment publiée (CU9) pour SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3035.2. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/en-us/help/4293805 ](https://support.microsoft.com/en-us/help/4293805).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3035.2-1 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm)| 
| Package RPM de SLES | 14.0.3035.2-1 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.3035.2-1 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3035.2-1_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3035.2-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3035.2-1_amd64.deb)<br/> |

## <a id="GDR2"></a> GDR2 (août 2018)

Il s’agit d’une mise à jour de sécurité qui inclut uniquement les correctifs de sécurité GDR2 (et GDR1) pour SQL Server 2017.  La version du moteur SQL Server pour cette version est 14.0.2002.14. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/en-us/help/4293803 ](https://support.microsoft.com/en-us/help/4293803).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.2002.14-1 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.2002.14-1 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.2002.14-1 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2002.14-1_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2002.14-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2002.14-1_amd64.deb) |

## <a id="CU9"></a> CU9 (juillet 2018)

Il s’agit de la version de mise à jour Cumulative 9 (CU9) de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3030.27. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/en-us/help/4341265 ](https://support.microsoft.com/en-us/help/4341265).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3030.27-1 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.3030.27-1 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.3030.27-1 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3030.27-1_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3030.27-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3030.27-1_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU8"></a> CU8 (juin 2018)

Il s’agit de la version de mise à jour Cumulative 8 (CU8) de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3029.16. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/en-us/help/4338363 ](https://support.microsoft.com/en-us/help/4338363).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3029.16-1 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.3029.16-1 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.3029.16-1 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3029.16-1_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3029.16-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3029.16-1_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU7"></a> CU7 (mai 2018)

Il s’agit de la version 7 de mise à jour Cumulative (CU7) de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3026.27. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/en-us/help/4229789 ](https://support.microsoft.com/en-us/help/4229789).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3026.27-2 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.3026.27-2 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.3026.27-2 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3026.27-2_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3026.27-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3026.27-2_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU6"></a> CU6 (avril 2018)

Il s’agit de la version 6 de mise à jour Cumulative (CU6) de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3025.34. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/help/4101464 ](https://support.microsoft.com/help/4101464).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3025.34-3 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.3025.34-3 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.3025.34-3 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU5"></a> CU5 (mars 2018)

Il s’agit de la version Cumulative Update 5 (CU5) de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3023.8. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/help/4092643 ](https://support.microsoft.com/help/4092643).

### <a name="known-upgrade-issue"></a>Problème de mise à niveau connu

Lorsque vous mettez à niveau à partir d’une version antérieure à CU5, SQL Server peut échouer démarrer avec l’erreur suivante :

```
Error: 4860, Severity: 16, State: 1.
Cannot bulk load. The file "C:\Install\SqlTraceCollect.dtsx" does not exist or you don't have file access rights.
Error: 912, Severity: 21, State: 2.
Script level upgrade for database 'master' failed because upgrade step 'msdb110_upgrade.sql' encountered error 200, state
```

Pour résoudre cette erreur, activez l’Agent SQL Server et redémarrez SQL Server avec les commandes suivantes :

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
sudo systemctl start mssql-server
```

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3023.8-5 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.3023.8-5 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.3023.8-5 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3023.8-5_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3023.8-5_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3023.8-5_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU4"></a> Cu4 et versions ultérieures (février 2018)

Il s’agit de la version à jour Cumulative 4 (CU4) de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3022.28. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/en-us/help/4056498 ](https://support.microsoft.com/en-us/help/4056498).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

> [!NOTE]
> À compter de cu4 et versions ultérieures, l’Agent SQL Server n’est plus installé comme un lot distinct. Il est installé avec le package de moteur et doit être activé à utiliser.

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3022.28-2 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.3022.28-2 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.3022.28-2 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3022.28-2_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3022.28-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3022.28-2_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GDR1"></a> GDR1 (janvier 2018)

Il s’agit d’une mise à jour de sécurité qui inclut uniquement les GDR1 les correctifs de sécurité pour SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.2000.63. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/en-us/help/4057122 ](https://support.microsoft.com/en-us/help/4057122).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.2000.63-3 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Package RPM de SLES | 14.0.2000.63-3 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.2000.63-3 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2000.63-3_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2000.63-3_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2000.63-3_amd64.deb) |

## <a id="CU3"></a> CU3 (janvier 2018)

Il s’agit de la version à jour Cumulative 3 (CU3) de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3015.40. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/en-us/help/4052987 ](https://support.microsoft.com/en-us/help/4052987).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3015.40-1 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[Package RPM de l’Agent SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.3015.40-1 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[Package RPM de l’Agent SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.3015.40-1 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3015.40-1_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3015.40-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3015.40-1_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3015.40-1_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU2"></a> CU2 (novembre 2017)

Il s’agit de la version à jour Cumulative 2 (CU2) de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3008.27. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/help/4052574 ](https://support.microsoft.com/help/4052574).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3008.27-1 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Package RPM de l’Agent SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.3008.27-1 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[Package RPM de l’Agent SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.3008.27-1 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3008.27-1_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3008.27-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3008.27-1_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3008.27-1_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU1"></a> CU1 (octobre 2017)

Il s’agit de la version à jour Cumulative 1 (CU1) de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.3006.16. Pour plus d’informations sur les correctifs et les améliorations apportées dans cette version, consultez [ https://support.microsoft.com/help/KB4053439 ](https://support.microsoft.com/help/4038634).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.3006.16-3 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Package RPM de l’Agent SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.3006.16-3 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[Package RPM de l’Agent SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.3006.16-3 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3006.16-3_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3006.16-3_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3006.16-3_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3006.16-3_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GA"></a> Disponibilité générale (octobre 2017)

Il s’agit de la version de disponibilité générale de SQL Server 2017. La version du moteur SQL Server pour cette version est 14.0.1000.169.

### <a name="package-details"></a>Détails du package

Détails du package et les emplacements de téléchargement pour les packages RPM et Debian sont répertoriées dans le tableau suivant. Notez que vous n’avez pas besoin de télécharger ces packages directement si vous utilisez les étapes décrites dans les guides d’installation suivants :

- [Installer le package SQL Server](sql-server-linux-setup.md)
- [Installer le package de recherche en texte intégral](sql-server-linux-setup-full-text-search.md)
- [Installer le package de l’Agent SQL Server](sql-server-linux-setup-sql-agent.md)
- [Installer SQL Server Integration Services](sql-server-linux-setup-ssis.md)

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 14.0.1000.169-2 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM de l’Agent SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[Package SSIS](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| Package RPM de SLES | 14.0.1000.169-2 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[Package RPM de l’Agent SQL Server](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Package Debian Ubuntu 16.04 | 14.0.1000.169-2 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[Package Debian de SQL Server Agent](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[Package SSIS](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a name="Unsupported"></a> Services et fonctionnalités non prises en charge

Les fonctionnalités et les services suivants ne sont pas disponibles sur Linux au moment de la disponibilité générale. La prise en charge de ces fonctionnalités est plus en plus activée au fil du temps.

| Domaine | Fonctionnalité non prise en charge ou un service |
|-----|-----|
| **Moteur de base de données** | Réplication transactionnelle |
| &nbsp; | Réplication de fusion |
| &nbsp; | Stretch DB |
| &nbsp; | PolyBase |
| &nbsp; | Requête distribuée avec des connexions 3 rd-party |
| &nbsp; | Serveurs liés aux sources de données autres que SQL Server |
| &nbsp; | Procédures système stockées étendues (XP_CMDSHELL, etc.). |
| &nbsp; | Filetable, FILESTREAM |
| &nbsp; | Définir des assemblys CLR avec l’autorisation EXTERNAL_ACCESS ou UNSAFE |
| &nbsp; | Buffer Pool Extension |
| **SQL Server Agent** |  Sous-systèmes : CmdExec, PowerShell, lecteur de file d’attente, SSIS, SSAS, SSRS |
| &nbsp; | Alertes |
| &nbsp; | l'Agent de lecture du journal ; |
| &nbsp; | Capture de données modifiées |
| &nbsp; | Sauvegarde managée |
| **Haute disponibilité** | Mise en miroir de bases de données  |
| **Sécurité** | Gestion de clés extensible |
| &nbsp; | Authentification Active Directory pour les serveurs liés | 
| &nbsp; | Authentification Active Directory pour les groupes de disponibilité (groupes de disponibilité) | 
| &nbsp; | outils de tiers AD 3e (Centrify, Vintela, Powerbroker) | 
| **Services** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | Data Quality Services |
| &nbsp; | Master Data Services |
| &nbsp; | Coordinateur de transactions distribuées (DTC) |

## <a name="known-issues"></a>Problèmes connus

Les sections suivantes décrivent les problèmes connus avec la version disponibilité générale de SQL Server 2017 sur Linux.

#### <a name="general"></a>Général

- Mises à niveau vers la version en disponibilité générale de SQL Server 2017 sont prises en charge uniquement à partir de CTP 2.1 ou version ultérieure. 

- Le nom d’hôte de l'ordinateur sur lequel SQL Server est installé doit avoir 15 caractères ou moins. 

    - **Résolution**: Remplacez le nom d’hôte dans /etc/hostname avec un nom de 15 caractères ou moins.

- Définition manuelle de l’heure système vers l’arrière dans le temps entraîne SQL Server arrêter la mise à jour de l’heure du système interne dans SQL Server.

    - **Résolution**: redémarrez SQL Server.

- Seules les installations d’instance unique sont prises en charge.

    - **Résolution**: Si vous souhaitez avoir plusieurs instances sur un hôte donné, envisagez d’utiliser des machines virtuelles ou des conteneurs Docker. 

- Le gestionnaire de Configuration SQL Server ne peut pas se connecter à SQL Server sur Linux.

- La langue par défaut de la **sa** connexion est l’anglaise.

    - **Résolution**: modifier la langue de la connexion **sa** avec l'instruction **ALTER LOGIN**.

#### <a name="databases"></a>Bases de données

- Impossible de déplacer la base de données master avec l’utilitaire mssql-conf. Les autres bases de données système peuvent être déplacées avec mssql-conf.

- Lorsque vous restaurez une base de données qui a été sauvegardée sur SQL Server sur Windows, vous devez utiliser la clause **WITH MOVE** dans l’instruction Transact-SQL.

- Nécessiter que le service Microsoft Distributed Transaction Coordinator les transactions distribuées ne sont pas pris en charge sur SQL Server s’exécutant sur Linux. SQL Server vers SQL Server, serveurs liés sont pris en charge, sauf si elles impliquent le DTC. Pour plus d’informations, consultez [nécessiter que le service Microsoft Distributed Transaction Coordinator les transactions distribuées ne sont pas pris en charge sur SQL Server s’exécutant sur Linux](https://blogs.msdn.microsoft.com/bobsql/2017/12/11/sql-server-linux-distributed-transactions-requiring-the-microsoft-distributed-transaction-coordinator-service-are-not-supported-on-sql-server-running-on-linux-sql-server-to-sql-server-distributed-tr/).

- Certains algorithmes (suites de chiffrement) de sécurité TLS (Transport Layer) ne fonctionnent pas correctement avec SQL Server sur Linux. Cela entraîne des échecs de connexion lorsque vous tentez de vous connecter à SQL Server, ainsi que des problèmes de l’établissement de connexions entre les réplicas de groupes de haute disponibilité.

   - **Résolution**: modifier le **mssql.conf** script de configuration pour SQL Server sur Linux pour désactiver les suites de chiffrement problématique, en procédant comme suit :

      1. Ajoutez le code suivant /var/opt/mssql/mssql.conf.

      ```
      [network]
      tlsciphers= AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-RSA-AES128-GCM-SHA256:!ECDHE-RSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

         >[!NOTE]
         >In the preceding code, `!` negates the expression. This tells OpenSSL to not use the following cipher suite.  

      1. Redémarrez SQL Server avec la commande suivante.

      ```bash
      sudo systemctl restart mssql-server
      ```

- Impossible de restaurer les bases de données SQL Server 2014 sur Windows qui utilisent OLTP en mémoire sur SQL Server 2017 sur Linux. Pour restaurer une base de données SQL Server 2014 qui utilise l’OLTP en mémoire, tout d’abord mettre à niveau les bases de données vers SQL Server 2016 ou SQL Server 2017 sur Windows avant de les déplacer vers SQL Server sur Linux par le biais de sauvegarder/restaurer ou attacher et détacher.

- Autorisation utilisateur **ADMINISTER BULK OPERATIONS** n’est pas pris en charge sur Linux pour l’instant.

#### <a name="networking"></a>Réseau

Fonctionnalités qui impliquent des connexions TCP sortantes à partir du processus sqlservr, tels que des serveurs liés ou des groupes de disponibilité, peut ne pas fonctionnent si les deux conditions suivantes sont remplies :

1. Le serveur cible est spécifié comme un nom d’hôte et non une adresse IP.

1. L’instance source a IPv6 désactivée dans le noyau. Pour vérifier si votre système a IPv6 activée dans le noyau, les tests suivants doivent être validés :

   - `cat /proc/cmdline` Imprime la ligne de commande de démarrage du noyau en cours. La sortie ne doit pas contenir `ipv6.disable=1`.
   - Le répertoire /proc/sys/net/ipv6/ doit exister.
   - Un programme C qui appelle `socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)` doit fonctionner - syscall doit retourner un fd ! = -1 et n’échoue pas avec EAFNOSUPPORT.

L’erreur exacte dépend de la fonctionnalité Pour les serveurs liés, cela se manifeste en tant qu’une erreur de délai d’attente de connexion. Pour les groupes de disponibilité, le DDL `ALTER AVAILABILITY GROUP JOIN` sur le serveur secondaire échoue après 5 minutes avec une erreur de délai d’attente de téléchargement de la configuration.

Pour contourner ce problème, effectuez l’une des opérations suivantes :

1. Utiliser des adresses IP au lieu des noms d’hôtes pour spécifier la cible de la connexion TCP.

1. Activation d’IPv6 dans le noyau en supprimant `ipv6.disable=1` à partir de la ligne de commande de démarrage. La façon de procéder dépend de la distribution Linux et le chargeur de démarrage, tels que grub. Si vous ne souhaitez pas que IPv6 doit être désactivée, vous pouvez toujours le désactiver en définissant `net.ipv6.conf.all.disable_ipv6 = 1` dans le `sysctl` configuration (par exemple, `/etc/sysctl.conf`). Cela sera toujours empêcher l’obtention d’une adresse IPv6 de carte de réseau du système, mais vous pouvez autoriser les fonctionnalités sqlservr.

#### <a name="network-file-system-nfs"></a>Network File System (NFS)
Si vous utilisez les partages distants **Network File System (NFS)** en production, notez les exigences de prise en charge suivantes :

- Utiliser la version NFS **4.2 ou ultérieure**. Les versions antérieures de NFS ne gèrent pas les fonctionnalités requises, telles que fallocate et la création de fichier sparse, courantes avec les systèmes de fichiers modernes.
- Positionnez uniquement les répertoires **/var/opt/mssql** sur le montage NFS. Les autres fichiers, tels que les fichiers binaires du système SQL Server, ne sont pas pris en charge.
- Assurez-vous que les clients NFS utilisent l’option 'nolock' lorsque qu'ils montent le partage distant.

#### <a name="localization"></a>Localisation

- Si vos paramètres régionaux ne sont pas anglais (fr_FR) lors de l’installation, vous devez utiliser l’encodage UTF-8 dans votre session d’interpréteur de commandes/terminal. Si vous utilisez l’encodage ASCII, vous pouvez voir une erreur semblable au suivant :

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Si vous ne pouvez pas utiliser l’encodage UTF-8, exécutez le programme d’installation à l’aide de la variable d’environnement MSSQL_LCID pour spécifier votre choix de langage.

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- Lorsque le programme d’installation de mssql-conf en cours d’exécution et effectuer une installation non anglaise de SQL Server, incorrect des caractères étendus sont affichés après le texte localisé, « Configuration de SQL Server... ». Ou, pour les installations en fonction des caractères non latins, la phrase peut être manquante complètement. La phrase manquante doit afficher la chaîne localisée suivante : « le PID de licence a été traité correctement.  La nouvelle édition est [\<nom\> édition] ». Cette chaîne est sortie uniquement à des fins d’information, et la prochaine mise à jour Cumulative SQL Server résoudre ce problème pour toutes les langues. Cela n’affecte pas la réussite de l’installation de SQL Server en aucune façon. 

#### <a name="full-text-search"></a>Recherche en texte intégral

- Pas tous les filtres sont disponibles avec cette version, notamment les filtres pour les documents Office. Pour obtenir la liste de filtres pris en charge, consultez [installer de recherche de texte intégral SQL Server sur Linux](sql-server-linux-setup-full-text-search.md#filters).

#### <a id="ssis"></a> SQL Server Integration Services (SSIS)

- Le **mssql-server est** package n’est pas pris en charge sur SUSE dans cette version. Il est actuellement pris en charge sur Ubuntu sur Red Hat Enterprise Linux (RHEL).

- Avec SSIS lors de l’actualisation de Linux CTP 2.1 et versions ultérieures, les packages SSIS peuvent utiliser des connexions ODBC sur Linux. Cette fonctionnalité a été testée avec le serveur SQL Server et les pilotes ODBC MySQL, mais il est également prévue pour fonctionner avec n’importe quel pilote ODBC Unicode qui observe la spécification ODBC. Au moment du design, vous pouvez fournir une source de données ou une chaîne de connexion pour se connecter aux données ODBC ; Vous pouvez également utiliser l’authentification Windows. Pour plus d’informations, consultez le [billet de blog annonçant prise en charge ODBC sur Linux](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/).

- Les fonctionnalités suivantes ne sont pas pris en charge dans cette version lorsque vous exécutez des packages SSIS sur Linux :
  - Base de données catalogue de SSIS
  - Exécution de package planifié par l’Agent SQL
  - Authentification Windows
  - Les composants tiers
  - Capture de données modifiées (CDC)
  - Integration Services (SSIS) Scale Out
  - Feature Pack Azure pour SSIS
  - Prise en charge de Hadoop et HDFS
  - Microsoft Connector pour SAP BW

Pour obtenir la liste de composants SSIS intégrés qui ne prennent pas en charge, ou qui sont pris en charge avec les limitations, consultez [Limitations et problèmes connus pour SSIS sur Linux](sql-server-linux-ssis-known-issues.md#components).

Pour plus d’informations à propos de SSIS sur Linux, consultez les articles suivants :
-   [Billet de blog annonçant prise en charge de SSIS pour Linux](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/).
-   [Installer SQL Server Integration Services (SSIS) sur Linux](sql-server-linux-setup-ssis.md)
-   [Extraire, transformer et charger des données sur Linux avec SSIS](sql-server-linux-migrate-ssis.md)

#### <a name="-a-idssmsa-sql-server-management-studio-ssms"></a>< un id = « ssms » ></a> SQL Server Management Studio (SSMS)

Les limitations suivantes s’appliquent à SSMS sur Windows connecté à SQL Server sur Linux.

- Plans de maintenance ne sont pas pris en charge.

- L’entrepôt de données de gestion (MDW) et la collecte de données (Data Collector) dans SSMS ne sont pas pris en charge. 

- Les composants de SSMS qui utilisent l’authentification Windows ou les options du journal des événements Windows ne fonctionnent pas avec Linux. Vous pouvez toujours utiliser ces fonctionnalités avec d’autres options, telles que des connexions SQL. 

- Impossible de modifier le nombre de fichiers journaux à conserver.

## <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez les Démarrages rapides suivants :

- [Installation sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécuter sur Docker](quickstart-install-connect-ubuntu.md)
- [Approvisionner une machine virtuelle SQL dans Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)
- [Exécuter et connecter - Cloud](quickstart-install-connect-clouds.md)

Pour obtenir des réponses aux questions fréquemment posées, consultez le [SQL Server sur le Forum aux questions sur Linux](sql-server-linux-faq.md).

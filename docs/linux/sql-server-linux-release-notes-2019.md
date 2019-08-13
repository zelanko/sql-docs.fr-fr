---
title: Notes de publication pour SQL Server 2019 (préversion) sur Linux
description: Cet article contient les notes de publication et fonctionnalités prises en charge pour SQL Server 2019 (préversion) sur Linux. Les notes de publication sont incluses dans la version la plus récente et dans plusieurs versions précédentes.
author: VanMSFT
ms.author: vanto
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15  || >= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 296581ab8052a7eab384721664fc10d675bb2d06
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68476033"
---
# <a name="release-notes-for-sql-server-2019-preview-on-linux"></a>Notes de publication pour SQL Server 2019 (préversion) sur Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md)]

Les notes de publication suivantes s’appliquent à SQL Server 2019 (préversion) sur Linux. Cet article est divisé en sections pour chaque version. Chaque version a un lien vers un article de support décrivant les modifications CU, ainsi que des liens de téléchargement des packages Linux.

> [!TIP]
> Pour en savoir plus sur les nouvelles fonctionnalités de Linux dans SQL Server 2019, consultez [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sql-server-on-linux).

## <a name="supported-platforms"></a>Plateformes prises en charge

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Serveur Red Hat Enterprise Linux 7.3, 7.4, 7.5 ou 7.6 | XFS ou EXT4 | [Guide d'installation](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | XFS ou EXT4 | [Guide d'installation](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS ou EXT4 | [Guide d'installation](quickstart-install-connect-ubuntu.md) | 
| Docker Engine 1.8+ sur Windows, Mac ou Linux | Néant | [Guide d'installation](quickstart-install-connect-docker.md) | 

> [!TIP]
> Pour plus d’informations, consultez la [configuration système requise](sql-server-linux-setup.md#system) pour SQL Server sur Linux. Pour obtenir la dernière stratégie de support pour SQL Server 2017, consultez la [Stratégie de support technique pour Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Outils

La plupart des outils client existants qui ciblent SQL Server peuvent cibler en toute transparence SQL Server sur Linux. Certains outils peuvent avoir une exigence de version spécifique pour fonctionner correctement avec Linux. Pour obtenir la liste complète des outils SQL Server, consultez [Outils et utilitaires SQL pour SQL Server](../tools/overview-sql-tools.md).

## <a name="release-history"></a>Historique des versions

Le tableau suivant répertorie l’historique de publication des versions CTP de SQL Server 2019 (préversion).

| Version               | Options de version       | Date de publication |
|-----------------------|---------------|--------------|
| [CTP 3.2](#CTP32)     | 15.0.1800.32  | 2019-7-24    |
| [CTP 3.1](#CTP31)     | 15.0.1700.37  | 2019-6-26    |
| [CTP 3.0](#CTP30)     | 15.0.1600.8   | 2019-5-22    |
| [CTP 2.5](#CTP25)     | 15.0.1500.28  | 2019-4-24    |
| [CTP 2.4](#CTP24)     | 15.0.1400.75  | 2019-3-27    |
| [CTP 2.3](#CTP23)     | 15.0.1300.359 | 2019-3-01    |
| [CTP 2.2](#CTP22)     | 15.0.1200.24  | 2018-12-11   |
| [CTP 2.1](#CTP21)     | 15.0.1100.94  | 2018-11-06   |
| [CTP 2.0](#CTP20)     | 15.0.1000.34  | 2018-09-24   |

## <a id="cuinstall"></a> Comment installer les mises à jour

Si vous avez configuré le référentiel de la préversion (**mssql-server-preview**), vous obtenez les derniers packages CTP de SQL Server quand vous effectuez de nouvelles installations. Si vous avez besoin d’images de conteneur Docker, consultez les images officielles pour [Microsoft SQL Server sur Linux pour Docker Engine](https://hub.docker.com/r/microsoft/mssql-server/). Pour plus d’informations sur la configuration du référentiel, consultez [Configurer les référentiels pour SQL Server sur Linux](sql-server-linux-change-repo.md).

Si vous mettez à jour des packages SQL Server existants, exécutez la commande de mise à jour appropriée pour chaque package afin d’obtenir la dernière CU. Pour obtenir des instructions de mise à jour spécifiques pour chaque package, consultez les guides d’installation suivants :

- [Installer un package SQL Server](sql-server-linux-setup.md#upgrade)
- [Installer le package de recherche en texte intégral](sql-server-linux-setup-full-text-search.md)
- [Installer SQL Server Integration Services](sql-server-linux-setup-ssis.md)
- [Installer la prise en charge de Python et de Machine Learning Services pour SQL Server 2019 (préversion) sur Linux](sql-server-linux-setup-machine-learning.md)
- [Installer le package PolyBase](../relational-databases/polybase/polybase-linux-setup.md)
- [Activer l’agent SQL Server](sql-server-linux-setup-sql-agent.md)

## <a id="CTP32"></a> CTP 3.2 (juillet 2019)

Les sections suivantes fournissent des emplacements de package et des problèmes connus pour la version CTP 3.2. Pour en savoir plus sur les nouvelles fonctionnalités de Linux sur SQL Server 2019, consultez [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Détails du packages

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 15.0.1800.32-1 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1800.32-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1800.32-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1800.32-1.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1800.32-1.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1800.32-1.x86_64.rpm)</br>[Package RPM PolyBase](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1800.32-1.x86_64.rpm)|
| Package SLES RPM | 15.0.1800.32-1 | [Package RPM du moteur mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1800.32-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1800.32-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1800.32-1.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1800.32-1.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1800.32-1.x86_64.rpm)</br>[Package RPM PolyBase](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1800.32-1.x86_64.rpm)|
| Package Ubuntu 16.04 Debian | 15.0.1800.32-1 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1800.32-1_amd64.deb)</br>[Package Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1800.32-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1800.32-1_amd64.deb)</br>[Package Debian d’extensibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1800.32-1_amd64.deb)</br>[Package Debian d’extensibilité Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1800.32-1_amd64.deb)</br>[Package RPM PolyBase](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1800.32-1_amd64.deb)|

## <a id="CTP31"></a> CTP 3.1 (juin 2019)

Les sections suivantes fournissent des emplacements de package et des problèmes connus pour la version CTP 3.1. Pour en savoir plus sur les nouvelles fonctionnalités de Linux sur SQL Server 2019, consultez [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Détails du packages

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 15.0.1700.37-2 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1700.37-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1700.37-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1700.37-2.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1700.37-2.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1700.37-2.x86_64.rpm)</br>[Package RPM PolyBase](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1700.37-2.x86_64.rpm)|
| Package SLES RPM | 15.0.1700.37-2 | [Package RPM du moteur mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1700.37-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1700.37-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1700.37-2.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1700.37-2.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1700.37-2.x86_64.rpm)</br>[Package RPM PolyBase](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1700.37-2.x86_64.rpm)|
| Package Ubuntu 16.04 Debian | 15.0.1700.37-2 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1700.37-2_amd64.deb)</br>[Package Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1700.37-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1700.37-2_amd64.deb)</br>[Package Debian d’extensibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1700.37-2_amd64.deb)</br>[Package Debian d’extensibilité Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1700.37-2_amd64.deb)</br>[Package RPM PolyBase](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1700.37-2_amd64.deb)|

## <a id="CTP30"></a> CTP 3.0 (juin 2019)

Les sections suivantes fournissent des emplacements de package et des problèmes connus pour la version CTP 3.0. Pour en savoir plus sur les nouvelles fonctionnalités de Linux sur SQL Server 2019, consultez [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Détails du packages

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 15.0.1600.8-1 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1600.8-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1600.8-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1600.8-1.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1600.8-1.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1600.8-1.x86_64.rpm)</br>[Package RPM PolyBase](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1600.8-1.x86_64.rpm)|
| Package SLES RPM | 15.0.1600.8-1 | [Package RPM du moteur mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1600.8-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1600.8-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1600.8-1.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1600.8-1.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1600.8-1.x86_64.rpm)</br>[Package RPM PolyBase](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1600.8-1.x86_64.rpm)|
| Package Ubuntu 16.04 Debian | 15.0.1600.8-1 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1600.8-1_amd64.deb)</br>[Package Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1600.8-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1600.8-1_amd64.deb)</br>[Package Debian d’extensibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1600.8-1_amd64.deb)</br>[Package Debian d’extensibilité Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1600.8-1_amd64.deb)</br>[Package RPM PolyBase](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1600.8-1_amd64.deb)|

### <a name="known-issues"></a>Problèmes connus

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Actuellement, MSDTC requiert l’authentification des transactions. Par exemple, si vous utilisez un serveur lié de SQL Server sur Windows vers SQL Server sur Linux, ou utilisez une application cliente Windows pour démarrer une transaction distribuée sur SQL Server sur Linux, MSDTC sur le serveur/client Windows doit utiliser l’option « Aucune authentification requise ».

## <a id="CTP25"></a> CTP 2.5 (avril 2019)

Les sections suivantes fournissent des emplacements de package et des problèmes connus pour la version CTP 2.5. Pour en savoir plus sur les nouvelles fonctionnalités de Linux sur SQL Server 2019, consultez [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Détails du packages

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 15.0.1500.28-1 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1500.28-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1500.28-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1500.28-1.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1500.28-1.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1500.28-1.x86_64.rpm)</br>[Package RPM PolyBase](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-polybase-15.0.1500.28-1.x86_64.rpm)|
| Package SLES RPM | 15.0.1500.28-1 | [Package RPM du moteur mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1500.28-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1500.28-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1500.28-1.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1500.28-1.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1500.28-1.x86_64.rpm)</br>[Package RPM PolyBase](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-polybase-15.0.1500.28-1.x86_64.rpm)|
| Package Ubuntu 16.04 Debian | 15.0.1500.28-1 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1500.28-1_amd64.deb)</br>[Package Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1500.28-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1500.28-1_amd64.deb)</br>[Package Debian d’extensibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1500.28-1_amd64.deb)</br>[Package Debian d’extensibilité Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1500.28-1_amd64.deb)</br>[Package RPM PolyBase](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-polybase/mssql-server-polybase_15.0.1500.28-1_amd64.deb)|

### <a name="known-issues"></a>Problèmes connus

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Actuellement, MSDTC requiert l’authentification des transactions. Par exemple, si vous utilisez un serveur lié de SQL Server sur Windows vers SQL Server sur Linux, ou utilisez une application cliente Windows pour démarrer une transaction distribuée sur SQL Server sur Linux, MSDTC sur le serveur/client Windows doit utiliser l’option « Aucune authentification requise ».

## <a id="CTP24"></a> CTP 2.4 (mars 2019)

Les sections suivantes fournissent des emplacements de package et des problèmes connus pour la version CTP 2.4. Pour en savoir plus sur les nouvelles fonctionnalités de Linux sur SQL Server 2019, consultez [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Détails du packages

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 15.0.1400.75-2 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1400.75-2.x86_64.rpm)|
| Package SLES RPM | 15.0.1400.75-2 | [Package RPM du moteur mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1400.75-2.x86_64.rpm)|
| Package Ubuntu 16.04 Debian | 15.0.1400.75-2 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1400.75-2_amd64.deb)</br>[Package Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1400.75-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1400.75-2_amd64.deb)</br>[Package Debian d’extensibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1400.75-2_amd64.deb)</br>[Package Debian d’extensibilité Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1400.75-2_amd64.deb)|

### <a name="known-issues"></a>Problèmes connus

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Actuellement, MSDTC requiert l’authentification des transactions. Par exemple, si vous utilisez un serveur lié de SQL Server sur Windows vers SQL Server sur Linux, ou utilisez une application cliente Windows pour démarrer une transaction distribuée sur SQL Server sur Linux, MSDTC sur le serveur/client Windows doit utiliser l’option « Aucune authentification requise ».

## <a id="CTP23"></a> CTP 2.3 (février 2019)

Les sections suivantes fournissent des emplacements de package et des problèmes connus pour la version CTP 2.3. Pour en savoir plus sur les nouvelles fonctionnalités de Linux sur SQL Server 2019, consultez [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Détails du packages

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 15.0.1300.359-1 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1300.359-1.x86_64.rpm)|
| Package SLES RPM | 15.0.1300.359-1 | [Package RPM du moteur mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1300.359-1.x86_64.rpm)|
| Package Ubuntu 16.04 Debian | 15.0.1300.359-1 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1300.359-1_amd64.deb)</br>[Package Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1300.359-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1300.359-1_amd64.deb)</br>[Package Debian d’extensibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1300.359-1_amd64.deb)</br>[Package Debian d’extensibilité Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1300.359-1_amd64.deb)|

### <a name="known-issues"></a>Problèmes connus

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Actuellement, MSDTC requiert l’authentification des transactions. Par exemple, si vous utilisez un serveur lié de SQL Server sur Windows vers SQL Server sur Linux, ou utilisez une application cliente Windows pour démarrer une transaction distribuée sur SQL Server sur Linux, MSDTC sur le serveur/client Windows doit utiliser l’option « Aucune authentification requise ».

## <a id="CTP22"></a> CTP 2.2 (décembre 2018)

Les sections suivantes fournissent des emplacements de package et des problèmes connus pour la version CTP 2.2. Pour en savoir plus sur les nouvelles fonctionnalités de Linux sur SQL Server 2019, consultez [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Détails du packages

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 15.0.1200.24-2 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1200.24-2.x86_64.rpm)|
| Package SLES RPM | 15.0.1200.24-2 | [Package RPM du moteur mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1200.24-2.x86_64.rpm)|
| Package Ubuntu 16.04 Debian | 15.0.1200.24-2 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1200.24-2_amd64.deb)</br>[Package Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1200.24-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1200.24-2_amd64.deb)</br>[Package Debian d’extensibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1200.24-2_amd64.deb)</br>[Package Debian d’extensibilité Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1200.24-2_amd64.deb)|

### <a name="known-issues"></a>Problèmes connus

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Actuellement, MSDTC requiert l’authentification des transactions. Par exemple, si vous utilisez un serveur lié de SQL Server sur Windows vers SQL Server sur Linux, ou utilisez une application cliente Windows pour démarrer une transaction distribuée sur SQL Server sur Linux, MSDTC sur le serveur/client Windows doit utiliser l’option « Aucune authentification requise ».

## <a id="CTP21"></a> CTP 2.1 (novembre 2018)

Les sections suivantes fournissent des emplacements de package et des problèmes connus pour la version CTP 2.1. Pour en savoir plus sur les nouvelles fonctionnalités de Linux sur SQL Server 2019, consultez [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Détails du packages

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 15.0.1100.94-1 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| Package SLES RPM | 15.0.1100.94-1 | [Package RPM du moteur mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| Package Ubuntu 16.04 Debian | 15.0.1100.94-1 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1100.94-1_amd64.deb)</br>[Package Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1100.94-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1100.94-1_amd64.deb)</br>[Package Debian d’extensibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1100.94-1_amd64.deb)</br>[Package Debian d’extensibilité Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1100.94-1_amd64.deb)|

### <a name="known-issues"></a>Problèmes connus

#### <a name="microsoft-distributed-transaction-coordinator"></a>Microsoft Distributed Transaction Coordinator

Actuellement, MSDTC requiert l’authentification des transactions. Par exemple, si vous utilisez un serveur lié de SQL Server sur Windows vers SQL Server sur Linux, ou utilisez une application cliente Windows pour démarrer une transaction distribuée sur SQL Server sur Linux, MSDTC sur le serveur/client Windows doit utiliser l’option « Aucune authentification requise ».

## <a id="CTP20"></a> CTP 2.0 (septembre 2018)

Les sections suivantes fournissent des emplacements de package et des problèmes connus pour la version CTP 2.0. Pour en savoir plus sur les nouvelles fonctionnalités de Linux sur SQL Server 2019, consultez [Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Détails du packages

Pour les installations manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations figurant dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 15.0.1000.34-2 | [Package RPM du moteur](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| Package SLES RPM | 15.0.1000.34-2 | [Package RPM du moteur mssql-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM haute disponibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM de recherche en texte intégral](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM d’extensibilité Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| Package Ubuntu 16.04 Debian | 15.0.1000.34-2 | [Package Debian du moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1000.34-2_amd64.deb)</br>[Package Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1000.34-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1000.34-2_amd64.deb)</br>[Package Debian d’extensibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1000.34-2_amd64.deb)</br>[Package Debian d’extensibilité Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1000.34-2_amd64.deb)|

### <a name="known-issues"></a>Problèmes connus

#### <a name="microsoft-distributed-transaction-coordinator"></a>Microsoft Distributed Transaction Coordinator

Actuellement, MSDTC requiert l’authentification des transactions. Par exemple, si vous utilisez un serveur lié de SQL Server sur Windows vers SQL Server sur Linux, ou utilisez une application cliente Windows pour démarrer une transaction distribuée sur SQL Server sur Linux, MSDTC sur le serveur/client Windows doit utiliser l’option « Aucune authentification requise ».

## <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez les guides de démarrage rapide suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécuter sur Docker](quickstart-install-connect-ubuntu.md)
- [Approvisionner une machine virtuelle SQL dans Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)
- [Exécuter et connecter - Cloud](quickstart-install-connect-clouds.md)

Pour obtenir des réponses aux questions fréquemment posées, consultez le [Forum aux questions de SQL Server sur Linux](sql-server-linux-faq.md).

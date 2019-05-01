---
title: Notes de version préliminaire de SQL Server 2019 sur Linux | Microsoft Docs
description: Cet article contient les notes de publication et les fonctionnalités prises en charge pour la version préliminaire de SQL Server 2019 en cours d’exécution sur Linux. Les notes de publication sont incluses dans la version la plus récente et plusieurs versions précédentes.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15  || >= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 56cb3c4fc617e4b158b974c82bec87401c01fca5
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63455148"
---
# <a name="release-notes-for-sql-server-2019-preview-on-linux"></a>Notes de publication pour la version préliminaire de SQL Server 2019 sur Linux

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-linuxonly.md)]

Les notes de publication suivantes s’appliquent à la version préliminaire de SQL Server 2019 en cours d’exécution sur Linux. Cet article est divisé en sections pour chaque version. Chaque version a un lien vers un article du support technique décrivant les modifications CU, ainsi que des liens vers les téléchargements du package de Linux.

> [!TIP]
> Pour en savoir plus sur les nouvelles fonctionnalités de Linux dans SQL Server 2019, consultez [quelles sont les nouveautés dans SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md?view=sql-server-ver15#sql-server-on-linux).

## <a name="supported-platforms"></a>Plateformes prises en charge

| Plateforme | Système de fichiers | Guide d'installation |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3, 7.4, 7.5 ou 7.6 Server | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server version 12 SP2 | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS ou EXT4 | [Guide d’installation](quickstart-install-connect-ubuntu.md) | 
| Docker Engine 1.8 + sur Windows, Mac ou Linux | N/A | [Guide d’installation](quickstart-install-connect-docker.md) | 

> [!TIP]
> Pour plus d’informations, consultez le [requise](sql-server-linux-setup.md#system) pour SQL Server sur Linux. Pour la dernière stratégie de prise en charge pour SQL Server 2017, consultez le [politique de support technique pour Microsoft SQL Server](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server).

## <a name="tools"></a>Outils

La plupart des outils clients existants qui ciblent SQL Server peuvent en toute transparence ciblant SQL Server en cours d’exécution sur Linux. Certains outils peuvent avoir une exigence de version spécifique pour fonctionner avec Linux. Pour obtenir une liste complète des outils SQL Server, consultez [SQL outils et utilitaires pour SQL Server](../tools/overview-sql-tools.md).

## <a name="release-history"></a>Historique des versions

Le tableau suivant répertorie l’historique de publication pour la version préliminaire de SQL Server 2019 que versions CTP.

| Version               | Version       | Date de publication |
|-----------------------|---------------|--------------|
| [CTP 2.4](#CTP24)     | 15.0.1400.75  | 2019-3-27    |
| [CTP 2.3](#CTP23)     | 15.0.1300.359 | 2019-3-01    |
| [CTP 2.2](#CTP22)     | 15.0.1200.24  | 2018-12-11   |
| [CTP 2.1](#CTP21)     | 15.0.1100.94  | 2018-11-06   |
| [CTP 2.0](#CTP20)     | 15.0.1000.34  | 2018-09-24   |

## <a id="cuinstall"></a> Comment installer des mises à jour

Si vous avez configuré le référentiel d’aperçu (**mssql-server-preview**), vous obtenez les derniers packages CTP de SQL Server lorsque vous effectuez de nouvelles installations. Si vous avez besoin d’images de conteneur Docker, consultez les images officielles pour [Microsoft SQL Server sur Linux pour le moteur Docker](https://hub.docker.com/r/microsoft/mssql-server/). Pour plus d’informations sur la configuration du référentiel, consultez [Source référentiels](sql-server-linux-change-repo.md).

Si vous mettez à jour des packages SQL Server existants, exécutez la commande de mise à jour appropriée pour chaque package obtenir la dernière version CU. Pour obtenir des instructions de mise à jour spécifique pour chaque package, consultez les guides d’installation suivants :

- [Installer le package SQL Server](sql-server-linux-setup.md#upgrade)
- [Installer le package de recherche en texte intégral](sql-server-linux-setup-full-text-search.md)
- [Installer SQL Server Integration Services](sql-server-linux-setup-ssis.md)
- [Installer la version préliminaire de SQL Server 2019 Machine Learning Services R et la prise en charge de Python sur Linux](sql-server-linux-setup-machine-learning.md)
- [Activer l’Agent SQL Server](sql-server-linux-setup-sql-agent.md)

## <a id="CTP24"></a> CTP 2.4 (Mar 2019)

Les sections suivantes fournissent des emplacements de package et les problèmes connus pour la CTP 2.4 version. Pour en savoir plus sur les nouvelles fonctionnalités pour Linux sur SQL Server 2019, consultez le [quelles sont les nouveautés dans SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 15.0.1400.75-2 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM d’extensibilité de Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1400.75-2.x86_64.rpm)|
| Package RPM de SLES | 15.0.1400.75-2 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1400.75-2.x86_64.rpm)</br>[Package RPM d’extensibilité de Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1400.75-2.x86_64.rpm)|
| Package Debian Ubuntu 16.04 | 15.0.1400.75-2 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1400.75-2_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1400.75-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1400.75-2_amd64.deb)</br>[Package Debian d’extensibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1400.75-2_amd64.deb)</br>[Package Debian d’extensibilité de Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1400.75-2_amd64.deb)|

### <a name="known-issues"></a>Problèmes connus

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Actuellement, MSDTC nécessite des transactions non authentifiés. Par exemple, si vous utilisez un serveur lié à partir de SQL Server sur Windows pour SQL Server sur Linux ou utilisez une application cliente de Windows pour démarrer une transaction distribuée par rapport à SQL Server sur Linux, puis MSDTC sur un serveur/client Windows est requis pour utiliser option « non Authentification requise ».

## <a id="CTP23"></a> CTP 2.3 (février 2019)

Les sections suivantes fournissent des emplacements de package et les problèmes connus pour la CTP 2.3 version. Pour en savoir plus sur les nouvelles fonctionnalités pour Linux sur SQL Server 2019, consultez le [quelles sont les nouveautés dans SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 15.0.1300.359-1 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM d’extensibilité de Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1300.359-1.x86_64.rpm)|
| Package RPM de SLES | 15.0.1300.359-1 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1300.359-1.x86_64.rpm)</br>[Package RPM d’extensibilité de Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1300.359-1.x86_64.rpm)|
| Package Debian Ubuntu 16.04 | 15.0.1300.359-1 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1300.359-1_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1300.359-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1300.359-1_amd64.deb)</br>[Package Debian d’extensibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1300.359-1_amd64.deb)</br>[Package Debian d’extensibilité de Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1300.359-1_amd64.deb)|

### <a name="known-issues"></a>Problèmes connus

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Actuellement, MSDTC nécessite des transactions non authentifiés. Par exemple, si vous utilisez un serveur lié à partir de SQL Server sur Windows pour SQL Server sur Linux ou utilisez une application cliente de Windows pour démarrer une transaction distribuée par rapport à SQL Server sur Linux, puis MSDTC sur un serveur/client Windows est requis pour utiliser option « non Authentification requise ».

## <a id="CTP22"></a> CTP 2.2 (décembre 2018)

Les sections suivantes fournissent des emplacements de package et les problèmes connus pour la CTP 2.2 version. Pour en savoir plus sur les nouvelles fonctionnalités pour Linux sur SQL Server 2019, consultez le [quelles sont les nouveautés dans SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 15.0.1200.24-2 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM d’extensibilité de Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1200.24-2.x86_64.rpm)|
| Package RPM de SLES | 15.0.1200.24-2 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1200.24-2.x86_64.rpm)</br>[Package RPM d’extensibilité de Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1200.24-2.x86_64.rpm)|
| Package Debian Ubuntu 16.04 | 15.0.1200.24-2 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1200.24-2_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1200.24-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1200.24-2_amd64.deb)</br>[Package Debian d’extensibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1200.24-2_amd64.deb)</br>[Package Debian d’extensibilité de Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1200.24-2_amd64.deb)|

### <a name="known-issues"></a>Problèmes connus

#### <a id="msdtc"></a> Microsoft Distributed Transaction Coordinator

Actuellement, MSDTC nécessite des transactions non authentifiés. Par exemple, si vous utilisez un serveur lié à partir de SQL Server sur Windows pour SQL Server sur Linux ou utilisez une application cliente de Windows pour démarrer une transaction distribuée par rapport à SQL Server sur Linux, puis MSDTC sur un serveur/client Windows est requis pour utiliser option « non Authentification requise ».

## <a id="CTP21"></a> CTP 2.1 (novembre 2018)

Les sections suivantes fournissent des emplacements de package et les problèmes connus pour la CTP 2.1 version. Pour en savoir plus sur les nouvelles fonctionnalités pour Linux sur SQL Server 2019, consultez le [quelles sont les nouveautés dans SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 15.0.1100.94-1 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM d’extensibilité de Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| Package RPM de SLES | 15.0.1100.94-1 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1100.94-1.x86_64.rpm)</br>[Package RPM d’extensibilité de Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1100.94-1.x86_64.rpm)|
| Package Debian Ubuntu 16.04 | 15.0.1100.94-1 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1100.94-1_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1100.94-1_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1100.94-1_amd64.deb)</br>[Package Debian d’extensibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1100.94-1_amd64.deb)</br>[Package Debian d’extensibilité de Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1100.94-1_amd64.deb)|

### <a name="known-issues"></a>Problèmes connus

#### <a name="microsoft-distributed-transaction-coordinator"></a>Microsoft Distributed Transaction Coordinator

Actuellement, MSDTC nécessite des transactions non authentifiés. Par exemple, si vous utilisez un serveur lié à partir de SQL Server sur Windows pour SQL Server sur Linux ou utilisez une application cliente de Windows pour démarrer une transaction distribuée par rapport à SQL Server sur Linux, puis MSDTC sur un serveur/client Windows est requis pour utiliser option « non Authentification requise ».

## <a id="CTP20"></a> CTP 2.0 (septembre 2018)

Les sections suivantes fournissent des emplacements de package et les problèmes connus pour la CTP 2.0 version. Pour en savoir plus sur les nouvelles fonctionnalités pour Linux sur SQL Server 2019, consultez le [quelles sont les nouveautés dans SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md).

### <a name="package-details"></a>Détails du package

Pour les installations de package manuelles ou hors connexion, vous pouvez télécharger les packages RPM et Debian avec les informations contenues dans le tableau suivant :

| Package | Version du package | Téléchargements |
|-----|-----|-----|
| Package Red Hat RPM | 15.0.1000.34-2 | [Package RPM de moteur](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM d’extensibilité de Java](https://packages.microsoft.com/rhel/7/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| Package RPM de SLES | 15.0.1000.34-2 | [package de moteur RPM MSSQL-server](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM de disponibilité élevée](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-ha-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM de recherche de texte intégral](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-fts-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM d’extensibilité](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-15.0.1000.34-2.x86_64.rpm)</br>[Package RPM d’extensibilité de Java](https://packages.microsoft.com/sles/12/mssql-server-preview/mssql-server-extensibility-java-15.0.1000.34-2.x86_64.rpm)|
| Package Debian Ubuntu 16.04 | 15.0.1000.34-2 | [Package Debian moteur](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server/mssql-server_15.0.1000.34-2_amd64.deb)</br>[Package de Debian haute disponibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-ha/mssql-server-ha_15.0.1000.34-2_amd64.deb)</br>[Package Debian de recherche en texte intégral](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-fts/mssql-server-fts_15.0.1000.34-2_amd64.deb)</br>[Package Debian d’extensibilité](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility/mssql-server-extensibility_15.0.1000.34-2_amd64.deb)</br>[Package Debian d’extensibilité de Java](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/mssql-server-extensibility-java/mssql-server-extensibility-java_15.0.1000.34-2_amd64.deb)|

### <a name="known-issues"></a>Problèmes connus

#### <a name="microsoft-distributed-transaction-coordinator"></a>Microsoft Distributed Transaction Coordinator

Actuellement, MSDTC nécessite des transactions non authentifiés. Par exemple, si vous utilisez un serveur lié à partir de SQL Server sur Windows pour SQL Server sur Linux ou utilisez une application cliente de Windows pour démarrer une transaction distribuée par rapport à SQL Server sur Linux, puis MSDTC sur un serveur/client Windows est requis pour utiliser option « non Authentification requise ».

## <a name="next-steps"></a>Étapes suivantes

Pour commencer, consultez les Démarrages rapides suivants :

- [Installation sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécuter sur Docker](quickstart-install-connect-ubuntu.md)
- [Approvisionner une machine virtuelle SQL dans Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)
- [Exécuter et connecter - Cloud](quickstart-install-connect-clouds.md)

Pour obtenir des réponses aux questions fréquemment posées, consultez le [SQL Server sur le Forum aux questions sur Linux](sql-server-linux-faq.md).

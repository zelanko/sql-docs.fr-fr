---
title: Extension d’Azure SQL Managed Instance
titleSuffix: Azure Data Studio
description: Utiliser Azure Data Studio avec Azure SQL Managed instance
ms.custom: seodec18
ms.date: 10/07/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: jovanpop-msft
ms.author: jovanpop
manager: alanyu
ms.openlocfilehash: d443292fb091679d3d6a18d557a5a7aac464fdec
ms.sourcegitcommit: 512acc178ec33b1f0403b5b3fd90e44dbf234327
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72041140"
---
# <a name="managed-instance-support-for-azure-data-studio-preview"></a>Prise en charge de Managed Instance pour Azure Data Studio (préversion)

Cette extension vous permet d’utiliser [Azure SQL Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-index) dans [Azure Data Studio](https://github.com/Microsoft/azuredatastudio). Cette extension fournit les fonctionnalités suivantes :

- Affichage des propriétés d’instance gérée (vCores, stockage utilisé).
- Surveillance de l’UC et de l’utilisation du stockage au cours des deux dernières heures.
- Affichage des avertissements de configuration et des recommandations de paramétrage.
- Affichage de l’état des réplicas de base de données.
- Affichage des journaux des erreurs filtrés.

## <a name="installations"></a>Installations

Vous pouvez installer la version officielle de l'extension de Managed Instance en suivant les étapes de la [documentation Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/extensions).
Dans le volet Extensions, recherchez l'extension « Managed Instance » et installez-la.  Vous recevrez automatiquement une notification à chaque mise à jour de l'extension !

Une fois l’extension de Managed Instance installée, vous voyez un onglet `Managed Instance` dans Azure Data Studio. Cet onglet contient des informations spécifiques à Managed Instance.

## <a name="properties"></a>Propriétés

Cette extension vous permet de voir les caractéristiques techniques de votre Managed Instance et l’utilisation des ressources.

![Propriétés de l’instance gérée](media/azure-sql-mi-extension/ads-mi-tab1.png)

Dans le premier panneau, vous pouvez voir les détails suivants :

- Les **propriétés de base**, telles que le nombre de vCores disponibles, la mémoire, le stockage, le niveau de service actuel et la génération de matériel ainsi que les caractéristiques d’E/S telles que le débit d’écriture du journal d’instance ou les caractéristiques d’E/S du fichier.
- **Utilisation du stockage SSD local**. Au niveau de service Usage général, seuls les fichiers **TEMPDB** sont placés localement, tandis qu’au niveau vital pour l'entreprise, tous les fichiers de base de données sont placés sur le stockage SSD local. Dans cette section, vous pouvez voir la quantité d’espace de stockage local utilisée par Managed Instance.
- **Utilisation du stockage sur disque Azure Premium** : les bases de données utilisateur et système au niveau de service Usage général sont placées sur le stockage Azure Premium. Ici, vous pouvez trouver combien de données vous avez utilisées et le stockage et le nombre de fichiers restants. Au niveau de service vital pour l'entreprise, cette section est vide.
- **Utilisation des ressources** : vous indique la quantité de stockage et d’UC utilisées par votre instance au cours des deux dernières heures. Augmentez la taille de l’instance si vous atteignez la limite.

## <a name="recommendations"></a>Recommandations

Cette extension fournit des recommandations et des alertes qui peuvent vous aider à optimiser Managed Instance.

![Recommandations relatives à une instance gérée](media/azure-sql-mi-extension/ads-mi-tab2.png)

Quelques-unes de ces recommandations sont mentionnées dans ce tableau :

- Atteinte de la limite d’espace de stockage : vous devez soit supprimer les données inutiles, soit augmenter la taille de stockage de l’instance, car les bases de données qui atteignent la limite de stockage peuvent ne pas pouvoir traiter même les requêtes de lecture.
- Atteinte de la limite de débit : si vous chargez environ 22 Mo/s sur GP ou environ 48 Mo/s sur BC, l’instance gérée limite votre charge pour garantir les sauvegardes.
- Sollicitation de la mémoire : la faible espérance de vie d'une page ou de nombreuses statistiques d’attente `PAGEIOLATCH` peuvent indiquer que votre instance supprime des pages de la mémoire et essaie constamment de charger plus de pages à partir du disque.
- Limites du fichier journal : si vos journaux atteignent les [limites d’E/S de fichier au niveau de service à usage général](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-resource-limits#file-io-characteristics-in-general-purpose-tier), vous devrez peut-être augmenter la taille de fichier pour améliorer les performances.
- Limites du fichier de données : si vos fichiers de données atteignent les [limites d’E/S de fichier au niveau de service à usage général](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-resource-limits#file-io-characteristics-in-general-purpose-tier), vous devrez peut-être augmenter la taille de fichier pour améliorer les performances. Ce problème peut entraîner une sollicitation de la mémoire et ralentir les sauvegardes.
- Problèmes de disponibilité : un nombre élevé de fichiers journaux virtuels peut avoir un impact sur les performances et augmenter la durée de récupération de la base de données au niveau de service à usage général en cas d’échec du processus.

Vous devez lire régulièrement ces recommandations, étudier les causes racines et prendre des mesures correctives. L’extension de Managed Instance fournit les scripts que vous pouvez exécuter pour atténuer certains des problèmes signalés.

## <a name="replicas"></a>Réplicas

L’extension Managed Instance vous permet de voir l’état des réplicas de base de données dans votre instance gérée.

![Réplicas d’instance gérée](media/azure-sql-mi-extension/ads-mi-tab3.png)

Sur la couche de service à usage général, chaque base de données a un seul réplica (principal), tandis que sur l’instance critique pour l'entreprise, chaque base de données a un réplica principal et trois réplicas secondaires (l’un étant utilisé pour les charges de travail en lecture seule). Ici, vous pouvez surveiller le processus de synchronisation et vérifier que tous les réplicas secondaires sont bien  synchronisés avec le réplica principal.

## <a name="logs"></a>Journaux

L’extension Managed Instance affiche les dernières entrées du journal d’erreurs SQL les plus pertinentes.

![Entrées de journal de Managed Instance](media/azure-sql-mi-extension/ads-mi-tab4.png)

Managed Instance émet un grand nombre d’entrées de journal, dont la plupart sont des informations internes/système. Certaines entrées du journal affichent des noms de bases de données physiques (valeurs `GUID`) au lieu de noms de bases de données logiques réelles.

L’extension Managed Instance filtre les entrées de journal inutiles en se basant sur la [méthode Dimitri Furman](https://techcommunity.microsoft.com/t5/DataCAT/Azure-SQL-DB-Managed-Instance-sp-readmierrorlog/ba-p/305506) et affiche les noms de fichiers logiques réels au lieu des noms physiques.

## <a name="reporting-problems"></a>Signalement des problèmes

Si vous rencontrez des problèmes avec l’extension Managed Instance, signalez le problème sur [projet Extension GitHub](https://github.com/JocaPC/AzureDataStudio-Managed-Instance/issues).

## <a name="maintainers"></a>Chargés de maintenance

- [Jovan Popovic(MSFT)](https://github.com/jovanpop_msft) - [@jovanpop_msft](https://twitter.com/JovanPop_MSFT)

## <a name="code-of-conduct"></a>Code de conduite

Ce projet a adopté le [Code de conduite Open Source de Microsoft][conduct-code].
Pour plus d'informations, voir la [FAQ sur le Code de conduite ][conduct-FAQ] ou contacter [opencode@microsoft.com][conduct-email] pour toute question ou commentaire supplémentaire.

[conduct-code]: http://opensource.microsoft.com/codeofconduct/
[conduct-FAQ]: http://opensource.microsoft.com/codeofconduct/faq/
[conduct-email]: mailto:opencode@microsoft.com
[conduct-md]: https://github.com/PowerShell/vscode-powershell/blob/master/CODE_OF_CONDUCT.md

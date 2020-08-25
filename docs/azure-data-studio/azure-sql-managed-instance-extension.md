---
title: Extension d’Azure SQL Managed Instance
description: Utiliser Azure Data Studio avec Azure SQL Managed Instance
ms.custom: seodec18
ms.date: 10/07/2019
ms.reviewer: alanyu, maghan, sstein
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: jovanpop-msft
ms.author: jovanpop
manager: alanyu
ms.openlocfilehash: dd1b610c5c8e99fcda446688d0dbdffe0a9dc51e
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88778478"
---
# <a name="azure-sql-managed-instance-dashboard-for-azure-data-studio-preview"></a>Tableau de bord Azure SQL Managed Instance pour Azure Data Studio (préversion)

L’extension Azure SQL Managed Instance fournit un tableau de bord permettant d’utiliser une [instance Azure SQL Managed Instance](/azure/sql-database/sql-database-managed-instance-index) dans [Azure Data Studio](https://github.com/Microsoft/azuredatastudio). Cette extension fournit les fonctionnalités suivantes :

- Affiche les propriétés de SQL Managed Instance, notamment les vCores et le stockage utilisé
- Supervise l’utilisation du processeur et du stockage au cours des deux heures précédentes
- Affiche des avertissements de configuration et des recommandations de paramétrage
- Affiche l’état des réplicas de base de données
- Affiche les journaux des erreurs filtrés

## <a name="install"></a>Installer

Vous pouvez installer la version officielle de cette extension. Suivez pour cela les étapes décrites dans la documentation sur [Azure Data Studio](./extensions.md).
Dans le volet **Extensions**, recherchez « Managed Instance » et installez-la à cet emplacement. Une fois l’installation terminée, vous recevrez automatiquement une notification à chaque mise à jour de l’extension.

Quand l’extension est installée, un onglet **Instance managée** apparaît dans Azure Data Studio. Vous trouverez ici des informations spécifiques à votre instance managée.

## <a name="properties"></a>Propriétés

Cette extension affiche les caractéristiques techniques de votre instance managée et son utilisation de certaines ressources.

[ ![Propriétés de l’instance managée](media/azure-sql-mi-extension/ads-mi-tab1.png )](media/azure-sql-mi-extension/ads-mi-tab1.png#lightbox)

Le volet supérieur affiche les détails suivants :

- **Propriétés**. Obtenez des informations de base sur votre instance managée, notamment les vCores, la mémoire et le stockage disponibles. Trouvez également le niveau de service actuel, la génération de matériel et les caractéristiques d’E/S telles que le débit d’écriture dans les journaux d’instance ou le débit d’E/S dans les fichiers.
- **Stockage SSD local**. Au niveau de service universel, les fichiers **TempDB** sont stockés localement. Au niveau de service vital pour l’entreprise, _tous_ les fichiers de base de données sont placés dans le stockage SSD local. Dans cette section, vous pouvez voir la quantité d’espace de stockage local utilisée par votre instance managée.
- **Stockage sur disque Azure Premium**. Si vous êtes au niveau de service universel, les fichiers des bases de données utilisateur et système sont placés dans le stockage Azure Premium. Dans cette section, vous pouvez voir la quantité de données utilisées, le nombre de fichiers et le stockage disponible. Au niveau de service vital pour l’entreprise, cette section est vide.
- **Utilisation des ressources**. Examinez le pourcentage de stockage et de processeur utilisé par votre instance managée au cours des deux heures précédentes. Vous pouvez ainsi augmenter la taille de l’instance si elle est proche de la limite.

## <a name="recommendations"></a>Recommandations

Quand vous sélectionnez le deuxième volet sous l’onglet **Instance managée**, vous recevez des recommandations et des alertes pour vous aider à optimiser votre instance managée.

[ ![Recommandations relatives aux instances managées](media/azure-sql-mi-extension/ads-mi-tab2.png )](media/azure-sql-mi-extension/ads-mi-tab2.png#lightbox)

Parmi les recommandations affichées, vous pouvez voir les suivantes :

- **Limite d’espace de stockage en passe d’être atteinte**. Supprimez les données inutiles ou augmentez la taille de stockage de l’instance. Les bases de données qui atteignent la limite de stockage risquent même de ne pas pouvoir traiter les requêtes lues.
- **Limite de débit de l’instance en passe d’être atteinte**. Vous avertit quand votre charge s’approche de la limite de votre niveau de service : 22 Mo/s pour le niveau universel ou 48 Mo/s pour le niveau vital pour l’entreprise. N’oubliez pas que votre instance managée limite votre charge pour que les sauvegardes puissent être effectuées.
- **Sollicitation de la mémoire**. La faible espérance de vie d’une page ou de nombreuses statistiques d’attente `PAGEIOLATCH` peuvent indiquer que votre instance supprime des pages de la mémoire et essaie constamment de charger plus de pages à partir du disque.
- **Limites des fichiers journaux**. Si vos fichiers journaux s’approchent des [limites d’E/S de fichier au niveau de service universel](/azure/sql-database/sql-database-managed-instance-resource-limits#file-io-characteristics-in-general-purpose-tier), vous devrez peut-être augmenter la taille des fichiers journaux pour améliorer les performances.
- **Limites des fichiers de données**. Si vos fichiers de données s’approchent des [limites d’E/S de fichier au niveau de service universel](/azure/sql-database/sql-database-managed-instance-resource-limits#file-io-characteristics-in-general-purpose-tier), vous devrez peut-être augmenter la taille des fichiers pour améliorer les performances. Ce problème peut entraîner une sollicitation de la mémoire et ralentir les sauvegardes.
- **Problèmes de disponibilité**. Un nombre élevé de fichiers journaux virtuels peut affecter les performances. En cas de défaillance d’un processus, ces problèmes peuvent entraîner un allongement de la récupération de la base de données au niveau de service universel.

Examinez régulièrement ces recommandations, étudiez les causes racines et prenez les mesures nécessaires pour corriger les problèmes. L’extension SQL Managed Instance fournit des scripts que vous pouvez exécuter pour atténuer certains des problèmes signalés.

## <a name="replicas"></a>Réplicas

Le troisième volet de l’onglet **Instance managée** affiche l’état des réplicas de base de données dans votre instance managée.

[ ![Réplicas d’instance managée](media/azure-sql-mi-extension/ads-mi-tab3.png )](media/azure-sql-mi-extension/ads-mi-tab3.png#lightbox)

Au niveau de service universel, chaque base de données a un seul réplica (principal). Sur une instance au niveau vital pour l’entreprise, chaque base de données a un réplica principal et trois réplicas secondaires, dont un est utilisé pour les charges de travail en lecture seule. Dans le volet **Réplicas**, vous pouvez superviser le processus de synchronisation et vérifier que tous les réplicas secondaires sont bien synchronisés avec le réplica principal.

## <a name="logs"></a>Journaux d’activité

Le quatrième volet de l’onglet **Instance managée** affiche les entrées du journal des erreurs SQL les plus récentes et les plus pertinentes.

[ ![Entrées du journal de l’instance managée](media/azure-sql-mi-extension/ads-mi-tab4.png )](media/azure-sql-mi-extension/ads-mi-tab4.png#lightbox)

Bien que votre instance managée génère un grand nombre d’entrées de journal, la plupart d’entre elles sont des informations internes/système. Par ailleurs, certaines entrées du journal montrent des noms de bases de données physiques (valeurs `GUID`) au lieu de noms de bases de données logiques réelles.

L’extension SQL Managed Instance filtre les entrées de journal inutiles selon la [méthode Dimitri Furman](https://techcommunity.microsoft.com/t5/DataCAT/Azure-SQL-DB-Managed-Instance-sp-readmierrorlog/ba-p/305506). L’extension affiche également les noms des fichiers logiques réels au lieu des noms physiques.

## <a name="reporting-problems"></a>Signalement des problèmes

Si vous rencontrez des problèmes avec l’extension SQL Managed Instance, accédez au [projet Extension GitHub](https://github.com/JocaPC/AzureDataStudio-Managed-Instance/issues) pour les signaler.

## <a name="code-of-conduct"></a>Code de conduite

Ce projet a adopté le [Code de conduite Open Source de Microsoft][conduct-code].

Pour plus d'informations, voir la [FAQ sur le Code de conduite ][conduct-FAQ] ou contacter [opencode@microsoft.com][conduct-email] pour toute question ou commentaire supplémentaire.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations, visitez le [projet GitHub](https://github.com/JocaPC/AzureDataStudio-Managed-Instance/).

[conduct-code]: https://opensource.microsoft.com/codeofconduct/
[conduct-FAQ]: https://opensource.microsoft.com/codeofconduct/faq/
[conduct-email]: mailto:opencode@microsoft.com
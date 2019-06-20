---
title: Vue d’ensemble de la solution Assistant expérimentation de base de données pour SQL Server met à niveau
description: Vue d’ensemble de l’Assistant expérimentation de base de données
ms.custom: ''
ms.date: 01/08/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
manager: jroth
ms.openlocfilehash: 25b5d051f6241919f34a60a42582e8a101052290
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794461"
---
# <a name="overview-of-database-experimentation-assistant"></a>Vue d’ensemble de l’Assistant expérimentation de base de données

Assistant base de données expérimentation (DEA) est une solution de l’expérimentation des mises à niveau de SQL Server. La DEA peut vous aider à évaluer une version ciblée de SQL Server pour une charge de travail spécifique. Les clients qui sont la mise à niveau à partir de versions antérieures de SQL Server (à partir de 2005) vers une version plus récente de SQL Server peuvent utiliser les métriques d’analyse qui fournit l’outil. 

La DEA analyse métrique incluent :
- Requêtes qui contiennent des erreurs de compatibilité
- Dégradation de requêtes et plans de requête
- Autres données de comparaison de la charge de travail

Données de comparaison peuvent entraîner plus de confiance et une expérience de mise à niveau réussie.

Pour une présentation 19 minutes DEA et une démonstration, regardez la vidéo suivante :

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]

## <a name="get-dea"></a>Obtenir la DEA

Pour installer la DEA, [télécharger](https://www.microsoft.com/download/details.aspx?id=54090) la dernière version de l’outil. Ensuite, exécutez le **DatabaseExperimentationAssistant.exe** fichier.

## <a name="solution-architecture-for-comparing-workloads"></a>Architecture de solution pour la comparaison de charges de travail

Le diagramme suivant illustre l’architecture de solution pour une comparaison de la charge de travail. La comparaison de la charge de travail utilise DEA et Distributed Replay pendant une mise à niveau à partir de SQL Server 2008 vers SQL Server 2016.

![Architecture de solution de comparaison de la charge de travail](./media/database-experimentation-assistant-overview/dea-overview-compare-solution-architecture.png)

## <a name="dea-prerequisites"></a>Conditions préalables DEA

Voici certaines conditions préalables pour la DEA en cours d’exécution :
- Configuration matérielle minimale requise : Une machine monocœur avec 3,5 Go de RAM.
- Exigence de matériel idéal : Un processeur huit cœurs (avec 3,5 Go de RAM ou plus). Processeurs de plus de huit cœurs n’améliorent DEA runtimes.
- Un supplémentaire 33 % de la taille de suivi des performances est nécessaire pour le magasin A, B et bases de données de rapport analyse.

## <a name="configure-dea"></a>Configurer la DEA

Dans l’architecture de l’environnement requis, nous vous recommandons d’installer la DEA *sur le même ordinateur que le contrôleur de Distributed Replay*. Cette pratique permet d’éviter les appels entre ordinateurs et simplifie la configuration.

### <a name="required-configuration-for-workload-comparison-by-using-dea"></a>Configuration requise pour la comparaison de la charge de travail à l’aide de la DEA

La DEA se connecte aux serveurs de base de données à l’aide de l’authentification Windows. N’oubliez pas qu’un utilisateur en cours d’exécution DEA peut se connecter aux serveurs de base de données (source, cible et analyse) à l’aide de l’authentification Windows.

**Capturer la configuration requise**:

*   Utilisateur en cours d’exécution DEA peut se connecter au serveur de base de données source à l’aide de l’authentification Windows.
*   Utilisateur qui exécute la DEA dispose des droits d’administrateur système sur le serveur de base de données source.
*   Compte de service exécutant le serveur de base de données source a accès en écriture pour le chemin d’accès du dossier de trace.

Pour plus d’informations, consultez le [capturer le Forum aux questions](database-experimentation-assistant-capture-trace.md#frequently-asked-questions-about-trace-capture)

**Configuration requise de relecture**: 

*   Utilisateur en cours d’exécution DEA peut se connecter au serveur de base de données cible à l’aide de l’authentification Windows.
*   Utilisateur qui exécute la DEA dispose des droits d’administrateur système sur le serveur de base de données cible.
*   Compte de service exécutant des serveurs de base de données cible a accès en écriture pour le chemin d’accès du dossier de trace.
*   Compte de service exécutant des clients Distributed Replay peut se connecter au serveur de base de données cible à l’aide de l’authentification Windows.
*   La DEA communique avec le contrôleur de Distributed Replay à l’aide des interfaces COM. Assurez-vous que les ports TCP sont ouverts pour les demandes entrantes sur le contrôleur de Distributed Replay.

Pour plus d’informations, consultez le [relire le Forum aux questions](database-experimentation-assistant-replay-trace.md#frequently-asked-questions-about-trace-replay)

**Exigences de configuration analyse**: 

*   Utilisateur en cours d’exécution DEA peut se connecter au serveur de base de données d’analyse à l’aide de l’authentification Windows.
*   Utilisateur qui exécute la DEA dispose des droits d’administrateur système sur le serveur de base de données source.

Pour plus d’informations, consultez le [analysis Forum aux questions](database-experimentation-assistant-create-report.md#frequently-asked-questions-about-analysis-reports)

## <a name="set-up-telemetry"></a>Configurer les données de télémétrie

La DEA possède une fonctionnalité compatibles internet qui envoie des informations de télémétrie à Microsoft. Microsoft collecte des données de télémétrie pour améliorer l’expérience du produit. Données de télémétrie sont facultative. Les informations collectées sont également enregistrées sur votre ordinateur pour l’audit local. Vous pouvez toujours voir les données collectées. Tous les fichiers journaux à partir de la DEA sont enregistrés dans le répertoire % temp%\\dossier DEA.

Vous pouvez décider quels événements sont collectés. Vous décidez également si les événements collectés sont envoyés à Microsoft. Il existe quatre types d’événements :

*   **Objet TraceEvent**: Événements d’utilisation de l’application (par exemple, « déclenchées arrêter la capture »).
*   **Exception**: Exception levée pendant l’utilisation des applications.
*   **DiagnosticEvent**: Un journal des événements afin de faciliter de diagnostic lorsque des problèmes se produisent (*pas* envoyées à Microsoft).
*   **FeedbackEvent**: Commentaires des utilisateurs sont envoyé via l’application.

Ces étapes vous montrent comment choisir les événements sont collectés et indique si les événements sont envoyés à Microsoft :

1.  Accédez à l’emplacement où est installée DEA (par exemple, C:\\Program Files (x86)\\Microsoft Corporation\\Assistant expérimentation de base de données).
2.  Ouvrez les deux fichiers : DEA.exe.config (pour l’application) et DEACmd.exe.config (pour l’interface CLI).
3.  Pour arrêter la collecte d’un type d’événement, définissez la valeur de *événement* (par exemple, **TraceEvent**) à **false**. Pour commencer à collecter à nouveau de l’événement, définissez la valeur sur **true**.
4.  Pour arrêter l’enregistrement de copies locales des événements, définissez la valeur de **TraceLoggerEnabled** à **false**. Pour démarrer l’enregistrement de copies locales à nouveau, définissez la valeur sur **true**.
5.  Pour arrêter l’envoi d’événements à Microsoft, définissez la valeur de **AppInsightsLoggerEnabled** à **false**. Pour commencer à envoyer des événements à Microsoft à nouveau, définissez la valeur sur **true**.

La DEA est régie par le [déclaration de confidentialité Microsoft](https://aka.ms/dea-privacy).

## <a name="next-steps"></a>Étapes suivantes

[Prise en main](database-experimentation-assistant-get-started.md) vous guide à travers les étapes requises pour capturer et relire les analyser une trace.

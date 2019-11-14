---
title: Vue d’ensemble de l’Assistant Expérimentation de base de données
description: Vue d’ensemble de Assistant Expérimentation de base de données
ms.custom: seo-lt-2019
ms.date: 11/05/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: jtoland
ms.reviewer: mathoma
ms.openlocfilehash: 7180656f8a4779c43f4c691f583aaaf5fcbf86d0
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056583"
---
# <a name="overview-of-database-experimentation-assistant"></a>Vue d’ensemble de Assistant Expérimentation de base de données

Assistant Expérimentation de base de données (DEA) est une solution d’expérimentation pour les mises à niveau SQL Server. La DEA peut vous aider à évaluer une version ciblée de SQL Server pour une charge de travail spécifique. Les clients qui effectuent une mise à niveau à partir de versions antérieures de SQL Server (à partir de 2005) vers une version plus récente de SQL Server peuvent utiliser les métriques d’analyse fournies par l’outil.

Les métriques d’analyse de DEA sont les suivantes :

- Requêtes qui présentent des erreurs de compatibilité
- Requêtes détériorées et plans de requête
- Autres données de comparaison de charge de travail

Les données de comparaison peuvent entraîner une plus grande confiance et une expérience de mise à niveau réussie.

## <a name="get-dea"></a>Bénéficier de DEA

Pour installer la DEA, [Téléchargez](https://www.microsoft.com/download/details.aspx?id=54090) la dernière version de l’outil. Exécutez ensuite le fichier **DatabaseExperimentationAssistant. exe** .

## <a name="solution-architecture-for-comparing-workloads"></a>Architecture de la solution pour la comparaison des charges de travail

Le diagramme suivant illustre l’architecture de la solution pour une comparaison de charges de travail. La comparaison des charges de travail utilise la DEA et les Distributed Replay lors d’une mise à niveau de SQL Server 2008 à SQL Server 2016.

![Architecture de la solution de comparaison de charge de travail](./media/database-experimentation-assistant-overview/dea-overview-compare-solution-architecture.png)

## <a name="dea-prerequisites"></a>Conditions requises pour la DEA

Voici quelques conditions préalables à l’exécution de la DEA :

- Configuration matérielle minimale requise : un ordinateur à cœur unique avec 3,5 Go de RAM.
- Configuration matérielle idéale idéale : un processeur à huit cœurs (avec 3,5 Go de RAM ou plus). Les processeurs dotés de plus de huit cœurs n’améliorent pas les runtimes de DEA.
- 33% de la taille de trace de performances supplémentaire est nécessaire pour stocker les bases de données A, B et d’analyse de rapport.

## <a name="configure-dea"></a>Configurer la DEA

Dans l’architecture d’environnement requise, nous vous recommandons d’installer la DEA *sur le même ordinateur que le contrôleur Distributed Replay*. Cette pratique évite les appels entre ordinateurs et simplifie la configuration.

### <a name="required-configuration-for-workload-comparison-by-using-dea"></a>Configuration requise pour la comparaison des charges de travail à l’aide de DEA

La DEA se connecte aux serveurs de base de données à l’aide de l’authentification Windows. Assurez-vous qu’un utilisateur exécutant la DEA peut se connecter aux serveurs de base de données (source, cible et analyse) à l’aide de l’authentification Windows.

**Configuration requise pour la capture**:

- L’utilisateur exécutant la DEA peut se connecter au serveur de base de données source à l’aide de l’authentification Windows.
- L’utilisateur exécutant la DEA dispose de droits d’administrateur système sur le serveur de base de données source.
- Le compte de service qui exécute le serveur de base de données source dispose d’un accès en écriture au chemin du dossier de trace.

Pour plus d’informations, consultez le [Forum aux questions sur la capture](database-experimentation-assistant-capture-trace.md#frequently-asked-questions-about-trace-capture)

**Configuration requise pour la relecture**: 

- L’utilisateur exécutant la DEA peut se connecter au serveur de base de données cible à l’aide de l’authentification Windows.
- L’utilisateur exécutant la DEA dispose de droits d’administrateur système sur le serveur de base de données cible.
- Le compte de service exécutant les serveurs de base de données cible dispose d’un accès en écriture au chemin du dossier de trace.
- Le compte de service exécutant Distributed Replay clients peut se connecter au serveur de base de données cible à l’aide de l’authentification Windows.
- La DEA communique avec le contrôleur Distributed Replay à l’aide d’interfaces COM. Assurez-vous que les ports TCP sont ouverts pour les demandes entrantes sur le contrôleur de Distributed Replay.

Pour plus d’informations, consultez le [FAQ sur la relecture](database-experimentation-assistant-replay-trace.md#frequently-asked-questions-about-trace-replay)

**Configuration requise pour l’analyse**:

- L’utilisateur exécutant la DEA peut se connecter au serveur de base de données d’analyse à l’aide de l’authentification Windows.
- L’utilisateur exécutant la DEA dispose de droits d’administrateur système sur le serveur de base de données source.

Pour plus d’informations, consultez le [FAQ sur l’analyse](database-experimentation-assistant-create-report.md#frequently-asked-questions-about-analysis-reports)

## <a name="set-up-telemetry"></a>Configurer la télémétrie

La DEA dispose d’une fonctionnalité Internet qui peut envoyer des informations de télémétrie à Microsoft. Microsoft collecte des données de télémétrie pour améliorer l’expérience du produit. La télémétrie est facultative. Les informations collectées sont également enregistrées sur votre ordinateur pour un audit local. Vous pouvez toujours voir ce qui est collecté. Tous les fichiers journaux de la DEA sont enregistrés dans le dossier% Temp%\\DEA.

Vous pouvez choisir les événements qui sont collectés. Vous décidez également si les événements collectés sont envoyés à Microsoft. Il existe quatre types d’événements :

- **TraceEvent**: événements d’utilisation de l’application (par exemple, « arrêter la capture »).
- **Exception**: exception levée pendant l’utilisation de l’application.
- **DiagnosticEvent**: journal des événements pour faciliter le diagnostic lorsque des problèmes se produisent (*non* envoyés à Microsoft).
- **FeedbackEvent**: commentaires des utilisateurs qui sont envoyés par le biais de l’application.

Ces étapes vous montrent comment choisir les événements qui sont collectés et si les événements sont envoyés à Microsoft :

1. Accédez à l’emplacement où la DEA est installée (par exemple, C :\\Program Files (x86)\\Microsoft Corporation\\Assistant Expérimentation de base de données).
2. Ouvrez les deux fichiers. config : DEA. exe. config (pour l’application) et DEACmd. exe. config (pour l’interface CLI).
3. Pour arrêter la collecte d’un type d’événement, définissez la valeur de l' *événement* (par exemple, **TraceEvent**) sur **false**. Pour recommencer la collecte de l’événement, définissez la valeur sur **true**.
4. Pour arrêter l’enregistrement des copies locales des événements, affectez la valeur **false**à **TraceLoggerEnabled** . Pour recommencer à enregistrer les copies locales, définissez la valeur sur **true**.
5. Pour arrêter l’envoi d’événements à Microsoft, affectez la valeur **false**à **AppInsightsLoggerEnabled** . Pour commencer à envoyer des événements à Microsoft, définissez la valeur sur **true**.

La DEA est régie par la [déclaration de confidentialité de Microsoft](https://aka.ms/dea-privacy).

## <a name="next-steps"></a>Étapes suivantes

La section [prise en main](database-experimentation-assistant-get-started.md) vous guide tout au long des étapes nécessaires à la capture, à la relecture et à l’analyse d’une trace.

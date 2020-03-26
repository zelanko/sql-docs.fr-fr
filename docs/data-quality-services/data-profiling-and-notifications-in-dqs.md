---
title: Profilage des données et notifications dans DQS
ms.date: 03/15/2020
ms.prod: sql
ms.reviewer: jroth
ms.technology: data-quality-services
ms.topic: conceptual
author: swinarko
ms.author: sawinark
ms.openlocfilehash: e0bd9585a48ee30368d145c79f8431e922801a9c
ms.sourcegitcommit: c30a2def43c86860aeec69d3e3029f2296544b13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80243399"
---
# <a name="data-profiling-and-notifications-in-data-quality-services-dqs"></a>Profilage des données et notifications dans Data Quality Services (DQS)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)](DQS) est un service de profilage des données. DQS analyse les données à partir d’une source et affiche des statistiques sur les données dans les activités DQS.

## <a name="attributes-goals-benefits"></a>Attributs, objectifs, avantages

### <a name="attributes-of-dqs"></a>Attributs de DQS

Le profilage DQS a les attributs suivants :

- Fournit des mesures automatisées de qualité des données.
- Est intégré à la gestion des connaissances DQS et aux projets de qualité des données.
- Est dynamique et réglable.

### <a name="goals-of-dqs"></a>Objectifs de DQS

Le profilage avec DQS présente les deux principaux objectifs suivants :

- Pour vous guider tout au long des processus de qualité des données et pour prendre en charge vos décisions.
- Pour évaluer l’efficacité des processus.

### <a name="benefits-of-dqs"></a>Avantages de DQS

Le profilage DQS présente les avantages suivants :

- Fournit un aperçu de la qualité de vos données sources et vous aide à identifier les problèmes de qualité des données.

- Évalue les processus de qualité des données et guide vos :
  - Découverte des connaissances
  - Nettoyage des données
  - Stratégie de correspondance
  - Travail de correspondance

- Vous présente les informations les plus pertinentes au moment le plus approprié.

- Génère des notifications qui mettent en évidence des statistiques ou des événements importants qui peuvent justifier une action. Les notifications DQS indiquent souvent une condition et recommandent une action corrective.

Le profilage DQS fournit la découverte des connaissances, le nettoyage des données et la correspondance des données. DQS est également un outil d’analyse de données. Vous pouvez créer une base de connaissances pour l’analyse. Ensuite, vous pouvez exécuter la découverte des connaissances à l’aide de la base de connaissances. La découverte des connaissances utilise des statistiques de profilage pour déterminer si la base de connaissances répond à vos besoins en matière de découverte, de nettoyage et de correspondance.

## <a name="how-dqs-profiling-works"></a><a name="How"></a>Fonctionnement du profilage DQS

Le profilage DQS ne mesure pas la qualité de la base de connaissances. Le profilage mesure la qualité des données sources. Le profilage fournit des statistiques qui indiquent l’effet des efforts suivants :

- Votre opération spécifique dans la gestion des connaissances.
- Projet de qualité des données sur vos données sources.

### <a name="activity-context"></a>Contexte d’activité

Le profilage est toujours dans le contexte de l'activité spécifique que vous effectuez. Vous pouvez cliquer sur l’onglet profilage dans un écran pour afficher les données de profilage. Ce clic ne vous éloigne pas de l’étape de l’activité que vous effectuez. La table de profilage est remplie en temps réel à mesure que le processus est exécuté. Par conséquent, vous pouvez évaluer les tâches de qualité des données au fur et à mesure de leur exécution.

Vous pouvez déterminer si les données sources sont meilleures après le nettoyage ou la déduplication, et dans quelle mesure.

### <a name="profiling-is-based-on-counts"></a>Le profilage est basé sur les nombres

Tous les numéros de profilage font référence au nombre d’apparences de valeurs spécifiques. Dans de nombreux cas, les nombres font référence au pourcentage du total. Les métriques d’unicité sont une exception. Les métriques d’unicité font référence au nombre absolu de valeurs, quel que soit le nombre d’apparitions de ces valeurs.

### <a name="knowledge-driven-solution"></a>Solution basée sur les connaissances

Le profilage fait partie de la solution pilotée par la connaissance DQS. Le profilage fournit des informations sur une base de connaissances, la correspondance ou le processus de nettoyage des données. Les informations sont basées sur le mappage entre les champs de source de données et les domaines de base de connaissances. Le profilage n’est effectué qu’une fois le mappage terminé. Aucun profilage n’est effectué pendant l’étape de mappage de toute activité.

Le profilage est toujours joint à une activité. Le processus de profilage est effectué sur les données qui sont _mappées_ aux domaines, et non sur les données _dans_ les domaines.

Le profilage est intégré aux étapes suivantes des activités :

- Étapes de découverte et de **gestion des valeurs de domaine** de l’activité de découverte des connaissances. **Discover**

- Étapes **nettoyer** et **gérer et afficher les résultats** de l’activité de nettoyage.

- La **stratégie de correspondance** et les **résultats de correspondance** sont les étapes de l’activité de stratégie de correspondance.

- Étapes de **correspondance** et d' **exportation** de l’activité de correspondance.

DQS ne fournit pas de statistiques de profilage pour l'activité de gestion de l'arborescence du domaine.

## <a name="profiling-data-by-activity"></a><a name="Activity"></a>Profilage des données par activité

Le profilage DQS utilise les dimensions de qualité des données standard suivantes pour représenter la qualité des données :

- Exhaustivité : étendue dans laquelle les données sont présentes.
- Précision : l’étendue dans laquelle les données peuvent être utilisées pour l’usage prévu.
- Unicité : l’étendue à laquelle les différentes valeurs représentent différentes entités.

Par défaut, les valeurs NULL et vides sont considérées comme manquantes, ou diminuent le pourcentage d’exhaustivité. Toutefois, vous pouvez définir d’autres valeurs comme équivalentes à NULL. Ces valeurs sont également considérées comme manquantes.

Le profilage vous fournit les statistiques nécessaires pour évaluer vos processus, mais vous devez interpréter les statistiques. Saisissez la signification de ce que le profilage indique en examinant les statistiques colonne par colonne.

### <a name="differing-sets-of-profiling-statistics"></a>Différents ensembles de statistiques de profilage

Les activités DQS ont différents ensembles de statistiques de profilage, comme suit :

- Seule l'activité de nettoyage a des statistiques de profilage pour la précision (en pourcentage par domaine). La précision est affectée par la validité, la cohérence, les erreurs de syntaxe et les règles de domaine.

- Seule l'activité de nettoyage a des statistiques de profilage pour les termes corrects, corrigés et suggérés dans la source, et les valeurs corrigées et suggérées par domaine (à la fois nombre et pourcentage).

- Les activités de nettoyage et de découverte des connaissances ont des statistiques de profilage pour la validité (nettoyage par enregistrement, découverte des connaissances par enregistrement et domaine). Les activités de stratégie de correspondance et de correspondance n'ont pas de statistiques pour la validité.

- Les statistiques de profilage sont fournies pour l’unicité, pour la source et par domaine. Cette instruction s’applique aux activités suivantes :
  - Découverte des connaissances.
  - Stratégie de correspondance.
  - Correspondent.
  - Mais _pas_ pour l’activité de nettoyage.

DQS offre des statistiques de profilage spécifiques liées à une activité. Pour plus d’informations, consultez les sections de **profilage** dans les rubriques suivantes :

- [Effectuer une découverte des connaissances](../data-quality-services/perform-knowledge-discovery.md)

- [Nettoyer les données à l’aide de DQS &#40;connaissances&#41; internes](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)

- [Créer une stratégie de correspondance](../data-quality-services/create-a-matching-policy.md)

- [Exécuter un projet de correspondance](../data-quality-services/run-a-matching-project.md)

## <a name="profiling-data-in-activity-monitoring"></a><a name="Monitoring"></a>Profilage des données dans l’analyse des activités

Les informations de profilage sont disponibles non seulement dans les pages d’activité du client de qualité des données, mais également dans l’analyse des activités. Ces informations concernent les activités de découverte des connaissances, de stratégie de correspondance, de correspondance et de nettoyage. Les informations sont disponibles dans les pages activité du client de qualité des données et dans l’analyse des activités.

Vous pouvez afficher tous les éléments suivants à un seul emplacement :

- Propriétés
- Processus de calcul associés des activités
- Informations de profilage générées pour chaque activité

Vous sélectionnez une activité dans la table activité pour afficher les résultats de profilage dans la seconde table. Vous pouvez également exporter les résultats de profilage.

Pour plus d’informations, consultez [DQS Administration](../data-quality-services/dqs-administration.md).

## <a name="notifications"></a><a name="Notifications"></a>Fonctionnalité

DQS génère des notifications pour indiquer le moment où vous pouvez prendre une mesure en fonction des statistiques profilées. DQS utilise des notifications pour des informations importantes sur la source de données. Ces faits montrent l’efficacité de l’activité actuelle par rapport à l’objectif pour lequel elle a été exécutée. Les notifications fournissent des conseils et des recommandations qui indiquent une condition. Les notifications peuvent également vous recommander comment vous pouvez améliorer une activité de découverte des connaissances, de nettoyage des données ou de correspondance des données.

DQS envoie une notification lorsqu’il détecte un problème susceptible de vous être important. En guise d’exemple de situation, lorsque l’exhaustivité et la précision sont à la fois de 100%, l’activité de nettoyage des données peut ne produire aucune valeur corrigée ni suggérée. DQS peut poster une notification pour cette situation. Cette notification indique que l’activité n’est peut-être pas nécessaire. L’exécution de l’activité reste votre décision.

Une notification est indiquée par une info-bulle avec un point d’exclamation dans l’onglet **profilage** . les statistiques associées à la notification sont colorées en rouge pour indiquer la justification statistique de la notification.

### <a name="disable-notifications"></a>Désactiver les notifications

Les notifications sont activées par défaut. Toutefois, vous pouvez désactiver les notifications à l’aide de la Data Quality Client page d’hébergement. Dans la section **administration** , utilisez l’onglet **paramètres généraux** .

Lorsque les notifications sont désactivées, les info-bulles ne sont pas affichées et les statistiques ne sont pas colorées en rouge. Le profilage reste opérationnel lorsque les notifications sont désactivées. Les performances ne sont pas améliorées en désactivant les notifications.

Pour connaître des conditions spécifiques associées aux notifications pour une activité, consultez ce qui suit :

- [Effectuer une découverte des connaissances](../data-quality-services/perform-knowledge-discovery.md)

- [Nettoyer les données à l’aide de DQS &#40;connaissances&#41; internes](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)

- [Créer une stratégie de correspondance](../data-quality-services/create-a-matching-policy.md)

- [Exécuter un projet de correspondance](../data-quality-services/run-a-matching-project.md)

## <a name="related-tasks"></a>Tâches associées

| Description de la tâche | Rubrique |
| :--------------- | :---- |
| Explique comment activer ou désactiver les notifications dans DQS. | [Activer ou désactiver les notifications de profilage dans DQS](../data-quality-services/enable-or-disable-profiling-notifications-in-dqs.md) |
|||

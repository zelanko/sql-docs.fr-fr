---
title: Activer ou désactiver la collecte des données d’utilisation et des rapports d’incidents
titleSuffix: Azure Data Studio
description: Cet article explique comment contrôler si les données de rapports d’incidents et de l’utilisation sont collectées et envoyées à Microsoft.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1f9dd29edf2474ab8db0e3dc7ad7dc2ff78016d1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63239444"
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>Activer ou désactiver la collecte des données d’utilisation [!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>Comment désactiver les rapports de télémétrie

[!INCLUDE[name-sos](../includes/name-sos-short.md)] collecte des données d’utilisation et l’envoie à Microsoft pour aider à améliorer nos produits et services. Pour en savoir plus, lisez le [déclaration de confidentialité](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Si vous ne souhaitez pas envoyer les données d’utilisation à Microsoft, vous pouvez définir le *telemetry.enableTelemetry* à *false*.

Pour exclure tous les événements de télémétrie à partir de [!INCLUDE[name-sos](../includes/name-sos-short.md)], à partir de **fichier** > **préférences** > **paramètres**, ajouter l’option suivante :

```json
    "telemetry.enableTelemetry": false
```

**Avis important**: Cette option nécessite un redémarrage de [!INCLUDE[name-sos](../includes/name-sos-short.md)] entrent en vigueur. 

## <a name="how-to-disable-crash-reporting"></a>Comment désactiver le signalement des incidents

Pour désactiver le rapport d’incident, à partir de **fichier** > **préférences** > **paramètres**, ajoutez l’option suivante :

```json
    "telemetry.enableCrashReporter": false
```

**Avis important**: Cette option nécessite un redémarrage de [!INCLUDE[name-sos](../includes/name-sos-short.md)] entrent en vigueur.

## <a name="additional-resources"></a>Ressources supplémentaires
- [Paramètres de l’espace de travail et l’utilisateur](settings.md)

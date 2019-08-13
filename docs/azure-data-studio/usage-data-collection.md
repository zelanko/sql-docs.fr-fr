---
title: Activer ou désactiver la collecte de données d’utilisation et les rapports d’incident
titleSuffix: Azure Data Studio
description: Cet article explique comment contrôler si les données de rapport d’utilisation et d’incident sont collectées et envoyées à Microsoft.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 71ed86e9ad076a41099eaf4e56fe67a25b5f2c21
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958947"
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>Activer ou désactiver la collecte de données d’utilisation pour [!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>Comment désactiver la création de rapports de télémétrie

[!INCLUDE[name-sos](../includes/name-sos-short.md)] collecte des données d’utilisation et les envoie à Microsoft pour contribuer à l’amélioration de nos produits et services. Pour en savoir plus, consultez la [Déclaration de confidentialité](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Si vous ne souhaitez pas envoyer de données d’utilisation à Microsoft, vous pouvez définir le paramètre *telemetry.enableTelemetry* sur *false*.

Pour couper tous les événements de télémétrie de [!INCLUDE[name-sos](../includes/name-sos-short.md)], à partir de **Fichier** > **Préférences** > **Paramètres**, ajoutez l’option suivante :

```json
    "telemetry.enableTelemetry": false
```

**Remarque importante** : Cette option nécessite un redémarrage de [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour prendre effet. 

## <a name="how-to-disable-crash-reporting"></a>Comment désactiver les rapports d’incident

Pour désactiver la création de rapports d’incident, à partir de **Fichier** > **Préférences** > **Paramètres**, ajoutez l’option suivante :

```json
    "telemetry.enableCrashReporter": false
```

**Remarque importante** : Cette option nécessite un redémarrage de [!INCLUDE[name-sos](../includes/name-sos-short.md)] pour prendre effet.

## <a name="additional-resources"></a>Ressources supplémentaires
- [Espace de travail et paramètres utilisateur](settings.md)

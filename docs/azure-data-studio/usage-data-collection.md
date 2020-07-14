---
title: Activer ou désactiver la collecte de données d’utilisation et les rapports d’incident
description: Cet article explique comment contrôler si les données de rapport d’utilisation et d’incident sont collectées et envoyées à Microsoft.
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18; seo-lt-2019
ms.date: 09/24/2018
ms.openlocfilehash: ad36e319338c90c33e0969f75ee34e980f3d23f5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85771938"
---
# <a name="enable-or-disable-usage-data-collection-for-azure-data-studio"></a>Activer ou désactiver la collecte de données d’utilisation pour Azure Data Studio

## <a name="how-to-disable-telemetry-reporting"></a>Comment désactiver la création de rapports de télémétrie

Azure Data Studio collecte des données d’utilisation et les envoie à Microsoft pour contribuer à l’amélioration de nos produits et services. Pour en savoir plus, consultez la [Déclaration de confidentialité](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Si vous ne souhaitez pas envoyer de données d’utilisation à Microsoft, vous pouvez définir le paramètre *telemetry.enableTelemetry* sur *false*.

Pour couper tous les événements de télémétrie d’Azure Data Studio, à partir de **Fichier** > **Préférences** > **Paramètres**, ajoutez l’option suivante :

```json
    "telemetry.enableTelemetry": false
```

**Remarque importante** : Cette option nécessite un redémarrage d’Azure Data Studio pour prendre effet. 

## <a name="how-to-disable-crash-reporting"></a>Comment désactiver les rapports d’incident

Pour désactiver la création de rapports d’incident, à partir de **Fichier** > **Préférences** > **Paramètres**, ajoutez l’option suivante :

```json
    "telemetry.enableCrashReporter": false
```

**Remarque importante** : Cette option nécessite un redémarrage d’Azure Data Studio pour prendre effet.

## <a name="additional-resources"></a>Ressources supplémentaires
- [Espace de travail et paramètres utilisateur](settings.md)

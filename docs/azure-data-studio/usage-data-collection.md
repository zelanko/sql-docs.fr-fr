---
title: Activer ou désactiver la collecte de données d’utilisation et rapports pour Azure Data Studio sur les incidents | Microsoft Docs
description: Cet article explique comment contrôler si les données de rapports d’incidents et de l’utilisation sont collectées et envoyées à Microsoft.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 17bcdff85ff4f40b41492095d265bc4c2b503d76
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "48038414"
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>Activer ou désactiver la collecte des données d’utilisation [!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>Comment désactiver les rapports de télémétrie

[!INCLUDE[name-sos](../includes/name-sos-short.md)] collecte des données d’utilisation et l’envoie à Microsoft pour aider à améliorer nos produits et services. Pour en savoir plus, lisez le [déclaration de confidentialité](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Si vous ne souhaitez pas envoyer les données d’utilisation à Microsoft, vous pouvez définir le *telemetry.enableTelemetry* à *false*.

Pour exclure tous les événements de télémétrie à partir de [!INCLUDE[name-sos](../includes/name-sos-short.md)], à partir de **fichier** > **préférences** > **paramètres**, ajouter l’option suivante :

```json
    "telemetry.enableTelemetry": false
```

**Avis important**: cette option nécessite un redémarrage de [!INCLUDE[name-sos](../includes/name-sos-short.md)] entrent en vigueur. 

## <a name="how-to-disable-crash-reporting"></a>Comment désactiver le signalement des incidents

Pour désactiver le rapport d’incident, à partir de **fichier** > **préférences** > **paramètres**, ajoutez l’option suivante :

```json
    "telemetry.enableCrashReporter": false
```

**Avis important**: cette option nécessite un redémarrage de [!INCLUDE[name-sos](../includes/name-sos-short.md)] entrent en vigueur.

## <a name="additional-resources"></a>Ressources supplémentaires
- [Paramètres de l’espace de travail et l’utilisateur](settings.md)

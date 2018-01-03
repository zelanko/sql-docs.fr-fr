---
title: "Détection de troncation de données activée à l’aide de ExtendedAnsiSQL | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 46f36a9de5b1ce9ca269511bb0a2a641d201ed37
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Détection de troncation de données activée à l’aide de ExtendedAnsiSQL
Lorsque l’indicateur ExtendedAnsiSQL est activé et l’application insère des données dans un char ou une colonne binaire des données sont tronquées, la troncation est détectée. Lorsque l’indicateur ExtendedAnsiSQL est désactivée, les données sont tronquées sans avertissement, tel qu’il était dans les versions précédentes des pilotes ODBC bureau de base de données.

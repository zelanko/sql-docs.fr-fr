---
title: Détection de troncation de données activée à l’aide de ExtendedAnsiSQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95b7d538c2ace45b42c947b56ca5a5bd5f981ec5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62744276"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Détection de la troncation de données activée avec ExtendedAnsiSQL
Lorsque l’indicateur ExtendedAnsiSQL est activé et l’application insère des données dans un char ou une colonne binaire des données sont tronquées, la troncation sera détectée. Lorsque l’indicateur ExtendedAnsiSQL est désactivée, les données sont tronquées sans avertissement, tel qu’il était dans les versions précédentes des pilotes de base de données ODBC Desktop.

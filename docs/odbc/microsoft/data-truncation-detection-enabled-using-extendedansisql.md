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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae1aa7a8a8b9ea2c3f3054717546506e660d5270
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280695"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Détection de la troncation de données activée avec ExtendedAnsiSQL
Lorsque l’indicateur ExtendedAnsiSQL est activé et que l’application insère des données dans une colonne de type char ou binary et que les données sont tronquées, la troncation est détectée. Lorsque l’indicateur ExtendedAnsiSQL est désactivé, les données sont tronquées sans avertissement, comme c’était le cas dans les versions précédentes des pilotes de base de données de bureau ODBC.

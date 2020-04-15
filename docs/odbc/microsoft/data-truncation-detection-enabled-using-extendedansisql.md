---
title: Détection de la truncation de données activée à l’aide d’Un Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280695"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>Détection de la troncation de données activée avec ExtendedAnsiSQL
Lorsque le drapeau ExtendedAnsiSQL est activé et que l’application insère des données dans une colonne et des données binaires et que les données sont tronquées, la troncation sera détectée. Lorsque le drapeau ExtendedAnsiSQL est désactivé, les données sont tronquées sans avertissement, comme elles l’étaient dans les versions précédentes des pilotes de base de données de bureau ODBC.

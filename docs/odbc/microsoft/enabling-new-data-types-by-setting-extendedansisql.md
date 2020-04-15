---
title: Permettre de nouveaux types de données en définissant ExtendedAnsiSQL (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- extendedANSISQL [ODBC], enabling new data types
ms.assetid: f2865543-7fff-44fa-9a6a-968bec33acdc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b703c5c14c4743e13feee139d16e5dfeb3c24c63
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303410"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>Activation de nouveaux types de données en définissant ExtendedAnsiSQL
Deux nouveaux types de données sont disponibles dans les bases de données Jet 4.0 lorsque le drapeau ExtendedAnsiSQL est activé : SQL_DECIMAL et SQL_NUMERIC. La précision par défaut et l’échelle sont 18 et 0, respectivement. Les données accessibles via ODBC qui sont dactylographiées comme SQL_DECIMAL ou SQL_NUMERIC seront cartographiées sur Microsoft Jet Decimal au lieu de Currency.  
  
 Lorsque le drapeau ExtendedAnsiSQL est éteint, vous ne pouvez pas créer des tables avec des types décimaux ou numériques, et ces types n’apparaîtront pas dans SQLGetTypeInfo(). Toutefois, si le tableau contient les nouveaux types de données, ils peuvent être utilisés avec les types de données corrects.

---
title: Activation de nouveaux types de données en définissant ExtendedAnsiSQL | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303410"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>Activation de nouveaux types de données en définissant ExtendedAnsiSQL
Deux nouveaux types de données sont disponibles dans les bases de données Jet 4,0 lorsque l’indicateur ExtendedAnsiSQL est activé : SQL_DECIMAL et SQL_NUMERIC. La précision et l’échelle par défaut sont respectivement 18 et 0. Les données accessibles via ODBC typées comme SQL_DECIMAL ou SQL_NUMERIC sont mappées à Microsoft Jet Decimal au lieu de Currency.  
  
 Lorsque l’indicateur ExtendedAnsiSQL est désactivé, vous ne pouvez pas créer de tables avec des types Decimal ou numeric, et ces types n’apparaissent pas dans SQLGetTypeInfo (). Toutefois, si la table contient les nouveaux types de données, ceux-ci peuvent être utilisés avec les types de données corrects.

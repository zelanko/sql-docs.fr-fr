---
title: L’activation de nouveaux Types de données en définissant ExtendedAnsiSQL | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 88f11adcab09dbe6964bfd67a944912fc185bccb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031121"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>Activation de nouveaux types de données en définissant ExtendedAnsiSQL
Deux nouveaux types de données sont disponibles dans les bases de données Jet 4.0 lorsque l’indicateur ExtendedAnsiSQL est activé : SQL_DECIMAL et SQL_NUMERIC. La précision par défaut et l’échelle sont respectivement 18 et 0. Données accédées via ODBC est typée en tant que SQL_DECIMAL ou SQL_NUMERIC seront être mappées à Microsoft Jet décimal au lieu de devise.  
  
 Lorsque l’indicateur ExtendedAnsiSQL est désactivée, vous ne pouvez pas créer des tables avec types décimales ou numériques, et ces types n’apparaissent pas dans SQLGetTypeInfo(). Toutefois, si la table contient de nouveaux types de données, elles peuvent servir avec les types de données correct.

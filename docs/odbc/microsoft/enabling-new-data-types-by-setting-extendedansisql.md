---
title: "L’activation de nouveaux Types de données en définissant ExtendedAnsiSQL | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extendedANSISQL [ODBC], enabling new data types
ms.assetid: f2865543-7fff-44fa-9a6a-968bec33acdc
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9eeff1a55315b30ab0d2cafa92f0aa4a511f9ab9
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>L’activation de nouveaux Types de données en définissant ExtendedAnsiSQL
Deux nouveaux types de données sont disponibles dans les bases de données Jet 4.0 lorsque l’indicateur ExtendedAnsiSQL est activée : SQL_DECIMAL et SQL_NUMERIC. La précision par défaut et l’échelle sont respectivement 18 et 0. Les données accessibilitées via ODBC qui est typée en tant que SQL_DECIMAL ou SQL_NUMERIC seront mappées à Microsoft Jet décimal au lieu de devise.  
  
 Lorsque l’indicateur ExtendedAnsiSQL est désactivée, Impossible de créer des tables avec des types décimales ou numériques, et ces types n’apparaissent pas dans SQLGetTypeInfo(). Toutefois, si la table contient de nouveaux types de données, ils peuvent être utilisés avec les types de données correct.

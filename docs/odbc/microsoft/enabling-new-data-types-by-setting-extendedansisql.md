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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 88f11adcab09dbe6964bfd67a944912fc185bccb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68031121"
---
# <a name="enabling-new-data-types-by-setting-extendedansisql"></a>Activation de nouveaux types de données en définissant ExtendedAnsiSQL
Deux nouveaux types de données sont disponibles dans les bases de données Jet 4,0 lorsque l’indicateur ExtendedAnsiSQL est activé : SQL_DECIMAL et SQL_NUMERIC. La précision et l’échelle par défaut sont respectivement 18 et 0. Les données accessibles via ODBC typées comme SQL_DECIMAL ou SQL_NUMERIC sont mappées à Microsoft Jet Decimal au lieu de Currency.  
  
 Lorsque l’indicateur ExtendedAnsiSQL est désactivé, vous ne pouvez pas créer de tables avec des types Decimal ou numeric, et ces types n’apparaissent pas dans SQLGetTypeInfo (). Toutefois, si la table contient les nouveaux types de données, ceux-ci peuvent être utilisés avec les types de données corrects.

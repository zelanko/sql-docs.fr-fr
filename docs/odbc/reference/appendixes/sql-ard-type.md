---
title: SQL_ARD_TYPE Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], SQL_ARD_TYPE
- SQL_ARD_TYPE [ODBC]
ms.assetid: 8d87ca10-f955-4284-8689-e9f4cc31e7ae
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d7e28d6babb7db8364697ae62092256396b44914
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305030"
---
# <a name="sql_ard_type"></a>SQL_ARD_TYPE
L’identifiant de type SQL_ARD_TYPE est utilisé pour indiquer que les données d’un tampon seront du type spécifiée dans le champ SQL_DESC_CONCISE_TYPE de l’ARD. SQL_ARD_TYPE est inscrit dans l’argument *TargetType* d’un appel à **SQLGetData** au lieu d’un type de données spécifique et permet à une application de modifier le type de données du tampon en changeant le champ descripteur. Cette valeur lie le type de données du tampon * \*TargetValuePtr* au champ descripteur. (SQL_ARD_TYPE n’est pas entré dans un appel à **SQLBindCol** ou **SQLBindParameter** parce que le type de tampon lié est déjà lié aux champs SQL_DESC_TYPE et SQL_DESC_CONCISE_TYPE et peut être changé à tout moment en changeant l’un ou l’autre de ces champs.)  
  
 L’identifiant de type SQL_ARD_TYPE peut être utilisé pour spécifier des valeurs non-défenses pour la précision de pointe et la précision des secondes des types de données d’intervalle, ainsi que les valeurs de précision et d’échelle pour le type de données SQL_C_NUMERIC. Pour plus d’informations, voir [Overriding Default Leading et Seconds Precision for Interval Data Types](../../../odbc/reference/appendixes/overriding-default-leading-and-seconds-precision-for-interval-data-types.md) and [Overrideing Default Precision and Scale for Numeric Data Types](../../../odbc/reference/appendixes/overriding-default-precision-and-scale-for-numeric-data-types.md), plus tard dans cette annexe.

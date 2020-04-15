---
title: Support de type de données (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3abfe85ee32fb9ff4a8499c9949c0685563fec70
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284426"
---
# <a name="data-type-support"></a>Prise en charge du type de données
Les conducteurs de l’ODBC doivent soutenir au moins un des SQL_CHAR et SQL_VARCHAR. Le support pour d’autres types de données est déterminé par le niveau de conformité SQL-92 du conducteur ou de la source de données. Une application doit appeler **SQLGetTypeInfo** pour déterminer les types de données pris en charge par le conducteur.  
  
 Pour plus d’informations sur les types de données, voir [Annexe D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md).

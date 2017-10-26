---
title: SQLBindParameter (pilote Excel) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel driver [ODBC], SQLBindParameter
- SQLBindParameter function [ODBC], Excel Driver
ms.assetid: 40489bc5-3e2a-425e-892d-e0dc037f4d7a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 013f19579815dfcac2fcfe78cbbe41919bff9c15
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlbindparameter-excel-driver"></a>SQLBindParameter (pilote Excel)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote Excel. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Lorsque le pilote Microsoft Excel est utilisé, l’exécution d’une instruction INSERT qui utilise un paramètre pour insérer une valeur NULL dans une colonne SQL_CHAR retourne SQL_SUCCESS_WITH_INFO, SQLSTATE 01004, « Données tronquées. »


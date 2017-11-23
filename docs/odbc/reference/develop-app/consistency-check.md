---
title: "Vérification de cohérence | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2b661526c69d6dbe88e47d4eace4f13c603f5e16
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="consistency-check"></a>Vérification de cohérence
Une vérification de cohérence est effectuée par le pilote automatiquement chaque fois qu’une application définit le champ SQL_DESC_DATA_PTR du APD, ARD ou IPD. Chaque fois que ce champ est défini, le pilote vérifie que la valeur du champ SQL_DESC_TYPE et les valeurs applicables pour le champ SQL_DESC_TYPE dans le même enregistrement sont valides et cohérents.  
  
 Le champ SQL_DESC_DATA_PTR d’un IPD n’est pas défini normalement ; Toutefois, une application peut faire pour forcer une vérification de cohérence de champs IPD. La valeur définie pour le champ SQL_DESC_DATA_PTR de l’IPD n’est pas réellement stockée et ne peut pas être récupérée par un appel à **SQLGetDescField** ou **SQLGetDescRec**; le paramètre fait uniquement pour forcer la vérification de cohérence. Une vérification de cohérence ne peut pas être effectuée sur un IRD.  
  
 Pour plus d’informations sur la vérification de cohérence, consultez [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).

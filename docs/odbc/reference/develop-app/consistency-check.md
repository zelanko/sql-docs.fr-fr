---
title: "Vérification de cohérence | Documents Microsoft"
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
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 81ecac0249bc5e981c95b319f64768d45b792b96
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="consistency-check"></a>Vérification de cohérence
Une vérification de cohérence est effectuée par le pilote automatiquement chaque fois qu’une application définit le champ SQL_DESC_DATA_PTR du APD, ARD ou IPD. Chaque fois que ce champ est défini, le pilote vérifie que la valeur du champ SQL_DESC_TYPE et les valeurs applicables pour le champ SQL_DESC_TYPE dans le même enregistrement sont valides et cohérents.  
  
 Le champ SQL_DESC_DATA_PTR d’un IPD n’est pas défini normalement ; Toutefois, une application peut faire pour forcer une vérification de cohérence de champs IPD. La valeur définie pour le champ SQL_DESC_DATA_PTR de l’IPD n’est pas réellement stockée et ne peut pas être récupérée par un appel à **SQLGetDescField** ou **SQLGetDescRec**; le paramètre fait uniquement pour forcer la vérification de cohérence. Une vérification de cohérence ne peut pas être effectuée sur un IRD.  
  
 Pour plus d’informations sur la vérification de cohérence, consultez [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).

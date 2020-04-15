---
title: Vérification de cohérence (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: edd946ca865cd9d8d2edff2c7bedbb3b2629c97c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298999"
---
# <a name="consistency-check"></a>Vérification de la cohérence
Une vérification de cohérence est effectuée automatiquement par le conducteur chaque fois qu’une application définit le champ SQL_DESC_DATA_PTR de l’APD, de l’ARD ou de l’IPD. Chaque fois que ce champ est défini, le conducteur vérifie que la valeur du champ SQL_DESC_TYPE et les valeurs applicables au champ SQL_DESC_TYPE dans le même dossier sont valides et cohérentes.  
  
 Le champ SQL_DESC_DATA_PTR d’un IPD n’est normalement pas défini; cependant, une application peut le faire pour forcer une vérification de cohérence des champs IPD. La valeur à laquelle le champ SQL_DESC_DATA_PTR de l’IPD est configuré n’est pas réellement stockée et ne peut pas être récupérée par un appel à **SQLGetDescField** ou **SQLGetDescRec;** le réglage est fait uniquement pour forcer le contrôle de cohérence. Une vérification de cohérence ne peut pas être effectuée sur un IRD.  
  
 Pour plus d’informations sur le contrôle de cohérence, voir [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).

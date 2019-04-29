---
title: Vérification de cohérence | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cb73d8a4de482f24eae5794232019af9890e3624
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63043734"
---
# <a name="consistency-check"></a>Vérification de la cohérence
Une vérification de cohérence est effectuée par le pilote automatiquement chaque fois qu’une application définit le champ SQL_DESC_DATA_PTR du APD, ARD ou IPD. Chaque fois que ce champ est défini, le pilote vérifie que la valeur du champ SQL_DESC_TYPE et les valeurs applicables pour le champ SQL_DESC_TYPE dans le même enregistrement sont valides et cohérentes.  
  
 Le champ SQL_DESC_DATA_PTR d’une infrastructure ou IPD n’est pas normalement défini ; Toutefois, une application peut le faire pour forcer une vérification de cohérence de champs IPD. La valeur définie pour le champ SQL_DESC_DATA_PTR de l’IPD n’est pas réellement stockée et ne peut pas être récupérée par un appel à **SQLGetDescField** ou **SQLGetDescRec**; le paramètre est effectué uniquement pour forcer le vérification de cohérence. Impossible d’effectuer une vérification de cohérence sur un IRD.  
  
 Pour plus d’informations sur la vérification de cohérence, consultez [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md).

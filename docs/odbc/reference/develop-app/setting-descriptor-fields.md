---
description: Définition des champs de descripteur
title: Définition des champs de descripteur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: d735dc64-370f-48ab-a59f-6cef9bc4e1e8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6625db69709098f3a3db1a1d40f9ab583eee4030
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476431"
---
# <a name="setting-descriptor-fields"></a>Définition des champs de descripteur
Pour modifier les champs d’un descripteur, une application peut appeler **SQLSetDescField**. Certains champs sont en lecture seule et ne peuvent pas être définis. (Voir la description de la fonction [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md) .)  
  
 Les champs d’enregistrement du descripteur sont définis avec un numéro d’enregistrement (*recnumber*) égal ou supérieur à 1, tandis que les champs d’en-tête de descripteur sont définis avec un numéro d’enregistrement égal à 0. Le numéro d’enregistrement 0 est également utilisé pour définir les champs de signet, conformément à la Convention selon laquelle les signets sont contenus dans la colonne 0. Cela peut entraîner l’impression que les champs de signet sont contenus dans l’en-tête du descripteur, mais ce n’est pas le cas. Les champs de signet sont distincts des champs d’en-tête.  
  
 Lors de la définition des champs individuellement, l’application doit suivre la séquence définie dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Si vous définissez certains champs, le pilote définit d’autres champs. Cela garantit que le descripteur est toujours prêt à être utilisé une fois que l’application a spécifié un type de données. Lorsque l’application définit le champ SQL_DESC_TYPE, le pilote vérifie que les autres champs qui spécifient le type sont valides et cohérents.  
  
 Si un appel de fonction qui définit un champ de descripteur échoue, le contenu du champ descripteur n’est pas défini après l’appel de la fonction failed.

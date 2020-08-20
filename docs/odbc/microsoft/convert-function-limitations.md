---
description: CONVERT, fonction - limitations
title: Limitations relatives aux fonctions CONVERT | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, CONVERT function limitations
- Convert function limitations [ODBC]
ms.assetid: 3c81fc58-57f0-4dd7-be16-2b146eb15cbc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 56c1d9704026511f68e76260bb4495acf1a872bf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466461"
---
# <a name="convert-function-limitations"></a>CONVERT, fonction - limitations
Les échecs de conversion de type entraînent la définition de la colonne affectée sur la valeur NULL.  
  
 Le type de données DATE et TIMESTAMP ne peut pas être converti en un autre type de données (ou lui-même) par la fonction CONVERT.

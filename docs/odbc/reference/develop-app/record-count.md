---
title: "Nombre d’enregistrements | Documents Microsoft"
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
- record count [ODBC]
- descriptors [ODBC], record count
ms.assetid: 46eec3cc-0ecc-4980-9020-fb74a9af5730
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 11c30fb4abfeab58b1a6ea650bc41ce1f72524e0
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="record-count"></a>Nombre d'enregistrements
Le champ d’en-tête SQL_DESC_COUNT d’un descripteur est l’index de base un de l’enregistrement le plus élevé numérotées qui contient les données. Ce champ n’est pas un nombre de toutes les colonnes ou les paramètres qui sont liés. Lorsqu’un descripteur est alloué, la valeur initiale de SQL_DESC_COUNT est 0.  
  
 Le pilote prend toute action nécessaire d’allouer et de gérer le stockage nécessaires pour conserver les informations de descripteur. L’application ne ne sont pas explicitement spécifier la taille d’un descripteur et allouer de nouveaux enregistrements. Lors de l’application fournit des informations pour un enregistrement de descripteur dont le numéro est supérieur à la valeur de SQL_DESC_COUNT, le pilote augmente automatiquement SQL_DESC_COUNT. Lorsque l’application annule l’enregistrement du descripteur de la plus élevée numérotées, le pilote diminue automatiquement SQL_DESC_COUNT pour contenir le nombre de l’enregistrement lié restante la plus élevée.

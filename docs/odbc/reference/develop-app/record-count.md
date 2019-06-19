---
title: Nombre d’enregistrements | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- record count [ODBC]
- descriptors [ODBC], record count
ms.assetid: 46eec3cc-0ecc-4980-9020-fb74a9af5730
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f8b0a6fc7aa5765d9373af33ab4fac0a4a07aac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63151236"
---
# <a name="record-count"></a>Nombre d'enregistrements
Le champ d’en-tête SQL_DESC_COUNT d’un descripteur est l’index de base un de l’enregistrement le plus élevé numérotés qui contient les données. Ce champ n’est pas un nombre de colonnes ou paramètres qui sont liés. Lorsqu’un descripteur est alloué, la valeur initiale de SQL_DESC_COUNT est 0.  
  
 Le pilote prend toute action nécessaire pour allouer et gérer le stockage nécessaire pour conserver les informations de descripteur. L’application ne pas explicitement spécifier la taille d’un descripteur de ni allouer de nouveaux enregistrements. Lors de l’application fournit des informations pour un enregistrement de descripteur dont le numéro est supérieur à la valeur de SQL_DESC_COUNT, le pilote augmente automatiquement SQL_DESC_COUNT. Lorsque l’application annule la liaison de l’enregistrement de descripteur portant un numéro le plus élevé, le pilote diminue automatiquement SQL_DESC_COUNT pour contenir le nombre de l’enregistrement lié restante la plus élevée.

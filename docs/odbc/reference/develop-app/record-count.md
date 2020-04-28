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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 28e503ae4602d87fc9138ed018ee1e95f135ec57
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81281815"
---
# <a name="record-count"></a>Nombre d'enregistrements
Le champ d’en-tête SQL_DESC_COUNT d’un descripteur est l’index de base un de l’enregistrement numéroté le plus élevé qui contient des données. Ce champ n’est pas le nombre de colonnes ou de paramètres liés. Lorsqu’un descripteur est alloué, la valeur initiale de SQL_DESC_COUNT est 0.  
  
 Le pilote effectue toute action nécessaire pour allouer et gérer le stockage dont il a besoin pour conserver les informations de descripteur. L’application ne spécifie pas explicitement la taille d’un descripteur et n’alloue pas de nouveaux enregistrements. Lorsque l’application fournit des informations pour un enregistrement de descripteur dont le nombre est supérieur à la valeur de SQL_DESC_COUNT, le pilote augmente automatiquement SQL_DESC_COUNT. Lorsque l’application dissocie l’enregistrement du descripteur numéroté le plus élevé, le pilote réduit automatiquement SQL_DESC_COUNT pour contenir le numéro de l’enregistrement dépendant le plus élevé.

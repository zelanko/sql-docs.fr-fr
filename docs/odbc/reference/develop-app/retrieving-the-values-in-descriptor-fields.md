---
title: "Récupération des valeurs dans les champs de descripteur | Documents Microsoft"
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
helpviewer_keywords: descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3f865e8372ba50cf2e6ee2bcfcf24863284cdd31
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Récupération des valeurs dans les champs de descripteur
Une application peut appeler **SQLGetDescField** pour obtenir un seul champ d’un enregistrement de descripteur. **SQLGetDescField** donne l’accès à l’application pour tous les champs de descripteur définis dans ODBC et également les champs définis par le pilote.  
  
 **SQLGetDescRec** peut être appelée pour récupérer les paramètres de plusieurs champs de descripteur qui affectent le type de données et de stockage des données de colonne ou du paramètre.

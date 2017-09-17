---
title: "Récupération des valeurs dans les champs de descripteur | Documents Microsoft"
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
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f86dd2e2cb625da359c677fedd297b510fee8593
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Récupération des valeurs dans les champs de descripteur
Une application peut appeler **SQLGetDescField** pour obtenir un seul champ d’un enregistrement de descripteur. **SQLGetDescField** donne l’accès à l’application pour tous les champs de descripteur définis dans ODBC et également les champs définis par le pilote.  
  
 **SQLGetDescRec** peut être appelée pour récupérer les paramètres de plusieurs champs de descripteur qui affectent le type de données et de stockage des données de colonne ou du paramètre.

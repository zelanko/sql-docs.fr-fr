---
title: Récupération des valeurs dans les champs de descripteur | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05d05eb20fdfa603748e4819d7f7583c6576a0b8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Récupération des valeurs dans les champs de descripteur
Une application peut appeler **SQLGetDescField** pour obtenir un seul champ d’un enregistrement de descripteur. **SQLGetDescField** donne l’accès à l’application pour tous les champs de descripteur définis dans ODBC et également les champs définis par le pilote.  
  
 **SQLGetDescRec** peut être appelée pour récupérer les paramètres de plusieurs champs de descripteur qui affectent le type de données et de stockage des données de colonne ou du paramètre.

---
title: Récupération des valeurs dans les champs de descripteur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 55d7017c659ca4d0b8094ed4a665d27c10b355f7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020448"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Récupération des valeurs dans les champs du descripteur
Une application peut appeler **SQLGetDescField** pour obtenir un seul champ d’un enregistrement de descripteur. **SQLGetDescField** donne l’accès aux applications pour tous les champs de descripteur définis dans ODBC et ainsi les champs définis par le pilote.  
  
 **SQLGetDescRec** peut être appelée pour récupérer les paramètres de plusieurs champs de descripteur qui affectent le type de données et stockage des données de colonne ou du paramètre.

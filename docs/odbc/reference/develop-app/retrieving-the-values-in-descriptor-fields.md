---
description: Récupération des valeurs dans les champs du descripteur
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a2118efe58b076287dd75192de679bdb74299435
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494647"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Récupération des valeurs dans les champs du descripteur
Une application peut appeler **SQLGetDescField** pour obtenir un champ unique d’un enregistrement de descripteur. **SQLGetDescField** permet à l’application d’accéder à tous les champs de descripteur définis dans ODBC, ainsi qu’aux champs définis par le pilote.  
  
 **SQLGetDescRec** peut être appelé pour récupérer les paramètres de plusieurs champs de descripteur qui affectent le type de données et le stockage des données de colonne ou de paramètre.

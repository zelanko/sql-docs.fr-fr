---
title: Récupération des valeurs dans les champs descripteurs (fr) Microsoft Docs
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
ms.openlocfilehash: 43467d19f3f2e576efa0402c4ba513e23da59390
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304320"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Récupération des valeurs dans les champs du descripteur
Une demande peut appeler **SQLGetDescField** pour obtenir un seul champ d’un enregistrement descripteur. **SQLGetDescField** donne à l’application l’accès à tous les champs descripteur définis dans ODBC, et aux champs définis par le conducteur ainsi.  
  
 **SQLGetDescRec** peut être appelé pour récupérer les paramètres de plusieurs champs descripteur qui affectent le type de données et le stockage des données de colonne ou de paramètres.

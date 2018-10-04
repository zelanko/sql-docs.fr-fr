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
manager: craigg
ms.openlocfilehash: ae95160a11a965e47845726748c2b9449a819e8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47775957"
---
# <a name="retrieving-the-values-in-descriptor-fields"></a>Récupération des valeurs dans les champs du descripteur
Une application peut appeler **SQLGetDescField** pour obtenir un seul champ d’un enregistrement de descripteur. **SQLGetDescField** donne l’accès aux applications pour tous les champs de descripteur définis dans ODBC et ainsi les champs définis par le pilote.  
  
 **SQLGetDescRec** peut être appelée pour récupérer les paramètres de plusieurs champs de descripteur qui affectent le type de données et stockage des données de colonne ou du paramètre.

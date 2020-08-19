---
description: Initialisation de champs de descripteur
title: Initialisation des champs de descripteur | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- initializing descriptor fields [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 1da157cb-8ea9-4a56-983b-1c45650217c5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2537e5e74c600c72368e46bda7640b881d9a34df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424651"
---
# <a name="initialization-of-descriptor-fields"></a>Initialisation de champs de descripteur
Lorsqu’un descripteur de ligne d’application est alloué, ses champs reçoivent les valeurs initiales comme indiqué dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). La valeur initiale du champ SQL_DESC_TYPE est SQL_DEFAULT. Cela permet un traitement standard des données de base de données pour la présentation à l’application. L’application peut spécifier un traitement différent des données en définissant des champs de l’enregistrement du descripteur.  
  
 La valeur initiale de SQL_DESC_ARRAY_SIZE dans l’en-tête du descripteur est 1. L’application peut modifier ce champ pour permettre l’extraction multiligne.  
  
 Le concept de valeur par défaut n’est pas valide pour les champs d’un IRD. Une application peut accéder aux champs d’un IRD uniquement lorsqu’une instruction préparée ou exécutée lui est associée.  
  
 Certains champs d’une IPD sont définis uniquement une fois que la IPD a été automatiquement remplie par le pilote. Si ce n’est pas le cas, ils ne sont pas définis. Ces champs sont SQL_DESC_CASE_SENSITIVE, SQL_DESC_FIXED_PREC_SCALE, SQL_DESC_TYPE_NAME, SQL_DESC_UNSIGNED et SQL_DESC_LOCAL_TYPE_NAME.

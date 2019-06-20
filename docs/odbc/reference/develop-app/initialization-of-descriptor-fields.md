---
title: L’initialisation des champs de descripteur | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d988099cad357254f04a79a8a6cccbbe4eb2768c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62446810"
---
# <a name="initialization-of-descriptor-fields"></a>Initialisation de champs de descripteur
Lorsqu’un descripteur de ligne d’application est alloué, ses champs recevant des valeurs initiales comme indiqué dans [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). La valeur initiale du champ SQL_DESC_TYPE est SQL_DEFAULT. Ainsi, pour un traitement standard des données de base pour la présentation à l’application. L’application peut spécifier un traitement différent des données en définissant les champs de l’enregistrement de descripteur.  
  
 La valeur initiale de SQL_DESC_ARRAY_SIZE dans l’en-tête de descripteur est 1. L’application peut modifier ce champ pour activer l’extraction de plusieurs ligne.  
  
 Le concept d’une valeur par défaut n’est pas valide pour les champs d’un IRD. Une application peut accéder aux champs d’un IRD uniquement s’il existe une instruction préparée ou exécutée associée.  
  
 Certains champs d’une infrastructure ou IPD sont définies uniquement une fois que l’IPD a été rempli automatiquement par le pilote. Dans le cas contraire, ils sont non définis. Ces champs sont SQL_DESC_CASE_SENSITIVE, SQL_DESC_FIXED_PREC_SCALE, SQL_DESC_TYPE_NAME, SQL_DESC_UNSIGNED et SQL_DESC_LOCAL_TYPE_NAME.

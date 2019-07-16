---
title: Les enregistrements de diagnostic | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- handles [ODBC], diagnostic records
- header records [ODBC]
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 92c73f9b-3ed7-410d-9cec-2771004aae60
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 90133b4a18876c52b9b6b6bffbe4c8c02c953e07
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039880"
---
# <a name="diagnostic-records"></a>Enregistrements de diagnostic
Associé à chaque environnement, connexion, l’instruction et handle de descripteur sont *les enregistrements de diagnostic*. Ces enregistrements contiennent des informations de diagnostic sur la dernière fonction appelée qui a utilisé un handle particulier. Les enregistrements sont remplacés uniquement quand une autre fonction est appelée à l’aide de ce descripteur. Il n’existe aucune limite au nombre d’enregistrements de diagnostic qui peuvent être stockés à tout moment.  
  
 Il existe deux types d’enregistrements de diagnostic : un *enregistrement d’en-tête* et zéro, un ou plusieurs *enregistrements d’état*. L’enregistrement d’en-tête est 0 ; les enregistrements d’état sont des enregistrements de 1 et versions ultérieures. Les enregistrements de diagnostic sont composées d’un nombre de champs distincts, qui sont différents pour l’enregistrement d’en-tête et les enregistrements d’état. En outre, les composants ODBC peuvent définir leurs propres champs d’enregistrement de diagnostic.  
  
 Bien que les enregistrements de diagnostic peuvent être considérées en tant que structures, n’est pas obligatoire pour qu’ils puissent être réellement les structures ; comment un pilote stocke les informations de diagnostic est spécifique au pilote.  
  
 Champs dans les enregistrements de diagnostic sont récupérés avec **SQLGetDiagField**. Le code SQLSTATE, numéro d’erreur natif et les champs de message de diagnostic d’enregistrements d’état peuvent être récupérées dans un seul appel avec **SQLGetDiagRec**.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Enregistrement d’en-tête](../../../odbc/reference/develop-app/header-record.md)  
  
-   [Enregistrements d’état](../../../odbc/reference/develop-app/status-records.md)

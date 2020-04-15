---
title: Mise en œuvre de SQLGetDiagRec et SQLGetDiagField (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], and SQLGetDiagRec
- SQLGetDiagRec function [ODBC], and SQLGetDiagField
- diagnostic information [ODBC], SqlGetDiagRec
- retrieving diagnostic information [ODBC]
ms.assetid: 11ba1857-b533-4517-8131-a2a8a0154a0a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4c090af19a9296e46e3036ca23f6c97298bcb1b8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300139"
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Implémentation de SQLGetDiagRec et de SQLGetDiagField
**SQLGetDiagRec** et **SQLGetDiagField** sont mis en œuvre par le gestionnaire de conducteur et chaque conducteur. Le gestionnaire de conducteur et chaque conducteur tiennent des dossiers diagnostiques pour chaque environnement, connexion, instruction et poignée descripteur, et ne les libèrent que lorsqu’une autre fonction est appelée avec cette poignée ou que la poignée est libérée.  
  
 Bien que le gestionnaire de pilote et chaque pilote doivent déterminer le premier enregistrement d’état en fonction du classement dans [Séquence des enregistrements d’état](../../../odbc/reference/develop-app/sequence-of-status-records.md), le gestionnaire de pilote détermine la séquence finale des enregistrements.  
  
 **SQLGetDiagRec** et **SQLGetDiagField** ne publient pas de dossiers diagnostiques sur eux-mêmes.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Règles de gestion des diagnostics](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Rôle du gestionnaire de pilotes](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Rôle du pilote](../../../odbc/reference/develop-app/role-of-the-driver.md)

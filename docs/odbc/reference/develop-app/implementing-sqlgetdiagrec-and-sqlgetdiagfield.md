---
title: Implémentation de SQLGetDiagRec et SQLGetDiagField | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a4b602d5ff4a94d2888395e6a62f03553fb50f98
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68216376"
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Implémentation de SQLGetDiagRec et de SQLGetDiagField
**SQLGetDiagRec** et **SQLGetDiagField** sont implémentées par le Gestionnaire de pilotes et chaque pilote. Le Gestionnaire de pilotes chaque pilote conservent des enregistrements de diagnostics pour chaque environnement, connexion, l’instruction et handle de descripteur et libérer ces enregistrements uniquement quand une autre fonction est appelée avec que handle ou le handle est libéré.  
  
 Bien que le Gestionnaire de pilotes et chaque pilote doivent déterminer le premier enregistrement de l’état selon les classements dans [séquence d’enregistrements d’état](../../../odbc/reference/develop-app/sequence-of-status-records.md), le Gestionnaire de pilote détermine la séquence finale d’enregistrements.  
  
 **SQLGetDiagRec** et **SQLGetDiagField** ne validez pas les enregistrements de diagnostic sur eux-mêmes.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Règles de gestion des diagnostics](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Rôle du gestionnaire de pilotes](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Rôle du pilote](../../../odbc/reference/develop-app/role-of-the-driver.md)

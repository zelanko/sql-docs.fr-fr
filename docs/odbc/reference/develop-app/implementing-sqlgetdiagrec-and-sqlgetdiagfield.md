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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4c090af19a9296e46e3036ca23f6c97298bcb1b8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300139"
---
# <a name="implementing-sqlgetdiagrec-and-sqlgetdiagfield"></a>Implémentation de SQLGetDiagRec et de SQLGetDiagField
**SQLGetDiagRec** et **SQLGetDiagField** sont implémentés par le gestionnaire de pilotes et chaque pilote. Le gestionnaire de pilotes et chaque pilote maintiennent les enregistrements de diagnostic pour chaque identificateur d’environnement, de connexion, d’instruction et de descripteur, et ne libèrent ces enregistrements que lorsqu’une autre fonction est appelée avec ce handle ou lorsque le descripteur est libéré.  
  
 Bien que le gestionnaire de pilotes et chaque pilote doivent déterminer le premier enregistrement d’État en fonction des classements dans l' [ordre des enregistrements d’État](../../../odbc/reference/develop-app/sequence-of-status-records.md), le gestionnaire de pilotes détermine la dernière séquence d’enregistrements.  
  
 **SQLGetDiagRec** et **SQLGetDiagField** ne publient pas d’enregistrements de diagnostic sur eux-mêmes.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Règles de gestion des diagnostics](../../../odbc/reference/develop-app/diagnostic-handling-rules.md)  
  
-   [Rôle du gestionnaire de pilotes](../../../odbc/reference/develop-app/role-of-the-driver-manager.md)  
  
-   [Rôle du pilote](../../../odbc/reference/develop-app/role-of-the-driver.md)

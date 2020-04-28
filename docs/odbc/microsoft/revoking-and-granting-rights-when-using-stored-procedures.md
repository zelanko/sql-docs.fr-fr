---
title: Révocation et octroi de droits lors de l’utilisation de procédures stockées | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 24070039-03ab-4623-a681-6308802eb399
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 469e6f0fdc6794e3bd163844e43821798aa4a617
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303985"
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Révocation et octroi de droits lors de l’utilisation de procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le pilote Microsoft ODBC pour Oracle retourne le message d’erreur suivant lorsque des droits d’utilisateur sont accordés, puis révoqués sur une table accessible par une procédure stockée :  
  
 SQL_ERROR =-1  
  
 szErrorMsg = "[Microsoft] [pilote ODBC pour Oracle] nombre incorrect de paramètres"  
  
 szErrorMsg = "[Microsoft] [pilote ODBC pour Oracle] erreur de syntaxe ou violation d’accès"  
  
 L’appel à la fonction Oracle OCI Odessp () échoue dans ce scénario, mais il est nécessaire pour implémenter les paramètres par défaut. Une fois les autorisations de la table sous-jacente modifiées, la procédure stockée doit être recompilée avant d’être réexécutée.

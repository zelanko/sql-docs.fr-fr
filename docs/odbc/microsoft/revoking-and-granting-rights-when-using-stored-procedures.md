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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 91fcf722554fe1840465329e707c792a6bbab6db
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67987954"
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Révocation et octroi de droits lors de l’utilisation de procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le pilote Microsoft ODBC pour Oracle retourne le message d’erreur suivant lorsque des droits d’utilisateur sont accordés, puis révoqués sur une table accessible par une procédure stockée :  
  
 SQL_ERROR =-1  
  
 szErrorMsg = "[Microsoft] [pilote ODBC pour Oracle] nombre incorrect de paramètres"  
  
 szErrorMsg = "[Microsoft] [pilote ODBC pour Oracle] erreur de syntaxe ou violation d’accès"  
  
 L’appel à la fonction Oracle OCI Odessp () échoue dans ce scénario, mais il est nécessaire pour implémenter les paramètres par défaut. Une fois les autorisations de la table sous-jacente modifiées, la procédure stockée doit être recompilée avant d’être réexécutée.

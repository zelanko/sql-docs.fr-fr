---
title: Révoquer et accorder des droits lors de l’utilisation des procédures stockées .fr Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303985"
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Révocation et octroi de droits lors de l’utilisation de procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le pilote Microsoft ODBC pour Oracle renvoie le message d’erreur suivant lorsque les droits de l’utilisateur sont accordés, puis révoqué sur une table accessible par une procédure stockée :  
  
 SQL_ERROR-1  
  
 szErrorMsg"[Microsoft][ODBC driver for Oracle]Mauvais nombre de paramètres"  
  
 szErrorMsg"[Microsoft][ODBC driver for Oracle]Syntax error or access violation"  
  
 L’appel à la fonction Oracle OCI Odessp() échoue dans ce scénario, mais est nécessaire afin de mettre en œuvre les paramètres par défaut. Une fois que les autorisations de table sous-jacentes sont modifiées, la procédure stockée doit être recompilée avant de l’exécuter à nouveau.

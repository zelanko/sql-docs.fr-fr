---
title: Révocation et l’octroi des droits lors de l’utilisation de procédures stockées | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: e881201e4653a168faff2fa438be19c1ca37e9b1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127963"
---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Révocation et octroi de droits lors de l’utilisation de procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Le pilote Microsoft ODBC pour Oracle retourne le message d’erreur suivant lorsque des droits d’utilisateur sont accordées et révoquées puis sur une table accédée par une procédure stockée :  
  
 SQL_ERROR=-1  
  
 szErrorMsg = « [Microsoft] [pilote ODBC pour Oracle] nombre de paramètres incorrect »  
  
 szErrorMsg = « [Microsoft] [pilote ODBC pour Oracle] syntaxe ou violation d’accès »  
  
 L’appel à la fonction Oracle OCI Odessp() échoue dans ce scénario, mais est nécessaire pour implémenter les paramètres par défaut. Une fois que les autorisations de la table sous-jacente sont modifiées, la procédure stockée doit être recompilée avant de l’exécuter à nouveau.

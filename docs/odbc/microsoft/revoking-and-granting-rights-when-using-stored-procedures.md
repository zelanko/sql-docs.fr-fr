---
title: "Révocation et accorder des droits lors de l’utilisation de procédures stockées | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stored procedures [ODBC], ODBC driver for Oracle
- ODBC driver for Oracle [ODBC], stored procedures
ms.assetid: 24070039-03ab-4623-a681-6308802eb399
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 67bad57e201d10c5eb29aafb19fa9f513c43b172
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="revoking-and-granting-rights-when-using-stored-procedures"></a>Révocation et accorder des droits lors de l’utilisation de procédures stockées
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Le pilote Microsoft ODBC pour Oracle retourne le message d’erreur suivant lorsque des droits d’utilisateur sont accordées et puis révoquées sur une table accédée par une procédure stockée :  
  
 SQL_ERROR =-1  
  
 szErrorMsg = « [Microsoft] [pilote ODBC pour Oracle] nombre de paramètres incorrect »  
  
 szErrorMsg = « [Microsoft] [pilote ODBC pour Oracle] syntaxe ou violation d’accès »  
  
 L’appel à la fonction Oracle OCI Odessp() échoue dans ce scénario, mais est nécessaire pour implémenter les paramètres par défaut. Une fois les autorisations de la table sous-jacente sont modifiées, la procédure stockée doit être recompilée avant d’exécuter à nouveau.

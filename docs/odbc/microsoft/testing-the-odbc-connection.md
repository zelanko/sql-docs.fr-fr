---
title: Test de la connexion ODBC | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing connections [ODBC]
- ODBC driver for Oracle [ODBC], testing connections
ms.assetid: 5e671665-2aba-49a7-8871-70784d8b3cc9
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4b4abf7893e6d09d93d8adda6c609412c7572727
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="testing-the-odbc-connection"></a>Test de la connexion ODBC
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Lors de la résolution des problèmes d’accès ODBC pour Oracle 7.x et les serveurs Oracle8 SGBDR, il peut être nécessaire vérifier que le sous-jacent SQL * Net et adaptateurs de protocole Oracle sont installés correctement. Pour ce faire, utilisez l’utilitaire fourni par Oracle Nettest.exe dans le répertoire Orawin\Bin.  
  
 Nettest est un utilitaire simple qui tente de se connecter au serveur sélectionné à l’aide uniquement installé SQL * Net logiciel qui fait partie du client Oracle. L’utilitaire vous invite à entrer un nom d’utilisateur, mot de passe et TNS chaîne de connexion. Si le client Oracle est installé correctement, l’utilitaire affiche simplement « Ping réussi. » Si la connexion n’a pas réussie, vous devez consulter un administrateur de base de données.

---
title: Interopérabilité | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC]
- interoperability [ODBC], about interoperability
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31b20a696c601ff91c591e4c717f468beca34e36
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306220"
---
# <a name="interoperability"></a>Interopérabilité
L' *interopérabilité* est la capacité d’une application unique à fonctionner avec de nombreux SGBD différents. La nécessité d’écrire des applications génériques et interopérables était l’un des principaux facteurs qui conduisent au développement d’ODBC. Toutefois, l’interopérabilité n’est pas un chemin d’accès simple, suivi de « non interopérable » à « entièrement interopérable ». Le chemin d’accès comporte de nombreuses branches, chacune nécessitant des compromis entre les fonctionnalités, la vitesse, la complexité du code et le temps de développement.  
  
 Le processus d’écriture d’une application interopérable suit plusieurs étapes :  
  
1.  Déterminer si l’application utilisera ODBC.  
  
2.  Le choix d’un niveau d’interopérabilité et la décision des compromis sont nécessaires pour atteindre ce niveau.  
  
3.  Écrire du code interopérable et le tester aussi complètement que possible.  
  
 Il convient de noter que l’interopérabilité est principalement le domaine du writer de l’application. Les pilotes sont conçus pour fonctionner avec un SGBD unique et, par définition, ne sont pas interopérables. Ils jouent un rôle dans l’interopérabilité en implémentant et en exposant correctement ODBC sur un SGBD unique.  
  
 Cette section contient les rubriques suivantes :  
  
-   [ODBC est-il la réponse ?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Choix d’un niveau d’interopérabilité](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Détermination des SGBD et des pilotes cibles](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [Considérations sur les fonctionnalités de base de données à utiliser](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Longueur du cycle produit](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Écriture d’une application interopérable](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Test des applications interopérables](../../../odbc/reference/develop-app/testing-interoperable-applications.md)

---
title: Interopérabilité Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306220"
---
# <a name="interoperability"></a>Interopérabilité
*L’interopérabilité* est la capacité d’une seule application à fonctionner avec de nombreux DBMS différents. La nécessité d’écrire des applications génériques et interopérables a été l’un des principaux facteurs qui ont mené au développement d’ODBC. Cependant, l’interopérabilité n’est pas un simple chemin suivi de « non interopérable » à « complètement interopérable ». Le chemin a de nombreuses branches, et chacun nécessite des compromis entre les caractéristiques, la vitesse, la complexité du code, et le temps de développement.  
  
 Le processus de rédaction d’une demande interopérable suit plusieurs étapes :  
  
1.  Décider si l’application utilisera ODBC.  
  
2.  Choisir un niveau d’interopérabilité et décider quels compromis sont nécessaires pour atteindre ce niveau.  
  
3.  Rédaction de code interopérable et test de test aussi pleinement que possible.  
  
 Il convient de noter que l’interopérabilité est principalement le domaine de l’auteur de l’application. Les conducteurs sont conçus pour travailler avec un seul DBMS et, par définition, ne sont pas interopérables. Ils jouent un rôle dans l’interopérabilité en mettant correctement en œuvre et en exposant ODBC sur un seul DBMS.  
  
 Cette section contient les rubriques suivantes :  
  
-   [ODBC est-il la réponse ?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Choix d’un niveau d’interopérabilité](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Détermination des SGBD et des pilotes cibles](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [Considérations sur les fonctionnalités de base de données à utiliser](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Longueur du cycle produit](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Écriture d’une application interopérable](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Test des applications interopérables](../../../odbc/reference/develop-app/testing-interoperable-applications.md)

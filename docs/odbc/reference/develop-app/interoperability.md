---
title: L’interopérabilité | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interoperability [ODBC]
- interoperability [ODBC], about interoperability
ms.assetid: 43b7c849-9d59-4002-9977-9e2c8730b859
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4e7bbec995af3475208afa328c163dbbd42f0e46
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="interoperability"></a>Interopérabilité
*L’interopérabilité* désigne la capacité d’une seule application de fonctionner avec nombreux SGBD différents. La nécessité d’écrire des applications interopérables génériques a été un des principaux facteurs menant au développement d’ODBC. Toutefois, l’interopérabilité n’est pas un chemin d’accès simple suivi de « pas interopérable » à « entièrement interopérables. » Le chemin d’accès possède de nombreuses branches, et chacune nécessite le compromis entre les fonctionnalités, la vitesse, la complexité du code et temps de développement.  
  
 Le processus d’écriture d’une application interopérable plusieurs étapes :  
  
1.  Décider si l’application utilise ODBC.  
  
2.  Choix d’un niveau d’interopérabilité et de décider quels compromis sont nécessaires pour atteindre ce niveau.  
  
3.  L’écriture de code interopérable et testez autant que possible.  
  
 Il convient de noter que l’interopérabilité est principalement le domaine de l’enregistreur de l’application. Les pilotes sont conçus pour fonctionner avec un SGBD unique et, par définition, ne sont pas interopérables. Ils jouent un rôle dans l’interopérabilité en implémentant et en exposant ODBC via un SGBD unique correctement.  
  
 Cette section contient les rubriques suivantes.  
  
-   [ODBC est-il la réponse ?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Choix d’un niveau d’interopérabilité](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Détermination des SGBD et des pilotes cibles](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [Considérations sur les fonctionnalités de base de données à utiliser](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Longueur du cycle produit](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Écriture d’une application interopérable](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Test des applications interopérables](../../../odbc/reference/develop-app/testing-interoperable-applications.md)

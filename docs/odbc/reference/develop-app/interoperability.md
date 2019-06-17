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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8d5e4fbee458bec88461d3e2945a466c848d3345
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62446486"
---
# <a name="interoperability"></a>Interopérabilité
*Interopérabilité* est la capacité d’une seule application pour fonctionner avec nombreux SGBD différents. La nécessité d’écrire des applications interopérables, génériques a été un des principaux facteurs menant au développement de ODBC. Toutefois, l’interopérabilité n’est pas un chemin d’accès simple suivi de « non interopérable » à « totalement interopérable ». Le chemin d’accès possède de nombreuses branches, et chacun nécessite des compromis entre les fonctionnalités, la vitesse, la complexité du code et temps de développement.  
  
 Le processus d’écriture d’une application interopérable de plusieurs étapes :  
  
1.  Décider si l’application utilise ODBC.  
  
2.  Choix d’un niveau d’interopérabilité et de décider quels compromis sont nécessaires pour atteindre ce niveau.  
  
3.  Écriture de code interopérable et du test d’aussi complète que possible.  
  
 Il convient de noter que l’interopérabilité est principalement le domaine de l’enregistreur de l’application. Pilotes sont conçus pour fonctionner avec un SGBD unique et, par définition, ne sont pas interopérables. Ils jouent un rôle dans l’interopérabilité en implémentant correctement et d’exposition d’ODBC sur un système SGBD unique.  
  
 Cette section contient les rubriques suivantes.  
  
-   [ODBC est-il la réponse ?](../../../odbc/reference/develop-app/is-odbc-the-answer.md)  
  
-   [Choix d’un niveau d’interopérabilité](../../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)  
  
-   [Détermination des SGBD et des pilotes cibles](../../../odbc/reference/develop-app/determining-the-target-dbmss-and-drivers.md)  
  
-   [Considérations sur les fonctionnalités de base de données à utiliser](../../../odbc/reference/develop-app/considering-database-features-to-use.md)  
  
-   [Longueur du cycle produit](../../../odbc/reference/develop-app/length-of-the-product-cycle.md)  
  
-   [Écriture d’une application interopérable](../../../odbc/reference/develop-app/writing-an-interoperable-application.md)  
  
-   [Test des applications interopérables](../../../odbc/reference/develop-app/testing-interoperable-applications.md)

---
title: "Vue d’ensemble ODBC | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC [ODBC]
- ODBC [ODBC], about ODBC
ms.assetid: 233315bd-2b7f-4b20-9978-e920e1ea9a07
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 20767544a83219c6583eaf03a78e240e15e19be2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-overview"></a>Vue d’ensemble d’ODBC
Connectivité de base de données ouverte (ODBC) est une interface de programmation largement répandue d’application (API) pour l’accès de la base de données. Il est basé sur les spécifications de l’Interface de niveau d’appel (CLI) d’Open Group et de la norme ISO/IEC pour l’API de la base de données et utilise le langage SQL (Structured Query) en tant que son langage d’accès de base de données.  
  
 ODBC est conçu pour maximum *interopérabilité* -autrement dit, la possibilité d’une application unique pour accéder aux systèmes de gestion de l’autre base de données (SGBD) avec le même code source. Les applications de base de données appellent des fonctions dans l’interface ODBC, qui sont implémentées dans des modules spécifiques à la base de données appelées *pilotes*. L’utilisation des pilotes isole les applications à partir des appels spécifiques à la base de données de la même façon que les pilotes d’imprimante isolent des programmes de traitement de texte à partir des commandes spécifiques à l’imprimante. Étant donné que les pilotes sont chargés au moment de l’exécution, un utilisateur doit uniquement ajouter un nouveau pilote pour accéder à un nouveau SGBD ; Il n’est pas nécessaire de recompilation ou de rétablir les liens de l’application.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Pourquoi ODBC a été créé ?](../../odbc/reference/why-was-odbc-created.md)  
  
-   [Nouveautés d’ODBC ?](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC et l’interface CLI Standard](../../odbc/reference/odbc-and-the-standard-cli.md)


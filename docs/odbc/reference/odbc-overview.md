---
title: Vue d’ensemble ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC]
- ODBC [ODBC], about ODBC
ms.assetid: 233315bd-2b7f-4b20-9978-e920e1ea9a07
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b064436dae6cb2f3d5f37fa02ab57a1e4a3f015
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47801537"
---
# <a name="odbc-overview"></a>Vue d’ensemble d’ODBC
Open Database Connectivity (ODBC) est une interface de programmation d’application largement acceptées (API) pour l’accès de base de données. Il est basé sur les spécifications de l’Interface de niveau d’appel (CLI) à partir d’Open Group et ISO/IEC pour l’API de la base de données et utilise le langage SQL (Structured Query) en tant que son langage d’accès de base de données.  
  
 ODBC est conçu pour maximum *interopérabilité* -autrement dit, la possibilité d’une application unique pour accéder aux systèmes de gestion de l’autre base de données (SGBD) avec le même code source. Applications de base de données appellent des fonctions dans l’interface ODBC, qui sont implémentées dans des modules spécifiques à la base de données appelées *pilotes*. L’utilisation de pilotes isole les applications à partir des appels spécifiques à la base de données de la même façon que les pilotes d’imprimante isolent des programmes de traitement de texte à partir des commandes spécifiques à l’imprimante. Étant donné que les pilotes sont chargés au moment de l’exécution, un utilisateur a uniquement ajouter un nouveau pilote pour accéder à un nouveau SGBD ; Il n’est pas nécessaire de recompiler ni de relier l’application.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Pourquoi ODBC a-t-il été créé ?](../../odbc/reference/why-was-odbc-created.md)  
  
-   [Qu’est-ce que ODBC ?](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC et l’interface CLI standard](../../odbc/reference/odbc-and-the-standard-cli.md)

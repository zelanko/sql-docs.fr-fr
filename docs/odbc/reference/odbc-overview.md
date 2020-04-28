---
title: Vue d’ensemble d’ODBC | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a0515a882cd7d1c97a60e9262942bd7c397b0b2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298289"
---
# <a name="odbc-overview"></a>Vue d’ensemble d’ODBC
L’interface Open Database Connectivity (ODBC) est une interface de programmation d’applications (API) largement acceptée pour l’accès à des bases de données. Il est basé sur les spécifications de l’interface de niveau d’appel (CLI) de Open Group et ISO/IEC pour les API de base de données et utilise langage SQL (SQL) comme langage d’accès à la base de données.  
  
 ODBC est conçu pour une *interopérabilité* maximale, c’est-à-dire la capacité d’une application unique à accéder à différents systèmes de gestion de base de données (SGBD) avec le même code source. Les applications de base de données appellent des fonctions dans l’interface ODBC, qui sont implémentées dans des modules spécifiques à la base de données appelés *pilotes*. L’utilisation de pilotes isole les applications des appels spécifiques à la base de données de la même façon que les pilotes d’imprimante isolent les programmes de traitement de texte des commandes spécifiques à l’imprimante. Étant donné que les pilotes sont chargés au moment de l’exécution, un utilisateur doit uniquement ajouter un nouveau pilote pour accéder à un nouveau SGBD. Il n’est pas nécessaire de recompiler ou de réassocier l’application.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Pourquoi ODBC a-t-il été créé ?](../../odbc/reference/why-was-odbc-created.md)  
  
-   [Qu’est-ce que ODBC ?](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC et l’interface CLI standard](../../odbc/reference/odbc-and-the-standard-cli.md)

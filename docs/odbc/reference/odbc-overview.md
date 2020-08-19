---
description: Vue d’ensemble d’ODBC
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
ms.openlocfilehash: 13f34a1ef329957854a8b33916b6b29506fc0ad9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421313"
---
# <a name="odbc-overview"></a>Vue d’ensemble d’ODBC
L’interface Open Database Connectivity (ODBC) est une interface de programmation d’applications (API) largement acceptée pour l’accès à des bases de données. Il est basé sur les spécifications de l’interface de niveau d’appel (CLI) de Open Group et ISO/IEC pour les API de base de données et utilise langage SQL (SQL) comme langage d’accès à la base de données.  
  
 ODBC est conçu pour une *interopérabilité* maximale, c’est-à-dire la capacité d’une application unique à accéder à différents systèmes de gestion de base de données (SGBD) avec le même code source. Les applications de base de données appellent des fonctions dans l’interface ODBC, qui sont implémentées dans des modules spécifiques à la base de données appelés *pilotes*. L’utilisation de pilotes isole les applications des appels spécifiques à la base de données de la même façon que les pilotes d’imprimante isolent les programmes de traitement de texte des commandes spécifiques à l’imprimante. Étant donné que les pilotes sont chargés au moment de l’exécution, un utilisateur doit uniquement ajouter un nouveau pilote pour accéder à un nouveau SGBD. Il n’est pas nécessaire de recompiler ou de réassocier l’application.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Pourquoi ODBC a-t-il été créé ?](../../odbc/reference/why-was-odbc-created.md)  
  
-   [Qu’est-ce que ODBC ?](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC et l’interface CLI standard](../../odbc/reference/odbc-and-the-standard-cli.md)

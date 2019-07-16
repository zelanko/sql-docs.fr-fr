---
title: Le Gestionnaire de pilotes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver manager [ODBC]
- ODBC architecture [ODBC], driver manager
- driver manager [ODBC], about driver manager
- ODBC driver manager [ODBC]
ms.assetid: 559e4de1-16c9-4998-94f5-6431122040cd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 659678451c368df0b6a213e54cf7edaedfc29bd1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039327"
---
# <a name="the-driver-manager"></a>Le gestionnaire de pilotes
Le *Gestionnaire de pilotes* est une bibliothèque qui gère la communication entre les applications et pilotes. Par exemple, sur les plateformes de Microsoft® Windows®, le Gestionnaire de pilotes est une bibliothèque de liens dynamiques (DLL) qui est écrite par Microsoft et peut être redistribuée par les utilisateurs du MDAC 2.8 SP1 SDK redistribuable.  
  
 Le Gestionnaire de pilotes existe principalement par souci de commodité pour les créateurs d’applications et résout de nombreux problèmes communs à toutes les applications. Ceux-ci incluent déterminer quel pilote charger selon un nom de source de données, le chargement et déchargement des pilotes et appeler des fonctions dans les pilotes.  
  
 Pour voir pourquoi ce dernier est un problème, examinez ce qui se passerait si l’application appelle des fonctions dans le pilote directement. À moins que l’application a été liée directement à un pilote spécifique, il fallait créer une table de pointeurs vers les fonctions de ce pilote et appeler ces fonctions en pointeur. Avec le même code pour plus d’un pilote à la fois ajouteriez un autre niveau de complexité. L’application serait vous devez tout d’abord définir un pointeur de fonction pour pointer vers la fonction correcte dans le pilote correct et appelle ensuite la fonction via ce pointeur.  
  
 Le Gestionnaire de pilotes résout ce problème en fournissant un emplacement unique pour appeler chaque fonction. L’application est liée aux fonctions ODBC Gestionnaire de pilotes et des appels dans le Gestionnaire de pilotes, pas le pilote. L’application identifie la source de données et de pilote cible avec un *handle de connexion*. Lorsqu’il charge un pilote, le Gestionnaire de pilotes crée un tableau de pointeurs vers les fonctions de ce pilote. Il utilise le handle de connexion transmis par l’application pour trouver l’adresse de la fonction dans le pilote de la cible et appelle cette fonction par adresse.  
  
 La plupart du temps, le Gestionnaire de pilotes transmet simplement les appels de fonction à partir de l’application pour le pilote correct. Toutefois, il implémente également certaines fonctions (**SQLDataSources**, **SQLDrivers**, et **SQLGetFunctions**) et effectue la vérification des erreurs de base. Par exemple, le Gestionnaire de pilotes vérifie que les handles ne sont pas des pointeurs null, que les fonctions sont appelées dans le bon ordre, et que certains arguments de fonction sont valides. Pour obtenir une description complète des erreurs vérifiées par le Gestionnaire de pilotes, consultez la section de référence pour chaque fonction et [annexe b : Tableaux des transitions d’état ODBC](../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Le rôle majeur final du Gestionnaire de pilotes est le chargement et déchargement des pilotes. L’application charge et décharge uniquement le Gestionnaire de pilotes. Lorsqu’il souhaite utiliser un pilote spécifique, il appelle une fonction de connexion (**SQLConnect**, **SQLDriverConnect**, ou **SQLBrowseConnect**) dans le Gestionnaire de pilotes et spécifie le nom de source de données particulière ou de pilote, tels que « Comptabilité » ou « SQL Server ». Le Gestionnaire de pilotes à l’aide de ce nom, recherche dans les informations de source de données pour le nom de fichier du pilote, telles que Sqlsrvr.dll. Il charge le pilote (en supposant qu’il n’est pas déjà chargé), stocke l’adresse de chaque fonction dans le pilote, puis appelle la fonction de connexion dans le pilote, puis initialise lui-même et se connecte à la source de données.  
  
 Lorsque l’application est effectuée à l’aide du pilote, il appelle **SQLDisconnect** dans le Gestionnaire de pilotes. Le Gestionnaire de pilotes appelle cette fonction dans le pilote, se déconnecte de la source de données. Toutefois, le Gestionnaire de pilotes conserve le pilote en mémoire dans le cas où l’application se reconnecte à ce dernier. Il décharge le pilote uniquement lorsque l’application libère la connexion utilisée par le pilote utilise la connexion pour un pilote différent, et aucune autre connexion n’utilisent le pilote. Pour obtenir une description complète du rôle du Gestionnaire de pilotes dans le chargement et déchargement des pilotes, consultez [rôle du Gestionnaire de pilotes dans le processus de connexion](../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).

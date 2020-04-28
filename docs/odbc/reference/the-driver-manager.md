---
title: Gestionnaire de pilotes | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 686a2b9673fb392f969a42f4cc86dd95a95668a6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81286793"
---
# <a name="the-driver-manager"></a>Le gestionnaire de pilotes
Le *Gestionnaire de pilotes* est une bibliothèque qui gère la communication entre les applications et les pilotes. Par exemple, sur les plateformes Microsoft® Windows®, le gestionnaire de pilotes est une bibliothèque de liens dynamiques (DLL) écrite par Microsoft et peut être redistribuée par les utilisateurs du kit de développement logiciel (SDK) MDAC 2,8 SP1 redistribuable.  
  
 Le gestionnaire de pilotes existe principalement pour faciliter les créateurs d’applications et résout un certain nombre de problèmes communs à toutes les applications. Celles-ci incluent la détermination du pilote à charger en fonction d’un nom de source de données, le chargement et le déchargement des pilotes, et l’appel de fonctions dans les pilotes.  
  
 Pour comprendre pourquoi ce dernier est un problème, réfléchissez à ce qui se passerait si l’application appelait des fonctions dans le pilote directement. À moins que l’application n’ait été directement liée à un pilote particulier, elle doit créer un tableau de pointeurs vers les fonctions de ce pilote et appeler ces fonctions par pointeur. L’utilisation du même code pour plusieurs pilotes à la fois peut ajouter un autre niveau de complexité. L’application doit tout d’abord définir un pointeur de fonction pour pointer vers la fonction correcte dans le pilote approprié, puis appeler la fonction par le biais de ce pointeur.  
  
 Le gestionnaire de pilotes résout ce problème en fournissant un emplacement unique pour appeler chaque fonction. L’application est liée au gestionnaire de pilotes et appelle les fonctions ODBC dans le gestionnaire de pilotes, et non le pilote. L’application identifie le pilote cible et la source de données avec un *handle de connexion*. Lors du chargement d’un pilote, le gestionnaire de pilotes crée un tableau de pointeurs vers les fonctions de ce pilote. Elle utilise le handle de connexion passé par l’application pour Rechercher l’adresse de la fonction dans le pilote cible et appelle cette fonction par adresse.  
  
 Dans la plupart des cas, le gestionnaire de pilotes transmet uniquement les appels de fonction de l’application au pilote approprié. Toutefois, elle implémente également certaines fonctions (**SQLDataSources**, **SQLDrivers**et **SQLGetFunctions**) et effectue une vérification des erreurs de base. Par exemple, le gestionnaire de pilotes vérifie que les handles ne sont pas des pointeurs null, que les fonctions sont appelées dans l’ordre correct et que certains arguments de fonction sont valides. Pour obtenir une description complète des erreurs vérifiées par le gestionnaire de pilotes, consultez la section de référence pour chaque fonction et [annexe B : tables de transition d’État ODBC](../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Le rôle majeur final du gestionnaire de pilotes est le chargement et le déchargement des pilotes. L’application charge et décharge uniquement le gestionnaire de pilotes. Lorsqu’il souhaite utiliser un pilote particulier, il appelle une fonction de connexion (**SQLConnect**, **SQLDriverConnect**ou **SQLBrowseConnect**) dans le gestionnaire de pilotes et spécifie le nom d’une source de données ou d’un pilote particulier, par exemple « comptabilité » ou « SQL Server ». À l’aide de ce nom, le gestionnaire de pilotes recherche le nom de fichier du pilote, par exemple sqlsrvr. dll, dans les informations de la source de données. Il charge ensuite le pilote (en supposant qu’il n’est pas déjà chargé), stocke l’adresse de chaque fonction dans le pilote, puis appelle la fonction de connexion dans le pilote, qui s’initialise ensuite et se connecte à la source de données.  
  
 Lorsque l’application est exécutée à l’aide du pilote, elle appelle **SQLDisconnect** dans le gestionnaire de pilotes. Le gestionnaire de pilotes appelle cette fonction dans le pilote, qui se déconnecte de la source de données. Toutefois, le gestionnaire de pilotes conserve le pilote en mémoire au cas où l’application se reconnecte. Elle décharge le pilote uniquement lorsque l’application libère la connexion utilisée par le pilote ou utilise la connexion pour un autre pilote, et qu’aucune autre connexion n’utilise le pilote. Pour obtenir une description complète du rôle du gestionnaire de pilotes dans le chargement et le déchargement des pilotes, consultez [rôle du gestionnaire de pilotes dans le processus de connexion](../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).

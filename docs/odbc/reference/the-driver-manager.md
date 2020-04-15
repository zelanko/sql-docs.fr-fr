---
title: Le gestionnaire de chauffeurs (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286793"
---
# <a name="the-driver-manager"></a>Le gestionnaire de pilotes
Le *Driver Manager* est une bibliothèque qui gère la communication entre les applications et les conducteurs. Par exemple, sur les plates-formes ® Microsoft® Windows, le Driver Manager est une bibliothèque à liaison dynamique (DLL) qui est écrite par Microsoft et peut être redistribuée par les utilisateurs du MDAC 2.8 SP1 SDK redistribuable.  
  
 Le Driver Manager existe principalement comme une commodité pour les rédacteurs d’applications et résout un certain nombre de problèmes communs à toutes les applications. Il s’agit notamment de déterminer quel conducteur charger en fonction d’un nom de source de données, le chargement et le déchargement des conducteurs, et les fonctions d’appel dans les conducteurs.  
  
 Pour voir pourquoi ce dernier est un problème, pensez à ce qui se passerait si l’application appelait directement les fonctions dans le conducteur. À moins que l’application ne soit directement liée à un conducteur particulier, elle devrait constituer un tableau de pointeurs aux fonctions de ce conducteur et appeler ces fonctions par pointeur. L’utilisation du même code pour plus d’un pilote à la fois ajouterait encore un autre niveau de complexité. L’application devrait d’abord définir un pointeur de fonction pour pointer vers la fonction correcte dans le bon pilote, puis appeler la fonction à travers ce pointeur.  
  
 Le Driver Manager résout ce problème en fournissant un seul endroit pour appeler chaque fonction. L’application est liée au gestionnaire de conducteur et appelle les fonctions ODBC dans le gestionnaire de conducteur, pas le conducteur. L’application identifie le conducteur cible et la source de données avec une *poignée de connexion*. Lorsqu’il charge un conducteur, le gestionnaire de conducteur construit une table de pointeurs aux fonctions de ce conducteur. Il utilise la poignée de connexion passée par l’application pour trouver l’adresse de la fonction dans le pilote cible et appelle cette fonction par adresse.  
  
 Pour la plupart, le Driver Manager passe simplement les appels de fonction de l’application au bon conducteur. Cependant, il met également en œuvre certaines fonctions (**SQLDataSources**, **SQLDrivers**, et **SQLGetFunctions**) et effectue la vérification des erreurs de base. Par exemple, les vérifications du gestionnaire de conducteur qui s’occupent ne sont pas des pointeurs nuls, que les fonctions sont appelées dans le bon ordre et que certains arguments de fonction sont valides. Pour une description complète des erreurs vérifiées par le gestionnaire de pilote, consultez la section de référence pour chaque fonction et [l’annexe B : ODBC State Transition Tables](../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Le dernier rôle majeur du gestionnaire de conducteur est le chargement et le déchargement des conducteurs. L’application charge et décharge uniquement le Driver Manager. Lorsqu’il souhaite utiliser un pilote particulier, il appelle une fonction de connexion (**SQLConnect**, **SQLDriverConnect**, ou **SQLBrowseConnect**) dans le Driver Manager et spécifie le nom d’une source de données ou d’un pilote particulier, comme « Comptabilité » ou « Serveur SQL ». À l’aide de ce nom, le gestionnaire de conducteur recherche les informations de source de données pour le nom du fichier du conducteur, comme Sqlsrvr.dll. Il charge ensuite le conducteur (en supposant qu’il n’est pas déjà chargé), stocke l’adresse de chaque fonction dans le conducteur, et appelle la fonction de connexion dans le conducteur, qui s’est ensuite parasumé et se connecte à la source de données.  
  
 Lorsque l’application est terminée à l’aide du conducteur, elle appelle **SQLDisconnect** dans le gestionnaire de conducteur. Le Gestionnaire de pilote appelle cette fonction dans le conducteur, qui se déconnecte de la source de données. Toutefois, le Driver Manager garde le pilote en mémoire au cas où l’application se reconnecterait à elle. Il décharge le conducteur seulement lorsque l’application libère la connexion utilisée par le conducteur ou utilise la connexion pour un pilote différent, et aucune autre connexion n’utilise le conducteur. Pour une description complète du rôle du gestionnaire de conducteur dans le chargement et le déchargement des conducteurs, consultez [le rôle du gestionnaire de conducteur dans le processus de connexion](../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md).

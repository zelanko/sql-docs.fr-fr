---
title: Architecture des pilotes de base de données de bureau (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], architecture
- ODBC desktop database drivers [ODBC], architecture
- desktop database drivers [ODBC], architecture
ms.assetid: 8b4d13f7-ab37-40b4-a9c6-145e7385352f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae6fb72bb3ed0a9bca1571eb572bbfbd20fe9995
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288739"
---
# <a name="desktop-database-drivers-architecture"></a>Architecture des pilotes pour les bases de données de poste de travail
Ces pilotes sont conçus pour une utilisation sur Microsoft Windows 95 ou plus tard, ou Windows NT 4.0 et Windows 2000. Seules les applications 32 bits sont prises en charge sur Windows 95 ou plus tard; Les applications 16 bits et 32 bits sont prises en charge sur Windows NT 4.0 et Windows 2000.  
  
> [!NOTE]  
>  Pour plus d’informations sur la version de l’ODBC à utiliser avec ces pilotes, consultez la *Référence du programmeur ODBC*et les notes de sortie passées et actuelles. À l’exception des zones notées, ces conducteurs se conforment à la *référence du programmeur de l’ODBC*.  
  
 Les pilotes de base de données de bureau ODBC comprennent des pilotes 32 bits pour Microsoft Access, dBASE, Microsoft Excel, Paradox et Text. Aucun conducteur 16 bits n’est inclus. (Un pilote pour Microsoft FoxPro est disponible séparément.)  
  
 L’architecture de l’application/conducteur sur Windows 95 ou plus tard est :  
  
 ![App&#47;architecture du conducteur: Windows 95 et plus tard](../../odbc/microsoft/media/odbcjetarch1.gif "ODBCJetArch1")  
  
 L’utilisation de ces pilotes par des applications 16 bits sur Windows 95 n’est pas prise en charge.  
  
 L’architecture de l’application/pilote sur Windows NT 4.0 et Windows 2000 est :  
  
 ![App&#47;architecture du conducteur: NT 4.0 et Windows 2000](../../odbc/microsoft/media/odbcjetarch2.gif "ODBCJetArch2")  
  
 Les pilotes de base de données de bureau sont des pilotes à deux niveaux. Dans une configuration à deux niveaux, le conducteur n’effectue pas le processus d’analyse, de validation, d’optimisation et d’exécution de la requête. Au lieu de cela, Microsoft Jet effectue ces tâches. Il traite les appels ODBC API et agit comme un moteur SQL. Microsoft Jet est devenu une partie intégrante et indissociable des pilotes: Il est expédié avec les pilotes et réside avec les pilotes, même si aucune autre application sur l’ordinateur l’utilise.  
  
 Les pilotes de base de données de bureau se composent de six pilotes différents - ou, plus précisément, d’un fichier pilote (Odbcjt32.dll) que le [gestionnaire de pilote](../../odbc/reference/the-driver-manager.md) ODBC utilise de six façons différentes. Le drapeau DRIVERID dans la saisie du registre pour une source de données détermine quel conducteur à Odbcjt32.dll le gestionnaire de conducteur utilise. Une application passe ce drapeau dans la chaîne de connexion incluse dans un appel à **SQLDriverConnect**. Par défaut, le drapeau est l’ID du pilote Microsoft Access.  
  
 Le fichier d’installation du pilote modifie le drapeau DRIVERID au moment de l’installation. Tous les pilotes, sauf le pilote Microsoft Access, ont une configuration DLL associée. Lorsque vous cliquez sur **Setup** dans [l’administrateur Microsoft ODBC Data Source](../../odbc/admin/odbc-data-source-administrator.md) pour une source de données, l’installateur DLL ODBC (Odbcinst.dll) charge la configuration DLL. La configuration DLL exporte la fonction d’installateur ODBC **SQLConfigDataSource**. Si une poignée de fenêtre est passée à **SQLConfigDataSource**, cette fonction affiche une fenêtre d’installation et modifie le drapeau DRIVERID en fonction du pilote sélectionné à partir de l’interface utilisateur.  
  
 Lorsqu’un fichier est créé de manière programmatique, une poignée de fenêtre NULL est transmise à **SQLConfigDataSource**, et la fonction crée une source de données dynamiquement, changeant le drapeau DRIVERID selon *l’argument lpszDriver* dans l’appel de fonction.  
  
 Odbcjt32.dll implémente les fonctions ODBC au-dessus de l’API Microsoft Jet. Il n’y a pas de cartographie directe entre les fonctions ODBC et Microsoft Jet, cependant. De nombreux facteurs, tels que les modèles de curseur et la cartographie SQL, empêchent une corrélation directe des fonctions.  
  
 Le pilote ODBC réside entre le moteur Microsoft Jet et le gestionnaire de pilote ODBC. Certaines fonctions ODBC appelées par une application sont traitées par le gestionnaire de conducteur et ne sont pas transmises au conducteur. Pour ces fonctions, Microsoft Jet ne voit jamais l’appel de fonction car il n’a pas de connexion directe avec le Driver Manager.

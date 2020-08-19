---
description: Architecture des pilotes pour les bases de données de poste de travail
title: Architecture des pilotes de base de données Desktop | Microsoft Docs
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
ms.openlocfilehash: d330392424b683e24f17bd959d0a29e76eedbd36
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449571"
---
# <a name="desktop-database-drivers-architecture"></a>Architecture des pilotes pour les bases de données de poste de travail
Ces pilotes sont conçus pour être utilisés sur Microsoft Windows 95 ou version ultérieure, ou Windows NT 4,0 et Windows 2000. Seules les applications 32 bits sont prises en charge sur Windows 95 ou version ultérieure. les applications 16 bits et 32 bits sont prises en charge sur Windows NT 4,0 et Windows 2000.  
  
> [!NOTE]  
>  Pour plus d’informations sur la version de ODBC à utiliser avec ces pilotes, reportez-vous à la *documentation de référence du programmeur ODBC*, ainsi qu’aux notes de publication actuelles et passées. À l’exception des zones notées, ces pilotes sont conformes aux informations de *Référence du programmeur ODBC*.  
  
 Les pilotes de base de données de bureau ODBC incluent des pilotes 32 bits pour Microsoft Access, dBASE, Microsoft Excel, Paradox et Text. Aucun pilote 16 bits n’est inclus. (Un pilote pour Microsoft FoxPro est disponible séparément.)  
  
 L’architecture de l’application/du pilote sur Windows 95 ou version ultérieure est :  
  
 ![Architecture du pilote d'&#47;d’application : Windows 95 et versions ultérieures](../../odbc/microsoft/media/odbcjetarch1.gif "ODBCJetArch1")  
  
 L’utilisation de ces pilotes par des applications 16 bits sur Windows 95 n’est pas prise en charge.  
  
 L’architecture des applications/pilotes sur Windows NT 4,0 et Windows 2000 est :  
  
 ![Architecture du pilote App&#47; : NT 4,0 et Windows 2000](../../odbc/microsoft/media/odbcjetarch2.gif "ODBCJetArch2")  
  
 Les pilotes de base de données de bureau sont des pilotes à deux niveaux. Dans une configuration à deux niveaux, le pilote n’effectue pas le processus d’analyse, de validation, d’optimisation et d’exécution de la requête. Au lieu de cela, Microsoft Jet effectue ces tâches. Il traite les appels d’API ODBC et agit comme un moteur SQL. Microsoft Jet est devenu une partie intégrante des pilotes. il est fourni avec les pilotes et réside avec les pilotes, même si aucune autre application de l’ordinateur ne l’utilise.  
  
 Les pilotes de base de données de bureau sont constitués de six pilotes différents (ou, plus précisément, d’un fichier de pilote (Odbcjt32.dll) utilisé par le [Gestionnaire de pilotes](../../odbc/reference/the-driver-manager.md) ODBC de six façons différentes. L’indicateur DRIVERID dans l’entrée de Registre pour une source de données détermine le pilote utilisé par Odbcjt32.dll le gestionnaire de pilotes. Une application transmet cet indicateur dans la chaîne de connexion incluse dans un appel à **SQLDriverConnect**. Par défaut, l’indicateur est l’ID du pilote Microsoft Access.  
  
 Le fichier d’installation du pilote modifie l’indicateur DRIVERID au moment de l’installation. Tous les pilotes, à l’exception de Microsoft Access Driver, ont une DLL d’installation associée. Lorsque vous cliquez sur le **programme d’installation** dans l’administrateur de la [source de données Microsoft ODBC](../../odbc/admin/odbc-data-source-administrator.md) pour une source de données, la dll du programme d’installation ODBC (Odbcinst.dll) charge la dll d’installation. La DLL d’installation exporte la fonction de programme d’installation ODBC **SQLConfigDataSource**. Si un handle de fenêtre est passé à **SQLConfigDataSource**, cette fonction affiche une fenêtre d’installation et modifie l’indicateur DRIVERID en fonction du pilote sélectionné à partir de l’interface utilisateur.  
  
 Lorsqu’un fichier est créé par programme, un handle de fenêtre NULL est passé à **SQLConfigDataSource**, et la fonction crée une source de données de manière dynamique, en modifiant l’indicateur DRIVERID en fonction de l’argument *lpszDriver* dans l’appel de fonction.  
  
 Odbcjt32.dll implémente les fonctions ODBC en plus de l’API Microsoft Jet. Toutefois, il n’existe pas de mappage direct entre les fonctions ODBC et Microsoft Jet. De nombreux facteurs, tels que les modèles de curseur et le mappage SQL, empêchent une corrélation directe des fonctions.  
  
 Le pilote ODBC réside entre le moteur Microsoft Jet et le gestionnaire de pilotes ODBC. Certaines fonctions ODBC appelées par une application sont gérées par le gestionnaire de pilotes et ne sont pas transmises au pilote. Pour ces fonctions, Microsoft Jet ne voit jamais l’appel de fonction, car il ne dispose pas d’une connexion directe au gestionnaire de pilotes.

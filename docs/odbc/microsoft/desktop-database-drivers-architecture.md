---
title: Architecture des pilotes de base de données de bureau | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7487d073b95190418ee7f6900390a2d60ce42e13
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62629071"
---
# <a name="desktop-database-drivers-architecture"></a>Architecture des pilotes pour les bases de données de poste de travail
Ces pilotes sont conçus pour les utiliser sur Microsoft Windows 95 ou version ultérieure, ou Windows NT 4.0 et Windows 2000. Seules les applications 32 bits sont pris en charge sur Windows 95 ou version ultérieure ; les applications 16 bits et 32 bits sont prises en charge sur Windows NT 4.0 et Windows 2000.  
  
> [!NOTE]  
>  Pour plus d’informations sur la version d’ODBC à utiliser avec ces pilotes, reportez-vous à la *de référence du programmeur ODBC*et les notes de publication passées et présentes. À l’exception des domaines indiqués, ces pilotes sont conformes à la *de référence du programmeur ODBC*.  
  
 Les pilotes de base de données ODBC Desktop incluent les pilotes 32 bits pour Microsoft Access, dBASE, Microsoft Excel, Paradox et texte. N° 16 - bits des pilotes sont inclus. (Un pilote pour Microsoft FoxPro est disponible séparément.)  
  
 L’architecture application/pilote sur Windows 95 ou version ultérieure est :  
  
 ![Application&#47;architecture du pilote : Windows 95 et versions ultérieures](../../odbc/microsoft/media/odbcjetarch1.gif "ODBCJetArch1")  
  
 L’utilisation de ces pilotes par les applications 16 bits sur Windows 95 n’est pas pris en charge.  
  
 L’architecture application/pilote sur Windows NT 4.0 et Windows 2000 est :  
  
 ![Application&#47;architecture du pilote : NT 4.0 et Windows 2000](../../odbc/microsoft/media/odbcjetarch2.gif "ODBCJetArch2")  
  
 Les pilotes de base de données de bureau sont à deux niveaux. Dans une configuration à deux niveaux, le pilote n’effectue pas le processus de l’analyse, validation, optimisation et l’exécution de la requête. Au lieu de cela, Microsoft Jet effectue ces tâches. Il traite les appels d’API ODBC et agit comme un moteur SQL. Microsoft Jet fait désormais partie intégrante, Inséparable des pilotes : Il est livré avec les pilotes et réside avec les pilotes, même si aucune autre application sur l’ordinateur l’utilise.  
  
 Les pilotes de base de données de bureau se composent de six différents pilotes - ou, plus précisément, un fichier de pilote (Odbcjt32.dll) qui ODBC [Gestionnaire de pilotes](../../odbc/reference/the-driver-manager.md) utilise de six différentes façons. L’indicateur DRIVERID dans l’entrée de Registre pour une source de données détermine quel pilote dans Odbcjt32.dll le Gestionnaire de pilotes utilise. Une application passe cet indicateur dans la chaîne de connexion incluse dans un appel à **SQLDriverConnect**. Par défaut, l’indicateur est l’ID du pilote Microsoft Access.  
  
 Le fichier d’installation de pilote modifie l’indicateur DRIVERID au moment de l’installation. Tous les pilotes sauf le pilote Microsoft Access ont une DLL d’installation associé. Lorsque vous cliquez sur **le programme d’installation** dans le [administrateur de sources de données Microsoft ODBC](../../odbc/admin/odbc-data-source-administrator.md) pour une source de données, le programme d’installation ODBC DLL (Odbcinst.dll) charge le DLL d’installation. Le programme d’installation DLL exporte la fonction de programme d’installation ODBC **SQLConfigDataSource**. Si un handle de fenêtre est passé à **SQLConfigDataSource**, cette fonction affiche une fenêtre de configuration et modifie l’indicateur DRIVERID selon le pilote sélectionné à partir de l’interface utilisateur.  
  
 Lorsqu’un fichier est créé par programme, un handle de fenêtre NULL est passé à **SQLConfigDataSource**, et la fonction crée une source de données de manière dynamique, en modifiant l’indicateur DRIVERID conformément à la *lpszDriver*argument dans l’appel de fonction.  
  
 Odbcjt32.dll implémente les fonctions ODBC sur l’API de Jet de Microsoft. Il n’existe aucun mappage direct entre les fonctions ODBC et Microsoft Jet, toutefois. Nombreux facteurs, tels que les modèles de curseur et le mappage de SQL, empêchent une corrélation directe des fonctions.  
  
 Le pilote ODBC réside entre le moteur Microsoft Jet et le Gestionnaire de pilotes ODBC. Certaines fonctions ODBC appelées par une application sont gérées par le Gestionnaire de pilotes et pas passées au pilote. Pour ces fonctions, Microsoft Jet voit jamais la fonction appeler car il ne dispose pas d’une connexion directe au Gestionnaire de pilote.

---
title: Applications | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- off-the-shelf applications [ODBC]
- ODBC architecture [ODBC], applications
- shrink-wrapped applications [ODBC]
- application development [ODBC], types
- custom applications [ODBC]
- virtual applications [ODBC]
- generic applications [ODBC]
ms.assetid: 39d6461f-0d24-4b7d-a723-843ade15ad73
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f15b5e8eb6eb7c63ab771030f0c31e8c9ff92724
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68135677"
---
# <a name="applications"></a>APPLICATIONS
Un *application* est un programme qui appelle l’API ODBC pour accéder aux données. Bien que de nombreux types d’applications sont possibles, la plupart se répartissent en trois catégories, qui sont utilisés comme exemples dans ce guide.  
  
-   **Applications génériques** ceux-ci sont également appelées applications neufs ou des applications prêtes à l’emploi. Applications génériques sont conçues pour fonctionner avec un large éventail de SGBD différents. Exemples incluent une feuille de calcul ou un package de statistiques qui utilise ODBC pour importer des données pour une analyse plus approfondie et un traitement de texte qui utilise ODBC pour obtenir une liste de diffusion à partir d’une base de données.  
  
     Une sous-catégorie importante d’applications génériques est environnements de développement d’application, telles que PowerBuilder ou Microsoft® Visual Basic®. Bien que les applications construites avec ces environnements fonctionnera probablement uniquement avec un SGBD unique, l’environnement lui-même doit fonctionner avec plusieurs systèmes SGBD.  
  
     Ce que toutes les applications génériques ont en commun est qu’ils sont hautement interopérables entre le SGBD et ils doivent utiliser ODBC de manière relativement générique. Pour plus d’informations sur l’interopérabilité, consultez [en choisissant un niveau d’interopérabilité](../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md).  
  
-   **Applications verticales** verticales effectuer un seul type de tâche, telle que la saisie de commandes ou le suivi des données de fabrication ou des applications avec un schéma de base de données qui est contrôlé par le développeur de l’application. Pour un client particulier, l’application fonctionne avec un système SGBD unique. Par exemple, une petite entreprise utilisation de l’application avec dBase, même si une grande entreprise peut l’utiliser avec Oracle.  
  
     L’application utilise ODBC de manière à ce que l’application n’est pas liée à n’importe quel un SGBD, bien qu’il peut être lié à un nombre limité de SGBD qui fournissent des fonctionnalités similaires. Par conséquent, le développeur d’applications peut vendre l’application indépendamment à partir de SGBD. Applications verticales sont interopérables lorsqu’ils sont développés, mais ils sont parfois modifiées pour inclure du code noninteroperable une fois que le client a choisi un SGBD.  
  
-   **Applications personnalisées** applications personnalisées sont utilisées pour effectuer une tâche spécifique dans une même société. Par exemple, une application dans une grande entreprise peut collecter des données de ventes à partir de plusieurs divisions (chacun d'entre eux utilisant un SGBD différents) et créer un rapport unique. ODBC est utilisé, car elle est une interface commune et enregistre les programmeurs de devoir apprendre plusieurs interfaces. Ces applications sont généralement pas interopérables et sont écrits dans le SGBD et des pilotes spécifiques.  
  
 Un nombre de tâches est commun à toutes les applications, quel que soit la façon dont ils utilisent ODBC. Prises ensemble, elles définissent en grande partie du flux de toute application ODBC. Les tâches sont :  
  
-   Sélection d’une source de données et la connexion à celui-ci.  
  
-   Soumission d’une instruction SQL pour l’exécution.  
  
-   Récupération des résultats (le cas échéant).  
  
-   Erreurs de traitement.  
  
-   Valider ou restaurer la transaction englobant l’instruction SQL.  
  
-   Déconnexion de la source de données.  
  
 Étant donné que la plupart des données accès Professionnel est effectuée avec SQL, la tâche principale pour les applications utilisent ODBC consiste à envoyer des instructions SQL et de récupérer les résultats (le cas échéant) générées par ces instructions. Autres tâches pour les applications utilisent ODBC incluent détermination et d’adapter aux fonctionnalités du pilote et de consultation du catalogue de base de données.

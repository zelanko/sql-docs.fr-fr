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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135677"
---
# <a name="applications"></a>Applications
Une *application* est un programme qui appelle l’API ODBC pour accéder aux données. Bien que de nombreux types d’applications soient possibles, la plupart se répartissent en trois catégories, qui sont utilisées comme exemples dans ce guide.  
  
-   **Applications génériques** Celles-ci sont également appelées applications compactées ou prêtes à l’emploi. Les applications génériques sont conçues pour fonctionner avec différents SGBD. Exemples : une feuille de calcul ou un package de statistiques qui utilise ODBC pour importer des données pour une analyse plus poussée et un traitement de texte qui utilise ODBC pour obtenir une liste de diffusion à partir d’une base de données.  
  
     Une sous-catégorie importante d’applications génériques est l’environnement de développement d’applications, tel que PowerBuilder ou Microsoft® Visual Basic®. Bien que les applications construites avec ces environnements ne fonctionnent probablement qu’avec un seul SGBD, l’environnement lui-même doit fonctionner avec plusieurs SGBD.  
  
     Ce que toutes les applications génériques ont en commun, c’est qu’elles sont très interopérables entre les SGBD et qu’elles doivent utiliser ODBC de manière relativement générique. Pour plus d’informations sur l’interopérabilité, consultez [choix d’un niveau d’interopérabilité](../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md).  
  
-   **Applications verticales** Les applications verticales exécutent un type de tâche unique, telles que l’entrée de commande ou le suivi des données de fabrication, et utilisent un schéma de base de données contrôlé par le développeur de l’application. Pour un client particulier, l’application fonctionne avec un seul SGBD. Par exemple, une petite entreprise peut utiliser l’application avec dBase, tandis qu’une entreprise de grande taille peut l’utiliser avec Oracle.  
  
     L’application utilise ODBC de manière à ce que l’application ne soit pas liée à un SGBD, bien qu’elle puisse être liée à un nombre limité de SGBD qui offrent des fonctionnalités similaires. Ainsi, le développeur d’applications peut vendre l’application indépendamment du SGBD. Les applications verticales sont interopérables lorsqu’elles sont développées mais sont parfois modifiées pour inclure le code noninteroperable une fois que le client a choisi un SGBD.  
  
-   **Applications personnalisées** Les applications personnalisées sont utilisées pour effectuer une tâche spécifique dans une seule société. Par exemple, une application dans une grande entreprise peut collecter des données de ventes à partir de plusieurs divisions (chacune d’elles utilisant un SGBD différent) et créer un rapport unique. ODBC est utilisé, car il s’agit d’une interface commune qui évite aux programmeurs d’avoir à apprendre plusieurs interfaces. Ces applications ne sont généralement pas interopérables et sont écrites dans des SGBD et des pilotes spécifiques.  
  
 Un certain nombre de tâches sont communes à toutes les applications, quel que soit leur mode d’utilisation d’ODBC. Pris ensemble, ils définissent en grande partie le déroulement d’une application ODBC. Les tâches sont les suivantes :  
  
-   Sélection d’une source de données et connexion à celle-ci.  
  
-   Envoi d’une instruction SQL pour l’exécution.  
  
-   Récupération des résultats (le cas échéant).  
  
-   Erreurs de traitement.  
  
-   Validation ou restauration de la transaction englobant l’instruction SQL.  
  
-   Déconnexion de la source de données.  
  
 Étant donné que la plupart des opérations d’accès aux données sont effectuées avec SQL, la tâche principale pour laquelle les applications utilisent ODBC consiste à envoyer des instructions SQL et à récupérer les résultats (le cas échéant) générés par ces instructions. Parmi les autres tâches pour lesquelles les applications utilisent ODBC, citons la détermination et l’ajustement des fonctionnalités du pilote et la navigation dans le catalogue de la base de données.

---
title: Applications (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9184986883f64bd082ca1db472d887609d3071bd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306550"
---
# <a name="applications"></a>Applications
Une *application* est un programme qui appelle l’API ODBC pour accéder aux données. Bien que de nombreux types d’applications soient possibles, la plupart se divisent en trois catégories, qui sont utilisées comme exemples tout au long de ce guide.  
  
-   **Applications génériques** Il s’agit également d’applications emballées sous le nom de récontignement ou d’applications prêtes à l’emploi. Les applications génériques sont conçues pour fonctionner avec une variété de DBMS différents. Par exemple, une feuille de calcul ou un ensemble de statistiques qui utilise ODBC pour importer des données pour une analyse plus approfondie et un traitement de texte qui utilise ODBC pour obtenir une liste de diffusion à partir d’une base de données.  
  
     Une sous-catégorie importante d’applications génériques est les environnements de développement d’applications, tels que PowerBuilder ou Microsoft® Visual Basic®. Bien que les applications construites avec ces environnements ne fonctionneront probablement qu’avec un seul DBMS, l’environnement lui-même doit fonctionner avec plusieurs DBMS.  
  
     Ce que toutes les applications génériques ont en commun, c’est qu’elles sont hautement interopérables chez les SDM et qu’elles doivent utiliser ODBC d’une manière relativement générique. Pour plus d’informations sur l’interopérabilité, voir [Choisir un niveau d’interopérabilité](../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md).  
  
-   **Applications verticales** Les applications verticales effectuent un seul type de tâche, telles que la saisie de commande ou le suivi des données de fabrication, et fonctionnent avec un schéma de base de données qui est contrôlé par le développeur de l’application. Pour un client particulier, l’application fonctionne avec un seul DBMS. Par exemple, une petite entreprise peut utiliser l’application avec dBase, tandis qu’une grande entreprise peut l’utiliser avec Oracle.  
  
     L’application utilise ODBC de telle manière que l’application n’est liée à aucun DBMS, bien qu’elle puisse être liée à un nombre limité de DBMS qui fournissent des fonctionnalités similaires. Ainsi, le développeur d’applications peut vendre l’application indépendamment de la DBMS. Les applications verticales sont interopérables lorsqu’elles sont développées, mais sont parfois modifiées pour inclure du code non inutilisable une fois que le client a choisi un DBMS.  
  
-   **Applications personnalisées** Les applications personnalisées sont utilisées pour effectuer une tâche spécifique dans une seule entreprise. Par exemple, une application dans une grande entreprise peut recueillir des données de vente auprès de plusieurs divisions (chacune d’entre elles utilise un DBMS différent) et créer un seul rapport. ODBC est utilisé parce qu’il s’agit d’une interface commune et évite aux programmeurs d’avoir à apprendre plusieurs interfaces. Ces applications ne sont généralement pas interopérables et sont écrites à des DBMS et conducteurs spécifiques.  
  
 Un certain nombre de tâches sont communes à toutes les applications, peu importe comment elles utilisent ODBC. Pris ensemble, ils définissent en grande partie le flux de toute application ODBC. Les tâches sont les suivantes :  
  
-   Sélection d’une source de données et connexion à elle.  
  
-   Soumettre une déclaration SQL pour exécution.  
  
-   Récupération des résultats (le cas échéant).  
  
-   Erreurs de traitement.  
  
-   Engager ou faire reculer la transaction englobant la déclaration SQL.  
  
-   Déconnecter de la source de données.  
  
 Étant donné que la plupart des travaux d’accès aux données sont effectués avec SQL, la tâche principale pour laquelle les applications utilisent ODBC est de soumettre des relevés SQL et de récupérer les résultats (le cas échéant) générés par ces énoncés. D’autres tâches pour lesquelles les applications utilisent ODBC incluent la détermination et l’ajustement aux capacités du conducteur et la navigation dans le catalogue de base de données.

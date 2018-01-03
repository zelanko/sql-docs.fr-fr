---
title: Types de pilotes | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
ms.assetid: 864c53c1-b68a-48b6-b6bc-5ecb520bb9dc
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c2068bb92d1aaa00debc46277c117d4134091666
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="types-of-drivers"></a>Types de pilotes
Pilotes ODBC peuvent être classés comme suit :  
  
-   **32 bits ODBC 2.**  
     ***x* pilote** pilote de 32 bits qui :  
  
    -   Exporte uniquement ODBC 2*.x* fonctions.  
  
    -   Expose ODBC 2. *x* comportement pour les changements de comportement.  
  
-   **ISO et pilote compatible groupe ouvert** pilote de 32 bits qui :  
  
    -   Exporte toutes les fonctions qui sont documentées dans les documents Open Group ou ISO CLI. Cela inclut certaines fonctions sont déconseillées dans ODBC.  
  
    -   Présente un comportement ODBC 3.0 pour les changements de comportement.  
  
    -   Ne pas nécessairement traverse le Gestionnaire de pilotes 3.0 de ODBC.  
  
-   **ODBC 3.0 Driver** pilote de 32 bits qui :  
  
    -   Exporte uniquement des fonctions qui se trouvent dans ODBC 3.0 moins les fonctions déconseillées.  
  
    -   Est capable de présentant ODBC 2. *x* comportement ou un comportement ODBC 3.0 en ce qui concerne les changements de comportement, en fonction de l’attribut d’environnement SQL_ATTR_APP_ODBC_VERSION.  
  
-   **Pilote de ANSI ODBC 3.5 (ou version ultérieure)** pilote de 32 bits qui :  
  
    -   Exporte uniquement des fonctions qui se trouvent dans ODBC 3.5 moins les fonctions déconseillées.  
  
    -   Est capable de présentant ODBC 2. *x* comportement ou ODBC 3.0 comportement ou le comportement ODBC 3.5 en ce qui concerne les changements de comportement, basé sur l’attribut d’environnement SQL_ATTR_APP_ODBC_VERSION.  
  
-   **ODBC 3.5 (ou version ultérieure) Unicode Driver** pilote de 32 bits qui :  
  
    -   Prend en charge toutes les fonctionnalités d’un pilote ODBC 3.5 ANSI.  
  
    -   Exporte les versions Unicode de toutes les API de chaîne ODBC.  
  
    -   Stocker et traiter les données Unicode sur la source de données.  
  
> [!NOTE]  
>  pilotes ODBC 16 bits ne fonctionnera pas directement avec ODBC 3. *x* du Gestionnaire de pilotes. Toutefois, il est possible pour les pilotes 16 bits fonctionner avec le Gestionnaire de pilotes ODBC 2.0, qui par la suite des thunks jusqu'à la version 3. *x* du Gestionnaire de pilotes.

---
title: Types de pilotes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
ms.assetid: 864c53c1-b68a-48b6-b6bc-5ecb520bb9dc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 08c1c9b4338502f20e5f99885d371d713971aa38
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792701"
---
# <a name="types-of-drivers"></a>Types de pilotes
Pilotes ODBC peuvent être classés comme suit :  
  
-   **32 bits ODBC 2.**  
     **_x_ pilote** pilote de 32 bits qui :  
  
    -   Exporte uniquement ODBC *2.x* fonctions.  
  
    -   Expose ODBC *2.x* comportement pour les changements de comportement.  
  
-   **ISO et pilote compatible groupe Open** pilote de 32 bits qui :  
  
    -   Exporte toutes les fonctions qui sont documentées dans les documents Open Group ou ISO CLI. Cela inclut certaines des fonctions qui sont déconseillées dans ODBC.  
  
    -   Expose le comportement ODBC 3.0 pour les changements de comportement.  
  
    -   Ne pas nécessairement traverse le Gestionnaire de pilotes 3.0 de ODBC.  
  
-   **ODBC 3.0 pilote** pilote de 32 bits qui :  
  
    -   Exporte uniquement des fonctions qui se trouvent dans ODBC 3.0 moins déconseillé de fonctions.  
  
    -   Est capable de présentant ODBC *2.x* comportement ou comportement ODBC 3.0 en ce qui concerne les changements de comportement, en fonction de l’attribut d’environnement SQL_ATTR_APP_ODBC_VERSION.  
  
-   **Pilote de ANSI ODBC 3.5 (ou version ultérieure)** pilote de 32 bits qui :  
  
    -   Exporte uniquement des fonctions qui se trouvent dans ODBC 3.5 moins déconseillé de fonctions.  
  
    -   Est capable de présentant ODBC *2.x* comportement ou ODBC 3.0 comportement ou le comportement ODBC 3.5 en ce qui concerne les changements de comportement, basé sur l’attribut d’environnement SQL_ATTR_APP_ODBC_VERSION.  
  
-   **ODBC 3.5 (ou version ultérieure) Unicode Driver** pilote de 32 bits qui :  
  
    -   Prend en charge toutes les fonctionnalités d’un pilote ODBC 3.5 ANSI.  
  
    -   Exporte les versions Unicode de chaîne ODBC toutes les API.  
  
    -   Stocker et traiter les données Unicode sur la source de données.  
  
> [!NOTE]  
>  pilotes ODBC 16 bits ne fonctionnent pas directement avec ODBC *3.x* Gestionnaire de pilotes. Toutefois, il est possible pour les pilotes 16 bits fonctionner avec le Gestionnaire de pilotes ODBC 2.0, qui par la suite thunks jusqu'à la *3.x* Gestionnaire de pilotes.

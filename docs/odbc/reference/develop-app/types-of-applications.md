---
title: Types d’applications (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- upgrading applications [ODBC], application types
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
- application upgrades [ODBC], application types
- application compatibility issues [ODBC]
ms.assetid: d346a64e-a32c-4153-a40f-5b53c2f57ef2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f14326c9cec1eb89e431154c91b680e4688fcdfa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305530"
---
# <a name="types-of-applications"></a>Types d’applications
Les applications ODBC peuvent être classées comme suit :  
  
-   **Pure ODBC 2.**  
     ** _x_ Application** Une application 32 bits qui :  
  
    -   Appels seulement ODBC 2. *x* fonctions (y compris la fonction ODBC 1.0 **SQLSetParam**). Il s’agit notamment de l’ODBC 1. *x* applications qui ont été portées à 32 bits.  
  
    -   Attend ODBC 2. *x* comportement pour les fonctionnalités qui ont eu des changements de comportement. (Voir [changements comportementaux](../../../odbc/reference/develop-app/behavioral-changes.md) pour plus d’informations.)  
  
    -   N’a pas été recompilé avec ODBC 3.5 en-têtes.  
  
-   **Pure ODBC 2.**  
     **_x_ Application recompilée** A pure ODBC 2. *x* application qui a été recompilée à l’aide des fichiers d’en-tête ODBC 3.5, en définissant ODBCVER-0x0250.  
  
-   **Pure ODBC 2.**  
     **_x_ Application Unicode** A pure ODBC 2. *x* application recompilée conforme à Unicode et utilise le type de données SQL_WCHAR.  
  
-   **Pure Open Group et ISO**-**conforme ODBC Application** Une application 32 bits qui:  
  
    -   Fonctions d’appels définies dans les normes Open Group ou ISO CLI. (Ces fonctions peuvent inclure des fonctions dépréciées de 3,0.)  
  
    -   N’utilise pas les types de données Unicode.  
  
    -   S’attend à un comportement ODBC 3.0 pour les fonctionnalités qui ont eu des changements de comportement.  
  
-   **Application Pure ODBC 3.0** Une application 32 bits qui :  
  
    -   Est compilé avec 3.0 en-têtes.  
  
    -   Appelle n’importe quelle fonction ODBC 3.0, y compris éventuellement ceux qui sont dépréciés.  
  
    -   S’attend à un comportement ODBC 3.0 pour les fonctionnalités qui ont eu des changements de comportement.  
  
-   **Application Pure ODBC 3.5** Une application 32 ou 64 bits qui :  
  
    -   Utiliser peut-être des types de données Unicode.  
  
    -   Appelle n’importe quelle fonction ODBC 3.5, y compris éventuellement ceux qui sont dépréciés.  
  
    -   S’attend à ODBC 3.5 comportement pour les fonctionnalités qui ont eu des changements de comportement.  
  
-   **Application Pure ODBC 3.8 (ou plus tard)** Une application 32 ou 64 bits qui :  
  
    -   Utiliser peut-être des types de données Unicode.  
  
    -   Appelle n’importe quelle fonction ODBC 3.8, y compris éventuellement ceux qui sont dépréciés.  
  
    -   S’attend à ODBC 3.8 comportement pour les fonctionnalités qui ont eu des changements de comportement.  
  
-   **Application remplacée** Une application 32 ou 64 bits qui :  
  
    -   Implémente un nouveau comportement pour les fonctionnalités dupliquées.  
  
    -   Utilise toutes les nouvelles fonctionnalités dans une version ultérieure d’ODBC uniquement dans le code conditionnel.  
  
    -   A limité le code conditionnel pour gérer les changements de comportement ou s’est enregistré pour être une version antérieure de l’application ODBC.

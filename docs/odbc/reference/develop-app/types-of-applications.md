---
title: Types d’Applications | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6e46075e55aa14784e967b3620de5855a47c4bd6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47676617"
---
# <a name="types-of-applications"></a>Types d’applications
Les applications ODBC peuvent être classées comme suit :  
  
-   **Pure ODBC 2.**  
     ***x* Application** les applications 32 bits qui :  
  
    -   Appelle uniquement ODBC 2. *x* fonctions (y compris la fonction ODBC 1.0 **SQLSetParam**). Ceux-ci incluent 1 d’ODBC. *x* applications qui ont été portées sur 32 bits.  
  
    -   Attend ODBC 2. *x* comportement pour les fonctionnalités qui ont connu des changements de comportement. (Consultez [des changements de comportement](../../../odbc/reference/develop-app/behavioral-changes.md) pour plus d’informations.)  
  
    -   N’a pas été compilé avec les en-têtes ODBC 3.5.  
  
-   **Pure ODBC 2.**  
     ***x* Application recompilé** une pure ODBC 2. *x* application qui a été compilée en utilisant les fichiers d’en-tête ODBC 3.5, en définissant ODBCVER = 0x0250.  
  
-   **Pure ODBC 2.**  
     ***x* Application Unicode** une pure ODBC 2. *x* recompiler l’application qui est compatible avec Unicode et utilise le type de données SQL_WCHAR.  
  
-   **Pure Open Group et ISO**–**Application ODBC compatible** les applications 32 bits qui :  
  
    -   Appelle les fonctions définies dans les normes Open Group ou ISO CLI. (Ces fonctions peuvent inclure des 3.0 fonctions déconseillées.)  
  
    -   N’utilise pas les types de données Unicode.  
  
    -   Attend un comportement ODBC 3.0 pour les fonctionnalités qui ont connu des changements de comportement.  
  
-   **Application de pure ODBC 3.0** les applications 32 bits qui :  
  
    -   Est compilé avec 3.0 en-têtes.  
  
    -   Appelle une fonction ODBC 3.0, éventuellement y compris ceux qui sont déconseillés.  
  
    -   Attend un comportement ODBC 3.0 pour les fonctionnalités qui ont connu des changements de comportement.  
  
-   **Application de pure ODBC 3.5** de 32 ou 64 bits application qui :  
  
    -   Peut utiliser des types de données Unicode.  
  
    -   Appelle une fonction ODBC 3.5, éventuellement y compris ceux qui sont déconseillés.  
  
    -   Attend un comportement ODBC 3.5 pour les fonctionnalités qui ont connu des changements de comportement.  
  
-   **Application de 3,8 (ou version ultérieure) ODBC pure** application 32 bits ou 64 bits qui :  
  
    -   Peut utiliser des types de données Unicode.  
  
    -   Appelle une fonction ODBC 3.8, éventuellement y compris ceux qui sont déconseillés.  
  
    -   Attend un comportement d’ODBC 3.8 pour les fonctionnalités qui ont connu des changements de comportement.  
  
-   **Remplacé Application** de 32 ou 64 bits application qui :  
  
    -   Implémente nouveau comportement pour la fonctionnalité en double.  
  
    -   Utilise des nouvelles fonctionnalités dans une version ultérieure d’ODBC uniquement dans le code conditionnel.  
  
    -   Dispose d’un code conditionnel pour gérer les changements de comportement limité ou s’est inscrit pour être une version antérieure de l’application ODBC.

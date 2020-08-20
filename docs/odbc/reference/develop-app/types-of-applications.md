---
description: Types d’applications
title: Types d’applications | Microsoft Docs
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
ms.openlocfilehash: 54056a6111924fb584ac35a65d6f74e8dab1ba6c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465549"
---
# <a name="types-of-applications"></a>Types d’applications
Les applications ODBC peuvent être classées comme suit :  
  
-   **Pur ODBC 2.**  
     **application _x_ ** application 32 bits qui :  
  
    -   Appelle uniquement ODBC 2. *x* Functions (y compris la fonction ODBC 1,0 **SQLSetParam,**). Cela inclut ODBC 1. *x* applications qui ont été portées à 32 bits.  
  
    -   Nécessite ODBC 2. comportement *x* pour les fonctionnalités qui ont subi des modifications de comportement. (Pour plus d’informations, consultez [changements de comportement](../../../odbc/reference/develop-app/behavioral-changes.md) .)  
  
    -   N’a pas été recompilé avec les en-têtes ODBC 3,5.  
  
-   **Pur ODBC 2.**  
     **_x_ application recompilée** A pur ODBC 2. *x* qui a été recompilée à l’aide des fichiers d’en-tête ODBC 3,5, en définissant ODBCVER = 0x0250.  
  
-   **Pur ODBC 2.**  
     **_x_ application Unicode** pur ODBC 2. *x* application recompilée qui est conforme à la norme Unicode et qui utilise le type de données SQL_WCHAR.  
  
-   **Groupe ouvert pur et ISO** - **application ODBC conforme** Une application 32 bits qui :  
  
    -   Appelle les fonctions définies dans les normes Open Group ou ISO CLI. (Ces fonctions peuvent inclure des fonctions 3,0 dépréciées.)  
  
    -   N’utilise pas les types de données Unicode.  
  
    -   Requiert un comportement ODBC 3,0 pour les fonctionnalités qui ont subi des modifications de comportement.  
  
-   **Application ODBC 3,0 pure** Une application 32 bits qui :  
  
    -   Est compilé avec des en-têtes 3,0.  
  
    -   Appelle toute fonction ODBC 3,0, y compris éventuellement celles qui sont dépréciées.  
  
    -   Requiert un comportement ODBC 3,0 pour les fonctionnalités qui ont subi des modifications de comportement.  
  
-   **Application ODBC 3,5 pure** Une application 32 ou 64 bits qui :  
  
    -   Peut utiliser des types de données Unicode.  
  
    -   Appelle toute fonction ODBC 3,5, y compris éventuellement celles qui sont dépréciées.  
  
    -   Requiert un comportement ODBC 3,5 pour les fonctionnalités qui ont subi des modifications de comportement.  
  
-   **Application ODBC 3,8 (ou version ultérieure) pure** Une application 32 bits ou 64 bits qui :  
  
    -   Peut utiliser des types de données Unicode.  
  
    -   Appelle toute fonction ODBC 3,8, y compris éventuellement celles qui sont dépréciées.  
  
    -   Requiert un comportement ODBC 3,8 pour les fonctionnalités qui ont subi des modifications de comportement.  
  
-   **Application remplacée** Une application 32 ou 64 bits qui :  
  
    -   Implémente un nouveau comportement pour les fonctionnalités dupliquées.  
  
    -   Utilise toutes les nouvelles fonctionnalités d’une version ultérieure d’ODBC uniquement au sein du code conditionnel.  
  
    -   Dispose d’un code conditionnel limité pour gérer les changements de comportement ou s’est inscrit auprès d’une version antérieure de l’application ODBC.

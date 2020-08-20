---
description: Types de pilotes
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ae3ab2b0172e97a221b446107ccbf4b6ae4eb7b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476293"
---
# <a name="types-of-drivers"></a>Types de pilotes
Les pilotes ODBC peuvent être classés comme suit :  
  
-   **ODBC 2 32 bits.**  
     ** _x_ ** pilote A 32 bits :  
  
    -   Exporte uniquement les fonctions ODBC *2. x* .  
  
    -   Présente le comportement ODBC *2. x* pour les changements de comportement.  
  
-   **ISO et le pilote compatible avec les groupes ouverts** Un pilote 32 bits qui :  
  
    -   Exporte toutes les fonctions documentées dans les documents Open Group ou ISO CLI. Cela inclut certaines des fonctions déconseillées dans ODBC.  
  
    -   Présente le comportement ODBC 3,0 pour les changements de comportement.  
  
    -   Ne passe pas nécessairement par le gestionnaire de pilotes ODBC 3,0.  
  
-   **Pilote ODBC 3,0** Un pilote 32 bits qui :  
  
    -   Exporte uniquement les fonctions qui sont dans les fonctions ODBC 3,0 moins dépréciées.  
  
    -   Peut exposer le comportement ODBC *2. x* ou ODBC 3,0 en ce qui concerne les changements de comportement, en fonction de l’attribut d’environnement SQL_ATTR_APP_ODBC_VERSION.  
  
-   **Pilote ANSI 3,5 (ou version ultérieure) ODBC** Un pilote 32 bits qui :  
  
    -   Exporte uniquement les fonctions qui sont dans les fonctions ODBC 3,5 moins dépréciées.  
  
    -   Peut exposer le comportement ODBC *2. x* ou ODBC 3,0, ou le comportement ODBC 3,5 en ce qui concerne les changements de comportement, en fonction de l’attribut d’environnement SQL_ATTR_APP_ODBC_VERSION.  
  
-   **Pilote Unicode ODBC 3,5 (ou version ultérieure)** Un pilote 32 bits qui :  
  
    -   Prend en charge toutes les fonctionnalités d’un pilote ODBC 3,5 ANSI.  
  
    -   Exporte les versions Unicode de toutes les API de chaîne ODBC.  
  
    -   Peut stocker et traiter des données Unicode sur la source de données.  
  
> [!NOTE]  
>  les pilotes ODBC 16 bits ne fonctionneront pas directement avec le gestionnaire de pilotes ODBC *3. x* . Toutefois, les pilotes 16 bits peuvent fonctionner avec le gestionnaire de pilotes ODBC 2,0 qui, par la suite, sont contextuels jusqu’au gestionnaire de pilotes *3. x* .

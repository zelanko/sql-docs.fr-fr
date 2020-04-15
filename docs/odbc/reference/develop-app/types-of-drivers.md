---
title: Types de pilotes Microsoft Docs
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
ms.openlocfilehash: de6d8e1473f127d28c69969e0fc298afd69d3023
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304870"
---
# <a name="types-of-drivers"></a>Types de pilotes
Les conducteurs D’ODBC peuvent être classés comme suit :  
  
-   **ODBC 2.**  
     ** _x_ Pilote** Un conducteur 32 bits qui :  
  
    -   Exportations uniquement ODBC *2.x* fonctions.  
  
    -   Expositions ODBC *2.x* comportement pour les changements de comportement.  
  
-   **PILOTE ISO et Open Group-Compliant** Un conducteur 32 bits qui :  
  
    -   Exporte toutes les fonctions qui sont documentées dans les documents Open Group ou ISO CLI. Cela inclura certaines des fonctions qui sont dépréciées dans ODBC.  
  
    -   Expositions ODBC 3.0 comportement pour les changements de comportement.  
  
    -   Ne passe pas nécessairement par le gestionnaire de conduite ODBC 3.0.  
  
-   **ODBC 3.0 Pilote** Un conducteur 32 bits qui :  
  
    -   Exportations ne fonctionne que dans ODBC 3.0 moins fonctions dépréciées.  
  
    -   Est capable d’afficher un comportement ODBC *2.x* ou un comportement ODBC 3.0 en ce qui concerne les changements de comportement, en fonction de l’attribut SQL_ATTR_APP_ODBC_VERSION environnement.  
  
-   **ODBC 3.5 (ou plus tard) PILOTE ANSI** Un conducteur 32 bits qui :  
  
    -   Exportations ne fonctions que dans ODBC 3.5 moins fonctions dépréciées.  
  
    -   Est capable d’afficher un comportement ODBC *2.x* ou un comportement ODBC 3.0, ou un comportement ODBC 3.5 en ce qui concerne les changements de comportement, en fonction de l’attribut SQL_ATTR_APP_ODBC_VERSION environnement.  
  
-   **ODBC 3.5 (ou plus tard) Unicode Driver** Un conducteur 32 bits qui :  
  
    -   Prend en charge toutes les caractéristiques d’un pilote ODBC 3.5 ANSI.  
  
    -   Exportations Des versions Unicode de toutes les API à cordes ODBC.  
  
    -   Peut stocker et traiter les données Unicode sur la source de données.  
  
> [!NOTE]  
>  Les conducteurs 16 bits de l’ODBC ne travailleront pas directement avec le gestionnaire de conducteur ODBC *3.x.* Cependant, il est possible pour les conducteurs 16 bits de travailler avec le gestionnaire de conducteur 2.0 ODBC, qui a ensuite thunks jusqu’à la *3.x* Driver Manager.

---
description: 'Annexe G : Conseils sur les pilotes pour la compatibilité descendante'
title: 'Annexe G : instructions relatives aux pilotes pour la compatibilité descendante | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 911cd335-f2c0-4d03-9739-1078308a678a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e2c09485879c2f0d16518dcfc0a17f4bf3a13943
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411405"
---
# <a name="appendix-g-driver-guidelines-for-backward-compatibility"></a>Annexe G : Conseils sur les pilotes pour la compatibilité descendante
Cette annexe fournit des informations pour les créateurs de pilotes qui fonctionnent sur ODBC 3. *x* pilotes qui doivent prendre en charge ODBC 2. *x* applications. Pour plus d’informations sur la compatibilité descendante, consultez [compatibilité descendante et conformité aux normes](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Curseurs de bloc, curseurs avec défilement et compatibilité descendante pour les pilotes ODBC 3. x](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) : les nouvelles fonctionnalités sont des fonctionnalités qui existent dans ODBC 3. *x* et non dans ODBC 2. *x*. ODBC 3. les pilotes *x* n’ont généralement pas à se soucier de la compatibilité descendante avec les nouvelles fonctionnalités, car ODBC 2. *x* les applications ne les utilisent jamais. Les seules exceptions sont les fonctionnalités apparentées à **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**et **SQLExtendedFetch**. Pour plus d’informations, consultez, plus loin dans cette annexe.  
  
-   [Fonctions de mappage dépréciées](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) -les fonctionnalités dupliquées sont des fonctionnalités implémentées différemment dans ODBC 3. *x* et ODBC 2. *x*. ODBC 3. *x* les pilotes n’ont pas à se soucier de la compatibilité descendante avec les fonctionnalités dupliquées, car le gestionnaire de pilotes mappe toujours ODBC 2. *x* sur ODBC 3. *x* lors de l’appel d’ODBC 3. pilote *x* . Par conséquent, ODBC 3. le pilote *x* ne voit que ODBC 3. *x* . Pour plus d’informations sur ces mappages, voir, plus loin dans cette annexe.  
  
-   [Changements de comportement et pilotes ODBC 3. x](../../../odbc/reference/appendixes/behavioral-changes-and-odbc-3-x-drivers.md) -les changements de comportement sont des fonctionnalités qui sont gérées différemment dans ODBC 3. *x* et ODBC 2. *x*. ODBC 3. *x* les pilotes doivent se soucier des changements de comportement et agir en réponse à l’attribut d’environnement SQL_ATTR_ODBC_VERSION défini par l’application.

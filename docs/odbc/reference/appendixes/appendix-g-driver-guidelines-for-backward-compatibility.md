---
title: 'Annexe G : Lignes directrices sur les conducteurs pour la compatibilité rétrograde (fr) Microsoft Docs'
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
ms.openlocfilehash: 1055f94cb54bba9262f210e5df5f028029aebf5b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292399"
---
# <a name="appendix-g-driver-guidelines-for-backward-compatibility"></a>Annexe G : Conseils sur les pilotes pour la compatibilité descendante
Cette annexe fournit des informations pour les auteurs de pilotes travaillant sur ODBC 3. *x* conducteurs qui ont besoin de prendre en charge ODBC 2. *x* applications. Pour plus d’informations sur la compatibilité rétrograde, voir [Compatibilité rétrograde et conformité aux normes](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Block Cursors, Cursesors Scrollable et Compatibilité vers l’arrière pour les pilotes ODBC 3.x](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md) - Les nouvelles fonctionnalités sont des fonctionnalités qui existent dans ODBC 3. *x* et non dans ODBC 2. *x*. ODBC 3. *x* les conducteurs n’ont généralement pas à s’inquiéter de la compatibilité vers l’arrière avec les nouvelles fonctionnalités parce que ODBC 2. *x* applications ne les utilisent jamais. Les seules exceptions à cela sont les caractéristiques liées à **SQLFetch**, **SQLFetchScroll**, **SQLSetPos**, et **SQLExtendedFetch;** pour plus d’informations, voir, plus tard dans cette annexe.  
  
-   [Cartographie des fonctions dépréciées](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) - Les fonctionnalités dupliquées sont des fonctionnalités qui sont mises en œuvre différemment dans ODBC 3. *x* et ODBC 2. *x*. ODBC 3. *x* les conducteurs n’ont pas à se soucier de la compatibilité rétrograde avec les fonctionnalités dupliquées parce que le Driver Manager cartographie toujours ODBC 2. *x* caractéristiques de ODBC 3. *x* caractéristiques lors de l’appel d’un ODBC 3. *x* conducteur. Ainsi, un ODBC 3. *x* le conducteur ne voit que ODBC 3. *x* caractéristiques. Pour plus d’informations sur ces cartes, voir, plus tard dans cette annexe.  
  
-   [Changements comportementaux et ODBC 3.x Pilotes](../../../odbc/reference/appendixes/behavioral-changes-and-odbc-3-x-drivers.md) - Les changements de comportement sont des fonctionnalités qui sont traitées différemment dans ODBC 3. *x* et ODBC 2. *x*. ODBC 3. *x* les conducteurs doivent s’inquiéter des changements de comportement et agir en réponse à l’attribut SQL_ATTR_ODBC_VERSION environnement défini par l’application.

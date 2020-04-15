---
title: Changements comportementaux (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], behavioral changes
- behavioral changes [ODBC]
- compatibility [ODBC], behavioral changes
ms.assetid: a17ae701-6ab6-4eaf-9e46-d3b9cd0a3a67
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3e4a433531d90eb0f89d9a5e446464b13fd02526
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283439"
---
# <a name="behavioral-changes"></a>Changements de comportement
Les changements de comportement sont ceux pour lesquels la *syntaxe* de l’interface reste la même, mais la *sémantique* a changé. Pour ces modifications, fonctionnalités utilisées dans ODBC 2. *x* se comporte différemment de la même fonctionnalité dans ODBC 3. *x*.  
  
 La question de savoir si une demande présente ODBC 2. *x* comportement ou ODBC 3. *x* le comportement est déterminé par l’attribut SQL_ATTR_ODBC_VERSION environnement. Cette valeur 32 bits est prête à SQL_OV_ODBC2 pour exposer ODBC 2. *x* comportement, et SQL_OV_ODBC3 d’exposer ODBC 3. *x* comportement.  
  
 L’attribut SQL_ATTR_ODBC_VERSION environnement est fixé par un appel à **SQLSetEnvAttr**. Après qu’une application appelle **SQLAllocHandle** pour allouer une poignée d’environnement, il doit appeler**SQLSetEnvAttr** immédiatement pour définir le comportement qu’il présente. (En conséquence, il existe un nouvel état de l’environnement pour décrire la poignée de l’environnement dans un état alloué, mais sans version.) Pour plus d’informations, voir [Annexe B: ODBC State Transition Tables](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Une application indique le comportement qu’elle présente avec l’attribut SQL_ATTR_ODBC_VERSION environnement, mais l’attribut n’a aucun effet sur la connexion de l’application avec un ODBC 2. *x* ou ODBC 3. *x* conducteur. Un ODBC 3. *x* application peut se connecter à un ODBC 2. *x* ou 3. *x* conducteur, quel que soit le réglage de l’environnement attribut.  
  
 ODBC 3. *x* applications ne doit jamais appeler **SQLAllocEnv**. Par conséquent, si le gestionnaire de conducteur reçoit un appel à **SQLAllocEnv**, il reconnaît l’application comme un ODBC 2. *x* application.  
  
 L’attribut SQL_ATTR_ODBC_VERSION affecte trois aspects différents d’un ODBC 3. *x* comportement du conducteur :  
  
-   Codes SQLSTATE  
  
-   Types de données pour la date, l’heure et l’heure  
  
-   *L’argument catalogué* dans **SQLTables** accepte les modèles de recherche dans ODBC 3. *x*, mais pas dans ODBC 2. *x*  
  
 Le réglage de l’attribut SQL_ATTR_ODBC_VERSION environnement n’affecte pas **SQLSetParam** ou **SQLBindParam**. **SQLColAttribute n’est** pas non plus affecté par ce bit. Bien que **SQLColAttribute** retourne les attributs qui sont affectés par la version de l’ODBC (type de date, précision, échelle et longueur), le comportement prévu est déterminé par la valeur de *l’argument FieldIdentifier.* Lorsque *FieldIdentifier* est égal à SQL_DESC_TYPE, **SQLColAttribute** retourne l’ODBC 3. *x* codes pour la date, l’heure et l’heure; lorsque *FieldIdentifier* est égal à SQL_COLUMN_TYPE, **SQLColAttribute** retourne l’ODBC 2. *x* codes pour la date, l’heure et l’heure.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Mappages SQLSTATE](../../../odbc/reference/develop-app/sqlstate-mappings.md)  
  
-   [Changements dans le type de données datetime](../../../odbc/reference/develop-app/datetime-data-type-changes.md)

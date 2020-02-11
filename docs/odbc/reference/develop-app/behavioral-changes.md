---
title: Changements de comportement | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fc9f8dcc3782204c8bf1c9add1200e451edcf127
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68103874"
---
# <a name="behavioral-changes"></a>Changements de comportement
Les changements de comportement sont les modifications pour lesquelles la *syntaxe* de l’interface reste la même, mais la *sémantique* a changé. Pour ces modifications, fonctionnalités utilisées dans ODBC 2. *x* se comporte différemment de la même fonctionnalité dans ODBC 3. *x*.  
  
 Si une application présente ODBC 2. comportement *x* ou ODBC 3. le comportement *x* est déterminé par l’attribut d’environnement SQL_ATTR_ODBC_VERSION. Cette valeur 32 bits est définie sur SQL_OV_ODBC2 pour exposer ODBC 2. le comportement *x* et SQL_OV_ODBC3 d’exposer ODBC 3. comportement *x* .  
  
 L’attribut d’environnement SQL_ATTR_ODBC_VERSION est défini par un appel à **SQLSetEnvAttr**. Une fois qu’une application a appelé **SQLAllocHandle** pour allouer un handle d’environnement, elle doit appeler**SQLSetEnvAttr** immédiatement pour définir le comportement qu’elle présente. (Par conséquent, il existe un nouvel état d’environnement pour décrire le descripteur d’environnement dans un État alloué, mais sans version.) Pour plus d’informations, consultez [annexe B : tables de transition d’État ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Une application indique le comportement qu’elle présente avec l’attribut d’environnement SQL_ATTR_ODBC_VERSION, mais l’attribut n’a aucun effet sur la connexion de l’application avec ODBC 2. *x* ou ODBC 3. pilote *x* . ODBC 3. *x* l’application peut se connecter à ODBC 2. *x* ou 3. *x* , quel que soit le paramètre de l’attribut d’environnement.  
  
 ODBC 3. *x* les applications ne doivent jamais appeler **SQLAllocEnv**. Par conséquent, si le gestionnaire de pilotes reçoit un appel à **SQLAllocEnv**, il reconnaît l’application comme ODBC 2. application *x* .  
  
 L’attribut SQL_ATTR_ODBC_VERSION affecte trois aspects différents d’un ODBC 3. comportement du pilote *x* :  
  
-   Codes SQLSTATE  
  
-   Types de données pour date, Time et timestamp  
  
-   L’argument *nomcatalogue* dans **SQLTables** accepte les modèles de recherche dans ODBC 3. *x*, mais pas dans ODBC 2. *x*  
  
 Le paramètre de l’attribut d’environnement SQL_ATTR_ODBC_VERSION n’affecte pas **SQLSetParam,** ou **SQLBindParam**. **SQLColAttribute** n’est pas non plus affecté par ce bit. Bien que **SQLColAttribute** retourne des attributs qui sont affectés par la version d’ODBC (type date, précision, échelle et longueur), le comportement prévu est déterminé par la valeur de l’argument *FieldIdentifier* . Lorsque *FieldIdentifier* est égal à SQL_DESC_TYPE, **SQLColAttribute** retourne ODBC 3. codes *x* pour date, Time et timestamp ; Lorsque *FieldIdentifier* est égal à SQL_COLUMN_TYPE, **SQLColAttribute** retourne ODBC 2. codes *x* pour date, Time et timestamp.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Mappages SQLSTATE](../../../odbc/reference/develop-app/sqlstate-mappings.md)  
  
-   [Changements dans le type de données datetime](../../../odbc/reference/develop-app/datetime-data-type-changes.md)

---
title: Déclarations DDL (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], DDL statements
- DDL statements [ODBC]
ms.assetid: 96ac9859-5976-4b06-ae1f-2fec3231e266
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cae06efe6dd11e651e8553fa5c1004c2fa145478
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302990"
---
# <a name="ddl-statements"></a>Instructions DDL
Les énoncés de langage de définition des données (DDL) varient énormément entre les DBMS. ODBC SQL définit les énoncés pour les opérations de définition de données les plus courantes : création et baisse des tableaux, des index et des points de vue; modifier les tables; et l’octroi et la révocation des privilèges. Toutes les autres déclarations DDL sont spécifiques à la source de données. Par conséquent, les applications interopérables ne peuvent pas effectuer certaines opérations de définition de données. En général, ce n’est pas un problème, parce que ces opérations ont tendance à être très DBMS spécifiques et sont mieux laissés au logiciel d’administration de base de données propriétaire expédié avec la plupart des DBMS ou le programme d’installation expédié avec le pilote.  
  
 Un autre problème dans la définition des données est que les noms de type de données varient énormément entre les DBMS. Plutôt que de définir les noms de type de données standard et de forcer les conducteurs à les convertir en noms spécifiques à DBMS, **SQLGetTypeInfo** fournit un moyen pour les applications de découvrir des noms de type de données spécifiques À DBMS. Les applications interopérables devraient utiliser ces noms dans les relevés SQL pour créer et modifier des tableaux; les noms énumérés à [l’Annexe C: SQL Grammar](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), et [Annexe D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md), sont des exemples seulement.

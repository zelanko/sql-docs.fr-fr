---
title: Instructions DDL | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9100405c91387faa66b714a94b8259167ae31899
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63267661"
---
# <a name="ddl-statements"></a>Instructions DDL
Instructions de langage de définition (DDL) de données peut varier énormément SGBD. SQL ODBC définit des instructions pour les opérations de définition de données courantes : créer et supprimer des tables, les index et les vues ; modification des tables ; et l’octroi et la révocation des privilèges. Toutes les autres instructions DDL sont spécifiques à la source de données. Par conséquent, les applications interopérables ne peut pas effectuer certaines opérations de définition de données. En général, cela n’est pas un problème, car ces opérations ont tendance à être hautement SGBD spécifiques et sont meilleures gauche pour le logiciel d’administration de base de données propriétaire fourni avec la plupart des SGBD ou le programme d’installation fourni avec le pilote.  
  
 Un autre problème dans la définition de données est de ce type de données noms varient énormément de SGBD. Au lieu de définir des noms de type de données standard et forcer les pilotes pour les convertir en noms de SGBD spécifiques, **SQLGetTypeInfo** fournit un moyen aux applications de découvrir les noms de types de données propres au SGBD. Applications interopérables doivent utiliser ces noms dans les instructions SQL pour créer et modifier des tables ; les noms répertoriés dans [annexe c : Grammaire SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), et [annexe d : Types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md), sont des exemples.

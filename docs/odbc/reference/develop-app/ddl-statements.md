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
ms.openlocfilehash: 14d9eb18a5c6c3cbd62cea0c668f3c53f8da48f3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626677"
---
# <a name="ddl-statements"></a>Instructions DDL
Instructions de langage de définition (DDL) de données peut varier énormément SGBD. SQL ODBC définit des instructions pour les opérations de définition de données courantes : créer et supprimer des tables, les index et les vues ; modification des tables ; et l’octroi et la révocation des privilèges. Toutes les autres instructions DDL sont spécifique à la source de données. Par conséquent, les applications interopérables ne peut pas effectuer certaines opérations de définition de données. En général, cela n’est pas un problème, car ces opérations ont tendance à être hautement SGBD spécifiques et sont meilleures gauche pour le logiciel d’administration de base de données propriétaire fourni avec la plupart des SGBD ou le programme d’installation fourni avec le pilote.  
  
 Un autre problème dans la définition de données est de ce type de données noms varient énormément de SGBD. Au lieu de définir des noms de type de données standard et forcer les pilotes pour les convertir en noms de SGBD spécifiques, **SQLGetTypeInfo** fournit un moyen aux applications de découvrir les noms de types de données propres au SGBD. Applications interopérables doivent utiliser ces noms dans les instructions SQL pour créer et modifier des tables ; les noms répertoriés dans [annexe c : SQL grammaire](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), et [annexe d : Types de données](../../../odbc/reference/appendixes/appendix-d-data-types.md), sont des exemples.

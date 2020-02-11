---
title: Identificateurs de type SQL | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- SQL data types [ODBC], identifiers
- type identifiers [ODBC], SQL
- identifiers [ODBC], SQL type
- SQL type identifiers [ODBC]
ms.assetid: 22f6793b-2f43-4281-b35a-28f48e504dd8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: be36bd8efc059c1a4f9b5ddf2cdd7faf32cf7dd4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107448"
---
# <a name="sql-type-identifiers"></a>Identificateurs de types SQL
Chaque source de données définit ses propres types de données SQL. ODBC définit des identificateurs de type et décrit les caractéristiques générales des types de données SQL qui peuvent être mappés à chaque identificateur de type. Il s’agit de la façon dont chaque type de données dans la source de données sous-jacente est mappé à un identificateur de type SQL ODBC.  
  
 Par exemple, SQL_CHAR est l’identificateur de type pour une colonne de caractères avec une longueur fixe, en général entre 1 et 254 caractères. Ces caractéristiques correspondent au type de données CHAR trouvé dans de nombreuses sources de données SQL. Ainsi, lorsqu’une application découvre que l’identificateur de type d’une colonne est SQL_CHAR, elle peut supposer qu’il s’agit probablement d’une colonne de type CHAR. Toutefois, il doit toujours vérifier la longueur d’octet de la colonne avant de supposer qu’elle est comprise entre 1 et 254 caractères. le pilote pour une source de données non-SQL, par exemple, peut mapper une colonne de caractères de longueur fixe de 500 caractères à SQL_CHAR ou SQL_LONGVARCHAR, car aucune n’est une correspondance exacte.  
  
 ODBC définit un large éventail d’identificateurs de type SQL. Toutefois, le pilote n’est pas obligé d’utiliser tous ces identificateurs. Au lieu de cela, il utilise uniquement les identificateurs dont il a besoin pour exposer les types de données SQL pris en charge par la source de données sous-jacente. Si la source de données sous-jacente prend en charge les types de données SQL auxquels aucun identificateur de type ne correspond, le pilote peut définir des identificateurs de type supplémentaires. Pour plus d’informations, consultez [types de données spécifiques au pilote, types de descripteurs, types d’informations, types de diagnostics et attributs](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Pour obtenir une description complète des identificateurs de type SQL, consultez [types de données C](../../../odbc/reference/appendixes/c-data-types.md) dans l’annexe D : types de données.

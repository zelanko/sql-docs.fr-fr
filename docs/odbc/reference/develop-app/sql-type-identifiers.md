---
title: Identifications de type SQL Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 95bf46844e9ed91aac1ec6cb93a298995f0901d6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299769"
---
# <a name="sql-type-identifiers"></a>Identificateurs de types SQL
Chaque source de données définit ses propres types de données SQL. ODBC définit les identificateurs de type et décrit les caractéristiques générales des types de données SQL qui pourraient être cartographiés à chaque type d’identificateur. Il est spécifique au conducteur comment chaque type de données dans la source de données sous-jacente est cartographié à un identifiant de type SQL de L’ODBC.  
  
 Par exemple, SQL_CHAR est l’identifiant de type pour une colonne de caractère avec une longueur fixe, généralement entre 1 et 254 caractères. Ces caractéristiques correspondent au type de données CHAR trouvé dans de nombreuses sources de données SQL. Ainsi, lorsqu’une application découvre que l’identifiant de type pour une colonne est SQL_CHAR, il peut supposer qu’il s’agit probablement d’une colonne CHAR. Cependant, il devrait toujours vérifier la longueur d’entrée de la colonne avant de supposer qu’il est entre 1 et 254 caractères; le conducteur d’une source de données non SQL, par exemple, peut cartographier une colonne de caractères de longueur fixe de 500 caractères pour SQL_CHAR ou SQL_LONGVARCHAR, car ni l’un ni l’autre n’est une correspondance exacte.  
  
 ODBC définit une grande variété d’identifiants de type SQL. Toutefois, le conducteur n’est pas tenu d’utiliser tous ces identificateurs. Au lieu de cela, il utilise uniquement les identificateurs dont il a besoin pour exposer les types de données SQL pris en charge par la source de données sous-jacente. Si la source de données sous-jacente prend en charge les types de données SQL auxquels aucun identifiant de type ne correspond, le conducteur peut définir d’autres identificateurs de type. Pour plus d’informations, consultez [les types de données spécifiques au conducteur, les types descripteurs, les types d’information, les types de diagnostic et les attributs](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Pour une description complète des identificateurs de type SQL, voir [les types de données C](../../../odbc/reference/appendixes/c-data-types.md) à l’annexe D : Types de données.

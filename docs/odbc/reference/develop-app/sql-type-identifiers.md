---
title: Les identificateurs de Type SQL | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 1763ee0cd8c5bc2017160de44b9c047781649eba
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740147"
---
# <a name="sql-type-identifiers"></a>Identificateurs de types SQL
Chaque source de données définit ses propres types de données SQL. ODBC définit des identificateurs de type et décrit les caractéristiques générales des types de données SQL qui peuvent être mappés à chaque identificateur de type. Il est spécifique au pilote comment chaque type de données dans la source de données sous-jacente est mappé à un identificateur de type SQL d’ODBC.  
  
 Par exemple, SQL_CHAR est l’identificateur de type pour une colonne de type caractère avec une longueur fixe, généralement entre 1 et 254 caractères. Ces caractéristiques correspondent au type de données CHAR trouvé dans nombreuses sources de données SQL. Par conséquent, lorsqu’une application découvre que l’identificateur de type pour une colonne est SQL_CHAR, peut supposer qu’il a affaire probablement avec une colonne de type CHAR. Toutefois, il doit toujours s’enregistrer la longueur d’octet de la colonne avant d’en supposant qu’elle est comprise entre 1 et 254 caractères ; le pilote pour une source de données non SQL, par exemple, peut mapper une colonne de caractères de longueur fixe de 500 caractères SQL_CHAR ou SQL_LONGVARCHAR, car aucun n’est une correspondance exacte.  
  
 ODBC définit un large éventail d’identificateurs de type SQL. Toutefois, le pilote n’est pas requis d’utiliser la totalité de ces identificateurs. Au lieu de cela, elle utilise uniquement ces identificateurs qu'il doit exposer les types de données SQL pris en charge par la source de données sous-jacente. Si la source de données sous-jacente prend en charge les types de données SQL qui aucun identificateur de type ne correspond, le pilote peut définir des identificateurs de type supplémentaire. Pour plus d’informations, consultez [les Types de données spécifiques au pilote, Types de descripteurs, Types d’informations, Types de diagnostics et attributs](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md).  
  
 Pour obtenir une description complète des identificateurs de type SQL, consultez [les Types de données C](../../../odbc/reference/appendixes/c-data-types.md) annexe d : Types de données.

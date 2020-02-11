---
title: Identificateurs entre guillemets | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], quoted identifiers
- quoted identifiers [ODBC]
ms.assetid: 729ba55f-743b-4a04-8c39-ac0a9914211d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3bc4d8378c243edf9f01cca58ff8be11d675711a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079002"
---
# <a name="quoted-identifiers"></a>Identificateurs entre guillemets
Dans une instruction SQL, les identificateurs contenant des caractères spéciaux ou des mots clés de correspondance doivent être placés entre *guillemets*. les identificateurs entre ces caractères sont appelés *identificateurs entre guillemets* (également appelés *identificateurs délimités* dans SQL-92). Par exemple, l’identificateur Accounts payable est placé entre guillemets dans l’instruction **Select** suivante :  
  
```  
SELECT * FROM "Accounts Payable"  
```  
  
 La raison pour laquelle les identificateurs sont des identificateurs consiste à rendre l’instruction analysable. Par exemple, si Accounts payable n’a pas été placé entre guillemets dans l’instruction précédente, l’analyseur suppose qu’il existait deux tables, Accounts et payable, et retourne une erreur de syntaxe qui n’était pas séparée par une virgule. Le caractère d’identificateur guillemet est spécifique au pilote et est récupéré avec l’option SQL_IDENTIFIER_QUOTE_CHAR dans **SQLGetInfo**. Les listes de caractères spéciaux et de mots clés sont extraites avec les options SQL_SPECIAL_CHARACTERS et SQL_KEYWORDS dans **SQLGetInfo**.  
  
 Pour garantir la sécurité, les applications interopérables encadrent souvent tous les identificateurs, à l’exception de ceux pour les pseudo-colonnes, telles que la colonne ROWID dans Oracle. **SQLSpecialColumns** retourne une liste de pseudo-colonnes. De même, s’il existe des restrictions spécifiques à l’application permettant d’afficher les caractères spéciaux dans un nom d’objet, il est préférable que les applications interopérables n’utilisent pas de caractères spéciaux dans ces positions.

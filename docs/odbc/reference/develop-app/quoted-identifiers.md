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
manager: craigg
ms.openlocfilehash: b0a81237eddd4836394cc9797a79690ba4b49a35
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62861643"
---
# <a name="quoted-identifiers"></a>Identificateurs entre guillemets
Dans une instruction SQL, les identificateurs contenant des caractères spéciaux ou des mots clés de correspondance doivent être placés entre *guillemets identificateur*; les identificateurs placés entre ces caractères sont appelés *d’identificateursentreguillemets*(également appelé *identificateurs délimités* dans SQL-92). Par exemple, l’identificateur de comptes fournisseurs est citée dans l’exemple suivant **sélectionnez** instruction :  
  
```  
SELECT * FROM "Accounts Payable"  
```  
  
 La raison pour les identificateurs consiste à rendre l’instruction analysable. Par exemple, si les comptes fournisseurs pas de guillemets dans l’instruction précédente, l’analyseur supposent portaient sur deux tables, comptes et à payer et retourner une erreur de syntaxe, elles n’étaient pas séparés par une virgule. L’identificateur de caractère de guillemet est spécifique au pilote et est récupérée avec l’option SQL_IDENTIFIER_QUOTE_CHAR dans **SQLGetInfo**. Les listes des caractères spéciaux et des mots clés sont récupérés avec les options SQL_SPECIAL_CHARACTERS et SQL_KEYWORDS **SQLGetInfo**.  
  
 Pour plus de sécurité, les applications interopérables devis souvent tous les identificateurs à l’exception de celles des pseudo colonnes, telles que la colonne ROWID dans Oracle. **SQLSpecialColumns** retourne une liste des pseudo colonnes. En outre, s’il existe des restrictions spécifiques à l’application sur où les caractères spéciaux peuvent apparaître dans un nom d’objet, il est préférable pour les applications interopérables ne pas à utiliser des caractères spéciaux dans ces positions.

---
title: Identifiants cités (en anglais) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c03fa8bbc059566288997b29c899056f26de252
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282002"
---
# <a name="quoted-identifiers"></a>Identificateurs entre guillemets
Dans une déclaration SQL, les identifiants contenant des caractères spéciaux ou des mots clés de correspondance doivent être inclus dans des *caractères de citation d’identification*; les identificateurs inclus dans ces caractères sont connus sous le nom *d’identifiants cités* (également connus sous le nom *d’identifiants délimités* dans SQL-92). Par exemple, l’identifiant comptes à payer est cité dans la déclaration **SELECT** suivante :  
  
```  
SELECT * FROM "Accounts Payable"  
```  
  
 La raison de citer les identificateurs est de rendre la déclaration parseable. Par exemple, si les comptes payables n’étaient pas cités dans la déclaration précédente, le parseur supposerait qu’il y avait deux tableaux, comptes et payables, et retournerait une erreur de syntaxe qu’ils n’étaient pas séparés par une virgule. Le caractère de citation d’identification est spécifique au conducteur et est récupéré avec l’option SQL_IDENTIFIER_QUOTE_CHAR dans **SQLGetInfo**. Les listes de caractères spéciaux et de mots clés sont récupérées avec les options SQL_SPECIAL_CHARACTERS et SQL_KEYWORDS dans **SQLGetInfo**.  
  
 Pour être sûrs, les applications interopérables citent souvent tous les identificateurs sauf ceux des pseudo-colonnes, comme la colonne ROWID dans Oracle. **SQLSpecialColumns** retourne une liste de pseudo-colonnes. En outre, s’il existe des restrictions spécifiques aux applications sur l’endroit où des caractères spéciaux peuvent apparaître dans un nom d’objet, il est préférable pour les applications interopérables de ne pas utiliser des caractères spéciaux dans ces positions.

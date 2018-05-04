---
title: Identificateurs entre guillemets | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], quoted identifiers
- quoted identifiers [ODBC]
ms.assetid: 729ba55f-743b-4a04-8c39-ac0a9914211d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3af402bd63bf1892b1906da34114d5515e6dfa30
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="quoted-identifiers"></a>Identificateurs entre guillemets
Dans une instruction SQL, les identificateurs qui contiennent des caractères spéciaux ou des mots clés de correspondance doivent être placées entre *guillemets identificateur*; les identificateurs placés entre ces caractères sont appelés *identificateurs entre guillemets* (également appelé *des identificateurs délimités* dans SQL-92). Par exemple, l’identificateur de comptes fournisseurs est placé entre guillemets dans le code suivant **sélectionnez** instruction :  
  
```  
SELECT * FROM "Accounts Payable"  
```  
  
 Les identificateurs fait pour que l’instruction analysable. Par exemple, si les comptes fournisseurs pas de guillemets dans l’instruction précédente, l’analyseur supposent la présence de deux tables, les comptes et les fournisseurs et retourner une erreur de syntaxe qui ils n’étaient pas séparés par une virgule. L’identificateur de guillemet est spécifique au pilote et sont récupérée avec l’option SQL_IDENTIFIER_QUOTE_CHAR dans **SQLGetInfo**. Les listes des caractères spéciaux et des mots clés sont récupérés avec les options SQL_SPECIAL_CHARACTERS et SQL_KEYWORDS **SQLGetInfo**.  
  
 Pour plus de sécurité, les applications interopérables devis souvent tous les identificateurs à l’exception de celles des pseudo colonnes, telles que la colonne ROWID dans Oracle. **SQLSpecialColumns** retourne une liste des pseudo colonnes. En outre, s’il existe des restrictions spécifiques à l’application sur où les caractères spéciaux peuvent apparaître dans un nom d’objet, il est préférable pour les applications interopérables ne doit ne pas utiliser de caractères spéciaux dans les positions.

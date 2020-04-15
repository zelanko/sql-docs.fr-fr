---
title: Arguments d’identification Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- identifier arguments [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], identifier
ms.assetid: b9de003f-cb49-4dec-b528-14a5b8ff12bd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6831eab30daebe37baecebe3ed7053537d7de8f8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300159"
---
# <a name="identifier-arguments"></a>Arguments d’identificateur
Si une chaîne dans un argument d’identification est citée, le conducteur enlève les blancs de tête et de fuite et traite littéralement la chaîne dans les guillemets. Si la ficelle n’est pas citée, le conducteur enlève les blancs de fuite et plie la ficelle à la majuscule. La définition d’un argument d’identification à un pointeur nul renvoie SQL_ERROR et SQLSTATE HY009 (utilisation invalide du pointeur nul), à moins que l’argument soit un nom de catalogue et que les catalogues ne soient pas pris en charge.  
  
 Ces arguments sont traités comme des arguments d’identification si l’attribut de déclaration SQL_ATTR_METADATA_ID est réglé pour SQL_TRUE. Dans ce cas, le soulignement () et le signe de pourcentage (%) sera traité comme le personnage réel, pas comme un caractère de modèle de recherche. Ces arguments sont traités soit comme un argument ordinaire, soit comme un argument de modèle, selon l’argument, si cet attribut est réglé pour SQL_FALSE.  
  
 Bien que les identificateurs contenant des caractères spéciaux doivent être cités dans les déclarations SQL, ils ne doivent pas être cités lorsqu’ils sont adoptés comme des arguments de fonction de catalogue, parce que les caractères de citation transmis aux fonctions de catalogue sont interprétés littéralement. Supposons, par exemple, que le caractère de citation d’identification (qui est spécifique au conducteur et retourné par **SQLGetInfo**) est une double marque de citation ("). Le premier appel à **SQLTables renvoie** un ensemble de résultats contenant des renseignements sur le tableau des comptes à payer, tandis que le deuxième appel renvoie des renseignements sur le tableau « Comptes payables », ce qui n’est probablement pas ce qui était prévu.  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, "Accounts Payable", SQL_NTS, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "\"Accounts Payable\"", SQL_NTS, NULL, 0);  
```  
  
 Les identificateurs cités sont utilisés pour distinguer un vrai nom de colonne d’une pseudo-colonne du même nom, comme ROWID dans Oracle. Si "ROWID" est adopté dans un argument d’une fonction de catalogue, la fonction fonctionnera avec la pseudo-colonne ROWID si elle existe. Si la pseudo-colonne n’existe pas, la fonction fonctionnera avec la colonne "ROWID". Si ROWID est adopté dans un argument d’une fonction de catalogue, la fonction fonctionnera avec la colonne ROWID.  
  
 Pour plus d’informations sur les identifiants cités, voir [Identifiers cités](../../../odbc/reference/develop-app/quoted-identifiers.md).

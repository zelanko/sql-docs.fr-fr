---
title: Arguments d’identificateur | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 156dfaf5c6a6a4ec06a0c96b5f726383cba32ba6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47609927"
---
# <a name="identifier-arguments"></a>Arguments d’identificateur
Si une chaîne dans un argument de l’identificateur est entre guillemets, le pilote supprime de début et les espaces à droite et traite littéralement la chaîne entre guillemets. Si la chaîne n’est pas mis entre guillemets, le pilote supprime les espaces à droite et des plis la chaîne en majuscules. La définition d’un argument d’identificateur pour un pointeur null retourne SQL_ERROR et SQLSTATE HY009 (utilisation non valide d’un pointeur null), sauf si l’argument est un nom de catalogue et de catalogues ne sont pas pris en charge.  
  
 Si l’attribut d’instruction SQL_ATTR_METADATA_ID a la valeur SQL_TRUE, ces arguments sont traités en tant qu’arguments de l’identificateur. Dans ce cas, le trait de soulignement (_) et le symbole de pourcentage (%) est considéré comme le caractère réel, pas comme un caractère de modèle de recherche. Ces arguments sont traitées comme un argument ordinaire ou un argument de modèle, en fonction de l’argument, si cet attribut a la valeur SQL_FALSE.  
  
 Bien que les identificateurs contenant des caractères spéciaux doivent être mis entre guillemets dans les instructions SQL, ils ne doivent pas être mis entre guillemets quand il est passé en tant qu’arguments de fonction de catalogue, étant donné que les caractères guillemet passés aux fonctions de catalogue sont interprétées littéralement. Par exemple, supposons que l’identificateur de caractère de guillemet (qui est spécifique au pilote et retournés via **SQLGetInfo**) est un guillemet double («). Le premier appel à **SQLTables** retourne un jeu de résultats contenant des informations sur la table de comptes fournisseurs, tandis que le deuxième appel retourne des informations sur la table « Comptabilité », qui est probablement pas ce qui a été prévu.  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, "Accounts Payable", SQL_NTS, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "\"Accounts Payable\"", SQL_NTS, NULL, 0);  
```  
  
 Identificateurs entre guillemets sont utilisés pour distinguer un nom de colonne true à partir d’une pseudo-colonne du même nom, tels que le ROWID dans Oracle. Si « ROWID » est passée dans un argument d’une fonction de catalogue, la fonction fonctionnera avec la pseudo-colonne ROWID si elle existe. Si la colonne pseudo-élément n’existe pas, la fonction ne fonctionnera avec la colonne « ROWID ». Si ROWID est passée dans un argument d’une fonction de catalogue, la fonction ne fonctionnera avec la colonne de ligne ROWID.  
  
 Pour plus d’informations sur les identificateurs entre guillemets, consultez [identificateurs entre guillemets](../../../odbc/reference/develop-app/quoted-identifiers.md).

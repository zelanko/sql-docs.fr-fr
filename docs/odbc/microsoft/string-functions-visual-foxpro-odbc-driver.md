---
title: Fonctions (pilote ODBC de Visual FoxPro) de chaîne | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC string functions [ODBC]
- string functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], string functions
- FoxPro ODBC driver [ODBC], string functions
ms.assetid: 1974fd26-ef0d-45d5-860b-298917c8e9c3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a9e1c94eec150cc24522cd6e4c57eb35b4a2126
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270915"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>Fonctions de chaîne (pilote ODBC Visual FoxPro)
Le tableau suivant répertorie les fonctions de manipulation de chaîne ODBC pris en charge par le pilote ODBC Visual FoxPro ; lors de la grammaire de Visual FoxPro pour la même fonction diffère de la syntaxe ODBC, le Visual FoxPro équivalent est répertorié.  
  
|Grammaire ODBC|Grammaire de Visual FoxPro|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|CHAR *(code)*|CHR *(string_exp)*|  
|CONCAT *(string_exp1, string_exp2)*|*string_exp1 + string_exp2*|  
|DIFFÉRENCE *(string_exp1, string_exp2)*||  
|Insérer *(string_exp1, début, longueur, string_exp2)*|STUFF *(string_exp1, début, longueur, string_exp2)*|  
|LCASE *(string_exp)*|INFÉRIEUR *(exp_chaîne)*|  
|GAUCHE *(exp_chaîne, décompte)*||  
|LONGUEUR *(exp_chaîne)*|LEN *(string_exp)*|  
|LTRIM *(string_exp)*||  
|RÉPÉTEZ *(exp_chaîne, décompte)*|RÉPLIQUER *(exp_chaîne, décompte)*|  
|Remplacez *(string_exp1, string_exp2, exp_chaîne3)*|STRTRAN *(string_exp1, string_exp2, exp_chaîne3)*|  
|DROITE *(exp_chaîne, décompte)*||  
|RTRIM *(string_exp)*||  
|SOUNDEX *(string_exp)*||  
|ESPACE *(nombre)*||  
|SOUS-chaîne *(exp_chaîne, début, longueur)*|SUBSTR *(exp_chaîne, début, longueur)*|  
|UCASE *(exp_chaîne)*|UPPER *(string_exp)*|

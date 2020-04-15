---
title: Fonctions de chaîne (Visual FoxPro ODBC Driver) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 988ba23b95f6b138148b1fa17ad303d7aa2dc895
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299189"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>Fonctions de chaîne (pilote ODBC Visual FoxPro)
Le tableau suivant répertorie les fonctions de manipulation des cordes ODBC soutenues par le Visual FoxPro ODBC Driver; lorsque la grammaire Visual FoxPro pour la même fonction diffère de la syntaxe ODBC, l’équivalent Visual FoxPro est répertorié.  
  
|Grammaire ODBC|Grammaire visuelle FoxPro|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|CHAR *(code)*|CHR *(string_exp)*|  
|CONCAT *(string_exp1, string_exp2)*|*string_exp1 et string_exp2*|  
|DIFFERENCE *(string_exp1, string_exp2)*||  
|INSERT *(string_exp1, départ, longueur, string_exp2)*|STUFF *(string_exp1, départ, longueur, string_exp2)*|  
|LCASE *(string_exp)*|LOWER *(string_exp)*|  
|LEFT *(string_exp, compte)*||  
|LENGTH *(string_exp)*|LEN *(string_exp)*|  
|LTRIM *(string_exp)*||  
|REPEAT *(string_exp, compte)*|REPLICATE *(string_exp, compte)*|  
|REPLACE *(string_exp1, string_exp2, string_exp3)*|STRTRAN *(string_exp1, string_exp2, string_exp3)*|  
|RIGHT *(string_exp, compte)*||  
|RTRIM *(string_exp)*||  
|SOUNDEX *(string_exp)*||  
|ESPACE *(compte)*||  
|SUBSTRING *(string_exp, départ, longueur)*|SUBSTR *(string_exp, départ, longueur)*|  
|UCASE *(string_exp)*|UPPER *(string_exp)*|

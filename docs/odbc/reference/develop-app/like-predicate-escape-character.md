---
title: LIKE Predicate Escape Character (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate [ODBC]
- escape sequences [ODBC], LIKE predicate
ms.assetid: 185d6109-48cf-4981-bc40-ec2a4a90cafc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2e4f04b12911145eede3354532736cb92f1ae413
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306150"
---
# <a name="like-predicate-escape-character"></a>Caractère d’échappement du prédicat LIKE
Dans un **prédicat LIKE,** le signe pour cent (%) correspond à zéro ou plus de n’importe quel personnage et le soulignement () correspond à n’importe quel personnage. Pour correspondre à un signe réel pour cent ou de souligner dans un **predicate LIKE,** un personnage d’évasion doit venir avant le signe pour cent ou souligner. La séquence d’évasion qui définit le personnage **d’évasion PRÉdicate LIKE** est :  
  
 **Évasion 'caractère** *d’évasion* **''**  
  
 où *le caractère d’évasion* est n’importe quel personnage pris en charge par la source de données.  
  
 Pour plus d’informations sur la séquence d’évasion LIKE, voir [LA séquence d’évasion LIKE](../../../odbc/reference/appendixes/like-escape-sequence.md) dans l’annexe C: SQL Grammar.  
  
 Par exemple, les déclarations SQL suivantes créent le même ensemble de résultats de noms de clients qui commencent par les caractères "%AAA". La première déclaration utilise la syntaxe de séquence d’évacuation. La deuxième déclaration utilise la syntaxe native pour Microsoft® Access et n’est pas interopérable. Notez que le deuxième pour cent de caractère dans chaque **predicate LIKE** est un personnage wildcard qui correspond à zéro ou plus de n’importe quel personnage.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Pour déterminer si le caractère **d’évasion JUST** est pris en charge par une source de données, une application appelle **SQLGetInfo** avec l’option SQL_LIKE_ESCAPE_CLAUSE.

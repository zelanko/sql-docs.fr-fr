---
title: COMME caractère d’échappement de prédicat | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 20310c60759aea17d61b9252fd73d226567a7a54
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68027227"
---
# <a name="like-predicate-escape-character"></a>Caractère d’échappement du prédicat LIKE
Dans un **comme** prédicat, le symbole de pourcentage (%) correspond à zéro ou plus de n’importe quel caractère et le trait de soulignement (_) correspond à tout caractère. Pour faire correspondre un signe pourcent ou de traits de soulignement dans un **comme** prédicat, un caractère d’échappement doit être placée avant le signe de pourcentage ou un trait de soulignement. La séquence d’échappement qui définit le **comme** caractère d’échappement de prédicat est :  
  
 **{escape '** *-caractère d’échappement* **'}**  
  
 où *-caractère d’échappement* est n’importe quel caractère pris en charge par la source de données.  
  
 Pour plus d’informations sur le type des séquence d’échappement, consultez [comme séquence d’échappement](../../../odbc/reference/appendixes/like-escape-sequence.md) dans l’annexe c : Grammaire SQL.  
  
 Par exemple, les instructions SQL suivantes créent le même jeu de résultats du client des noms qui commencent par les caractères « % AAA ». La première instruction utilise la syntaxe de la séquence d’échappement. La deuxième instruction utilise la syntaxe native pour Microsoft® Access et n’est pas interopérable. Notez que le deuxième caractère de pourcentage dans chaque **comme** prédicat est un caractère générique qui correspond à zéro ou plus de n’importe quel caractère.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 Pour déterminer si le **comme** caractère d’échappement de prédicat est pris en charge par une source de données, une application appelle **SQLGetInfo** avec l’option SQL_LIKE_ESCAPE_CLAUSE.

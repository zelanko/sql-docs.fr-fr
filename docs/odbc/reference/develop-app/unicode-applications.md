---
title: Applications Unicode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], compiling as Unicode application
- Unicode [ODBC], functions
- compiling Unicode applications [ODBC]
- functions [ODBC], Unicode functions
ms.assetid: 7986c623-2792-4e77-bfee-c86cbf84f08d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 32b4125d0ecb1f15fab00119a8ef4ed361b6db72
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087738"
---
# <a name="unicode-applications"></a>Applications Unicode
Vous pouvez recompiler une application en tant qu’application Unicode de l’une des deux manières suivantes :  
  
-   Incluez les **#define** Unicode contenues dans le fichier d’en-tête sqlucode. h dans l’application.  
  
-   Compilez l’application avec l’option Unicode du compilateur. (Cette option sera différente pour différents compilateurs.)  
  
 Pour convertir une application ANSI en application Unicode, écrivez l’application pour stocker et transmettre des données Unicode. En outre, les appels aux fonctions qui prennent en charge les arguments SQLPOINTER doivent être convertis pour utiliser le nombre d’octets.  
  
 Après la compilation d’une application en tant qu’application Unicode, si l’application appelle une fonction API ODBC (sans suffixe), le gestionnaire de pilotes reconnaît l’application en tant qu’application Unicode et convertit l’appel de fonction en fonction Unicode (avec le suffixe *W* ) si le pilote sous-jacent prend en charge Unicode. Quand une application ANSI effectue un appel de fonction sans suffixe, le gestionnaire de pilotes la convertit en ANSI si le pilote sous-jacent prend en charge ANSI. Si l’application et le pilote prennent en charge le même codage de caractères, le gestionnaire de pilotes passe les appels au pilote (avec certaines exceptions pour les applications ANSI).  
  
 Une application peut appeler à la fois des fonctions Unicode (avec le suffixe *W* ) et des fonctions ANSI (avec ou sans suffixe *A* ). Les appels de fonction Unicode et ANSI peuvent être mélangés. Si la bibliothèque de curseurs doit être utilisée, toutefois, les appels de fonction Unicode et ANSI ne peuvent pas être mélangés. La bibliothèque de curseurs est de type Unicode ou ANSI, et non d’un mélange.  
  
 Une application peut être écrite de telle sorte qu’elle puisse être compilée comme une application Unicode ou une application ANSI. Dans ce cas, les types de données caractère peuvent être déclarés comme SQL_C_TCHAR. Il s’agit d’une macro qui insère SQL_C_WCHAR si l’application est compilée en tant qu’application Unicode ou insère SQL_C_CHAR si elle est compilée en tant qu’application ANSI. Le programmeur de l’application doit faire attention aux fonctions qui prennent SQLPOINTER comme argument, car la taille de l’argument de longueur change (pour les types de données de type chaîne), selon que l’application est ANSI ou Unicode.  
  
 Une fonction peut être appelée de trois façons : en tant qu’appel de fonction Unicode uniquement (avec le suffixe *W* ), en tant qu’appel de fonction ANSI uniquement (avec le suffixe *a* ), ou en tant qu’appel de fonction ODBC sans suffixe. Les arguments des trois formes d’une fonction sont identiques. Seules les fonctions avec des \* arguments SQLCHAR ou des arguments SQLPOINTER qui pointent vers des chaînes requièrent des formulaires Unicode et ANSI. Pour les fonctions qui ont des arguments qui peuvent être déclarés comme type de caractère, tel que **SQLBindCol** ou **SQLGetData** (qui n’ont pas de formulaires Unicode et ANSI), l’argument peut être déclaré comme type Unicode, le type ANSI ou, dans le cas d’un argument de type C, la macro SQL_C_TCHAR. Pour plus d’informations, consultez [données Unicode](../../../odbc/reference/develop-app/unicode-data.md).  
  
 Une application peut être écrite en tant qu’application Unicode même si aucun pilote Unicode n’est disponible pour son utilisation. Le gestionnaire de pilotes mappera des fonctions Unicode et des types de données à ANSI. Il existe des restrictions concernant les mappages Unicode à ANSI qui peuvent être exécutés. L’existence d’un pilote Unicode pour l’application Unicode à utiliser entraînera de meilleures performances et supprimera les restrictions inhérentes aux mappages Unicode à ANSI.

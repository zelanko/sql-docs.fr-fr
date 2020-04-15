---
title: Applications Unicode Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94bd5211c878904453624adb2acd0fe435ebc812
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298945"
---
# <a name="unicode-applications"></a>Applications Unicode
Vous pouvez recomposer une application unicode de l’une des deux façons :  
  
-   Inclure le **#define** Unicode contenu dans le fichier d’en-tête Sqlucode.h dans l’application.  
  
-   Compilez l’application avec l’option Unicode du compilateur. (Cette option sera différente pour différents compilateurs.)  
  
 Pour convertir une application ANSI en application Unicode, écrivez l’application pour stocker et passer les données Unicode. De plus, les appels à des fonctions qui prennent en charge les arguments de SQLPOINTER doivent être convertis en compte d’utilisation d’octets.  
  
 Une fois qu’une application est compilée sous forme d’application Unicode, si l’application appelle une fonction API ODBC (sans suffixe), le Gestionnaire de pilote reconnaît l’application comme une application Unicode et convertit l’appel de fonction à une fonction Unicode (avec le suffixe *W)* si le pilote sous-jacent prend en charge Unicode. Lorsqu’une application ANSI effectue un appel de fonction sans suffixe, le Driver Manager le convertit en ANSI si le conducteur sous-jacent prend en charge l’ANSI. Si l’application et le conducteur prennent en charge le même codage de caractère, le gestionnaire de pilote passe les appels au conducteur (à quelques exceptions près pour les applications ANSI).  
  
 Une application peut appeler à la fois les fonctions Unicode (avec le suffixe *W)* et les fonctions ANSI (avec ou sans le suffixe *A).* Les appels de fonction Unicode et ANSI peuvent être mélangés. Toutefois, si la bibliothèque de curseurs doit être utilisée, les appels de fonction Unicode et ANSI ne peuvent pas être mélangés. La bibliothèque de curseurs est Unicode ou ANSI, pas un mélange.  
  
 Une application peut être écrite de telle sorte qu’elle puisse être compilée comme une application Unicode ou une application ANSI. Dans ce cas, les types de données de caractère peuvent être déclarés comme SQL_C_TCHAR. Il s’agit d’une macro qui insère SQL_C_WCHAR si l’application est compilée sous forme d’application Unicode ou insère SQL_C_CHAR si elle est compilée comme une application ANSI. Le programmeur d’application doit faire attention aux fonctions qui prennent SQLPOINTER comme argument, car la taille de l’argument de longueur va changer (pour les types de données de chaîne) selon que l’application est ANSI ou Unicode.  
  
 Une fonction peut être appelée de trois façons : comme un appel de fonction Unicode seulement (avec le suffixe *W),* comme un appel de fonction ANSI-seulement (avec le suffixe *A),* ou comme l’appel de fonction ODBC sans suffixe. Les arguments des trois formes d’une fonction sont identiques. Seules les fonctions avec \* des arguments SQLCHAR ou des arguments SQLPOINTER qui pointent vers les chaînes nécessitent unicode et ansI formes. Pour les fonctions qui ont des arguments qui peuvent être déclarés comme un type de caractère, tels que **SQLBindCol** ou **SQLGetData** (qui n’ont pas de formulaires Unicode et ANSI), l’argument peut être déclaré comme le type Unicode, le type ANSI, ou dans le cas d’un argument de type C, le SQL_C_TCHAR macro. Pour plus d’informations, voir [Unicode Data](../../../odbc/reference/develop-app/unicode-data.md).  
  
 Une application peut être écrite sous forme d’application Unicode même si aucun pilote Unicode n’est disponible pour qu’elle puisse travailler. Le Driver Manager cartographiera les fonctions unicode et les types de données à l’ANSI. Il existe certaines restrictions à l’Unicode aux cartographies ANSI qui peuvent être effectuées. L’existence d’un pilote Unicode pour l’application Unicode pour travailler avec se traduira par de meilleures performances et supprimera les restrictions inhérentes à l’Unicode aux cartographies ANSI.

---
title: Les Applications Unicode | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 7fc9cb98837d206d5279d1f14d4a57ce56782759
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62633379"
---
# <a name="unicode-applications"></a>Applications Unicode
Vous pouvez recompiler une application en tant qu’Unicode application de deux manières :  
  
-   Inclure le Unicode **#define** contenus dans le fichier d’en-tête Sqlucode.h dans l’application.  
  
-   Compilez l’application avec l’option du compilateur Unicode. (Cette option sera différente pour différents compilateurs.)  
  
 Pour convertir une application ANSI à une application Unicode, écrivez l’application pour stocker et transmettre les données Unicode. En outre, les appels aux fonctions qui prennent en charge les arguments SQLPOINTER doivent être convertis pour utiliser le nombre d’octets.  
  
 Après la compilation d’une application comme une application Unicode, si l’application appelle une fonction API ODBC (sans suffixe), le Gestionnaire de pilotes reconnaît l’application comme une application Unicode et convertit l’appel de fonction à une fonction Unicode (avec la  *W* suffixe) si le pilote sous-jacent prend en charge Unicode. Lorsqu’une application ANSI appelle une fonction sans suffixe, le Gestionnaire de pilote le convertit en ANSI si le pilote sous-jacent prend en charge ANSI. Si l’application et le pilote prend en charge de l’encodage de caractères même, le Gestionnaire de pilotes transmet les appels par le biais du pilote (avec certaines exceptions pour les applications ANSI).  
  
 Une application peut appeler les deux fonctions Unicode (avec le *W* suffixe) et les fonctions ANSI (avec ou sans le *A* suffixe). Appels de fonction ANSI et Unicode peuvent être mélangés. Si la bibliothèque de curseurs doit être utilisée, toutefois, les appels de fonction Unicode et ANSI ne peut pas être mélangées. La bibliothèque de curseurs est au format Unicode ou ANSI, pas un mélange des deux.  
  
 Une application peut être écrite de sorte qu’il peut être compilé en tant qu’une application Unicode ou une application ANSI. Dans ce cas, les types de données caractères peuvent être déclarés comme SQL_C_TCHAR. Il s’agit d’une macro qui insère SQL_C_WCHAR si l’application est compilée dans une application Unicode ou insère SQL_C_CHAR s’il est compilé en tant qu’une application ANSI. Les programmeurs d’applications doivent être prudent de fonctions qui acceptent SQLPOINTER comme argument, car la taille de l’argument de longueur change (pour les types de données de chaîne) selon que l’application est ANSI ou Unicode.  
  
 Une fonction peut être appelée de trois manières : en tant qu’un appel de fonction Unicode uniquement (avec le *W* suffixe), comme un appel de fonction ANSI uniquement (avec le *A* suffixe), ou en tant que l’appel de fonction ODBC sans suffixe. Les arguments à trois formes possibles d’une fonction sont identiques. Seules les fonctions avec SQLCHAR \* arguments ou des arguments SQLPOINTER qui pointent vers les chaînes nécessitent des formulaires Unicode et ANSI. Pour les fonctions qui possèdent des arguments qui peuvent être déclarées comme type de caractère, tel que **SQLBindCol** ou **SQLGetData** (qui n’ont pas les formulaires Unicode et ANSI), l’argument peut être déclaré comme type Unicode, l’ANSI type, ou dans le cas d’un C argument, la macro SQL_C_TCHAR. Pour plus d’informations, consultez [les données Unicode](../../../odbc/reference/develop-app/unicode-data.md).  
  
 Une application peut être écrit comme une application Unicode, même si aucun pilote Unicode n’est disponibles pour qu’il fonctionne avec. Le Gestionnaire de pilotes mappera les types de données et des fonctions Unicode vers ANSI. Il existe certaines restrictions au Unicode aux mappages ANSI qui peuvent être effectuées. L’existence d’un pilote Unicode pour l’application Unicode pour travailler avec entraîne de meilleures performances et supprime les restrictions inhérentes à la Unicode aux mappages d’ANSI.

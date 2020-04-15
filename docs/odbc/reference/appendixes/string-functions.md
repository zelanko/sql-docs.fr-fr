---
title: Fonctions de chaîne (fonctions de chaîne) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], string functions
- string functions [ODBC]
ms.assetid: 270f669e-8aab-4db0-95a4-f2b3c69538b3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d9323809028ad170a4811b1af8b6e276cdbb4293
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302840"
---
# <a name="string-functions"></a>Fonctions de chaîne
Le tableau suivant répertorie les fonctions de manipulation des cordes. Une application peut déterminer quelles fonctions de chaîne sont prises en charge par un conducteur en appelant **SQLGetInfo** avec un *type d’information* de SQL_STRING_FUNCTIONS.  
  
## <a name="remarks"></a>Notes  
 Arguments désignés comme *string_exp* peuvent être le nom d’une colonne, un *caractère-corde-littérale*, ou le résultat d’une autre fonction scalaire, où le type de données sous-jacente peut être représenté comme SQL_CHAR, SQL_VARCHAR, ou SQL_LONGVARCHAR.  
  
 Les arguments désignés comme *character_exp* sont une chaîne de caractères à longueur variable.  
  
 Les arguments désignés comme *le début,* *la longueur,* ou le *compte* peuvent être un *numérique-littérale* ou le résultat d’une autre fonction scalaire, où le type de données sous-jacent peut être représenté comme SQL_TINYINT, SQL_SMALLINT, ou SQL_INTEGER.  
  
 Les fonctions de chaîne énumérées ici sont basées à 1; c’est-à-dire que le premier personnage de la chaîne est le caractère 1.  
  
 Les fonctions de scalaire des cordes BIT_LENGTH, CHAR_LENGTH, CHARACTER_LENGTH, OCTET_LENGTH et POSITION ont été ajoutées dans ODBC 3.0 pour s’aligner sur SQL-92.  
  
|Fonction|Description|  
|--------------|-----------------|  
|**ASCII (** _string_exp_ **)** (ODBC 1.0)|Retourne la valeur de code ASCII du caractère le plus à gauche de *string_exp* comme un intégrant.|  
|**BIT_LENGTH (** _string_exp_ **)** (ODBC 3.0)|Retourne la longueur en bits de l'expression de chaîne.<br /><br /> Ne fonctionne pas seulement pour les types de données de chaîne, donc ne convertira pas implicitement *string_exp* en chaîne, mais retournera plutôt la taille (interne) de n’importe quel type de données qu’il est donné.|  
|**CHAR (** _code_ **)** (ODBC 1.0)|Retourne le caractère dont la valeur de code ASCII est spécifiée par *code*. La valeur du *code* doit être comprise entre 0 et 255; autrement, la valeur de rendement dépend de la source de données.|  
|**CHAR_LENGTH (** _string_exp_ **)** (ODBC 3.0)|Retourne la longueur dans les caractères de l’expression de la chaîne, si l’expression de la chaîne est d’un type de données de caractère ; sinon, retourne la longueur dans les octets de l’expression de la chaîne (le plus petit integer pas moins que le nombre de bits divisés par 8). (Cette fonction est la même que la fonction CHARACTER_LENGTH.)|  
|**CHARACTER_LENGTH (** _string_exp_ **)** (ODBC 3.0)|Retourne la longueur dans les caractères de l’expression de la chaîne, si l’expression de la chaîne est d’un type de données de caractère ; sinon, retourne la longueur dans les octets de l’expression de la chaîne (le plus petit integer pas moins que le nombre de bits divisés par 8). (Cette fonction est la même que la fonction CHAR_LENGTH.)|  
|**CONCAT (** _string_exp1_,_string_exp2_**)** (ODBC 1.0)|Retourne une chaîne de caractères qui est le résultat de concatenating *string_exp2* à *string_exp1*. La chaîne résultante dépend de SGBD. Par exemple, si la colonne représentée par *string_exp1* contenait une valeur NULL, DB2 retournerait NULL, mais SQL Server retournerait la chaîne non-NULL.|  
|**DIFFERENCE (** _string_exp1_,_string_exp2_**)** (ODBC 2.0)|Retourne une valeur d’intégrant qui indique la différence entre les valeurs retournées par la fonction SOUNDEX pour *string_exp1* et *string_exp2*.|  
|**INSERT (** _string_exp1_, *départ*, *longueur*, _string_exp2_**)** (ODBC 1.0)|Retourne une chaîne de caractères où les personnages de *longueur* ont été supprimés de *string_exp1*, à partir de *début*, et où *string_exp2* a été inséré dans *string_exp,* à partir du *début*.|  
|**LCASE (** _string_exp_ **)** (ODBC 1.0)|Retourne une chaîne égale à celle de *string_exp,* avec tous les caractères majuscules convertis en lowercase.|  
|**LEFT (** _string_exp_, _compter_**)** (ODBC 1.0)|Retourne les personnages *de comptage* les plus à gauche de *string_exp*.|  
|**LENGTH (** _string_exp_ **)** (ODBC 1.0)|Retourne le nombre de caractères dans *string_exp,* à l’exclusion des blancs de fuite.<br /><br /> **LENGTH** n’accepte que les cordes. Par conséquent, convertira implicitement *string_exp* en chaîne, et retournera la longueur de cette chaîne (pas la taille interne du datatype).|  
|**LOCATE (** _string_exp1_, *string_exp2*[, *départ*]**)** (ODBC 1.0)|Retourne la position de départ de la première occurrence de *string_exp1* dans *string_exp2*. La recherche de la première occurrence de *string_exp1* commence par la première position de caractère dans *string_exp2* à moins que l’argument facultatif, *commencer*, est spécifié. Si *le démarrage* est spécifié, la recherche commence avec la position de caractère indiquée par la valeur de *départ*. La première position de caractère dans *string_exp2* est indiquée par la valeur 1. Si *string_exp1* ne se trouve pas dans *string_exp2,* la valeur 0 est retournée.<br /><br /> Si une application peut appeler la fonction scalaire LOCATE avec le *string_exp1,* *string_exp2,* et *commencer* les arguments, le conducteur retourne SQL_FN_STR_LOCATE lorsque **SQLGetInfo** est appelé avec une *option* de SQL_STRING_FUNCTIONS. Si l’application peut appeler la fonction scalaire LOCATE avec seulement les *arguments string_exp1* et *string_exp2,* le conducteur retourne SQL_FN_STR_LOCATE_2 lorsque **SQLGetInfo** est appelé avec une *option* de SQL_STRING_FUNCTIONS. Les conducteurs qui prennent en charge l’appel de la fonction LOCATE avec deux ou trois arguments retournent à la fois SQL_FN_STR_LOCATE et SQL_FN_STR_LOCATE_2.|  
|**LTRIM (** _string_exp_ **)** (ODBC 1.0)|Retourne les personnages de *string_exp*, avec des blancs de tête supprimés.|  
|**OCTET_LENGTH (** _string_exp_ **)** (ODBC 3.0)|Retourne la longueur en octets de l'expression de chaîne. Le résultat est le plus petit entier qui n'est pas inférieur au nombre de bits divisé par 8.<br /><br /> Ne fonctionne pas seulement pour les types de données de chaîne, donc ne convertira pas implicitement *string_exp* en chaîne, mais retournera plutôt la taille (interne) de n’importe quel type de données qu’il est donné.|  
|**POSITION (** _CHARACTER_EXP_ **IN** _CHARACTER_EXP_**)** (ODBC 3.0)|Retourne la position de la première expression de caractère dans la deuxième expression de caractère. Le résultat est un numérique exact avec une précision définie par implémentation et une échelle de 0.|  
|**REPEAT (** _string_exp,_ _compte_**)** (ODBC 1.0)|Retourne une chaîne de caractères composée de *string_exp* temps de *comptage* répété.|  
|**REPLACE (** _string_exp1_, *string_exp2*, _string_exp3_**)** (ODBC 1.0)|Rechercher *string_exp1* pour les string_exp2 *,* et remplacer par *string_exp3*.|  
|**RIGHT (** _string_exp_, _compter_**)** (ODBC 1.0)|Retourne les personnages de *comptage* les plus à droite de *string_exp*.|  
|**RTRIM (** _string_exp_ **)** (ODBC 1.0)|Retourne les personnages de *string_exp* avec des blancs de fuite enlevés.|  
|**SOUNDEX(** _string_exp_ **)** (ODBC 2.0)|Retourne une chaîne de caractères dépendante de la source de données représentant le son des mots dans *string_exp*. Par exemple, SQL Server renvoie un code SOUNDEX à 4 chiffres; Oracle renvoie une représentation phonétique de chaque mot.|  
|**SPACE (** _compter_ **)** (ODBC 2.0)|Retourne une chaîne de caractères composée d’espaces de *comptage.*|  
|**SUBSTRING (** _string_exp_, *départ*, longueur **)** (ODBC 1.0)|Retourne une chaîne de caractère qui est dérivée de *string_exp*, à partir de la position de caractère spécifiée par *début* pour *les caractères de longueur.*|  
|**UCASE (** _string_exp_ **)** (ODBC 1.0)|Retourne une chaîne égale à celle de *string_exp,* avec tous les caractères minuscules convertis en uppercase.|

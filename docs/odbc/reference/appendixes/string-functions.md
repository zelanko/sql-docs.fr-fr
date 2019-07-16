---
title: Fonctions de chaîne | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fd4ec3e05acfd4faaafd38a79e48c67d03d86bd4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070175"
---
# <a name="string-functions"></a>Fonctions de chaîne
Le tableau suivant répertorie les fonctions de manipulation de chaîne. Une application peut déterminer les fonctions de chaîne sont prises en charge par un pilote en appelant **SQLGetInfo** avec un *d’informations, tapez* de SQL_STRING_FUNCTIONS.  
  
## <a name="remarks"></a>Notes  
 Arguments indiqués par *exp_chaîne* peut être le nom d’une colonne, une *littéral de chaîne de caractères*, ou le résultat d’une autre fonction scalaire, où le type de données sous-jacent peut être représenté comme SQL_CHAR, SQL_ VARCHAR ou SQL_LONGVARCHAR.  
  
 Arguments indiqués par *exp_caractère* sont une chaîne de caractères de longueur variable.  
  
 Arguments indiqués par *Démarrer*, *longueur*, ou *nombre* peut être un *littéral numérique* ou le résultat d’une autre fonction scalaire, où le type de données sous-jacent peut être représentée comme SQL_TINYINT, SQL_SMALLINT ou SQL_INTEGER.  
  
 Les fonctions de chaîne répertoriées ici sont de base 1 ; Autrement dit, le premier caractère dans la chaîne est le caractère 1.  
  
 Les fonctions scalaires de chaîne BIT_LENGTH, CHAR_LENGTH, CHARACTER_LENGTH, OCTET_LENGTH et POSITION ont été ajoutées dans ODBC 3.0 pour les aligner avec SQL-92.  
  
|Fonction|Description|  
|--------------|-----------------|  
|**ASCII (** _exp_chaîne_ **)** (ODBC version 1.0)|Retourne la valeur du code ASCII du caractère à l’extrême gauche de *exp_chaîne* sous forme d’entier.|  
|**BIT_LENGTH (** _exp_chaîne_ **)** (ODBC 3.0)|Retourne la longueur en bits de l'expression de chaîne.<br /><br /> Inopérante uniquement pour les types de données de chaîne, par conséquent ne sera pas implicitement convert *exp_chaîne* en chaîne mais retournera la taille (interne) de quelque type de données lui est attribué.|  
|**CHAR (** _code_ **)** (ODBC version 1.0)|Retourne le caractère qui a l’ASCII code la valeur spécifiée par *code*. La valeur de *code* doit être comprise entre 0 et 255 ; sinon, la valeur de retour est dépend de la source de données.|  
|**CHAR_LENGTH (** _exp_chaîne_ **)** (ODBC 3.0)|Retourne la longueur en caractères de l’expression de chaîne, si l’expression de chaîne est un type de données caractères ; Sinon, retourne la longueur en octets de l’expression de chaîne (le plus petit entier pas moins que le nombre de bits divisé par 8). (Cette fonction est identique à la fonction CHARACTER_LENGTH.)|  
|**CHARACTER_LENGTH (** _exp_chaîne_ **)** (ODBC 3.0)|Retourne la longueur en caractères de l’expression de chaîne, si l’expression de chaîne est un type de données caractères ; Sinon, retourne la longueur en octets de l’expression de chaîne (le plus petit entier pas moins que le nombre de bits divisé par 8). (Cette fonction est identique à la fonction CHAR_LENGTH.)|  
|**CONCAT (** _string_exp1_,_string_exp2_ **)** (ODBC 1.0)|Retourne une chaîne de caractères qui est le résultat de la concaténation *string_exp2* à *string_exp1*. La chaîne résultante dépend de SGBD. Par exemple, si la colonne représentée par *string_exp1* contenait une valeur NULL, DB2 retour NULL, mais SQL Server serait retournerait la chaîne non NULL.|  
|**DIFFÉRENCE (** _string_exp1_,_string_exp2_ **)** (ODBC 2.0)|Retourne une valeur entière qui indique la différence entre les valeurs retournées par la fonction SOUNDEX pour *string_exp1* et *string_exp2*.|  
|**Insérer (** _string_exp1_, *Démarrer*, *longueur*, _string_exp2_ **)** (ODBC version 1.0)|Retourne un caractère de chaîne où *longueur* caractères ont été supprimés de *string_exp1*, en commençant par *Démarrer*et où *string_exp2* a été inséré dans *exp_chaîne,* commençant à *Démarrer*.|  
|**LCASE (** _exp_chaîne_ **)** (ODBC version 1.0)|Retourne une chaîne égale à celle dans *exp_chaîne*, avec toutes les majuscules les caractères sont convertis en minuscules.|  
|**GAUCHE (** _exp_chaîne_, _nombre_ **)** (ODBC version 1.0)|Retourne le plus à gauche *nombre* caractères de *exp_chaîne*.|  
|**LONGUEUR (** _exp_chaîne_ **)** (ODBC version 1.0)|Retourne le nombre de caractères dans *exp_chaîne,* à l’exclusion des espaces blancs de fin.<br /><br /> **LONGUEUR** accepte uniquement les chaînes. Par conséquent convertira implicitement les *exp_chaîne* à une chaîne et retourne la longueur de cette chaîne (pas la taille interne du type de données).|  
|**LOCALISER (** _string_exp1_, *string_exp2*[, *Démarrer*] **)** (ODBC version 1.0)|Retourne la position de départ de la première occurrence de *string_exp1* dans *string_exp2*. La recherche de la première occurrence de *string_exp1* commence par la première position de caractère dans *string_exp2* , sauf si l’argument facultatif, *Démarrer*, est spécifié. Si *Démarrer* est spécifié, la recherche commence par la position du caractère indiquée par la valeur de *Démarrer*. Le premier caractère positionner dans *string_exp2* est indiqué par la valeur 1. Si *string_exp1* ne figure pas dans *string_exp2*, la valeur 0 est retournée.<br /><br /> Si une application peut appeler la fonction scalaire localiser avec le *string_exp1*, *string_exp2*, et *Démarrer* arguments, le pilote retourne SQL_FN_STR_LOCATE lorsque  **SQLGetInfo** est appelée avec un *Option* de SQL_STRING_FUNCTIONS. Si l’application peut appeler la fonction scalaire localiser avec uniquement le *string_exp1* et *string_exp2* arguments, le pilote retourne SQL_FN_STR_LOCATE_2 lorsque **SQLGetInfo**est appelée avec un *Option* de SQL_STRING_FUNCTIONS. Les pilotes qui prennent en charge l’appel de la fonction localiser avec deux ou trois arguments retournent SQL_FN_STR_LOCATE et SQL_FN_STR_LOCATE_2.|  
|**LTRIM (** _exp_chaîne_ **)** (ODBC version 1.0)|Retourne les caractères de *exp_chaîne*, avec des espaces de fin supprimés.|  
|**OCTET_LENGTH (** _exp_chaîne_ **)** (ODBC 3.0)|Retourne la longueur en octets de l'expression de chaîne. Le résultat est le plus petit entier qui n'est pas inférieur au nombre de bits divisé par 8.<br /><br /> Inopérante uniquement pour les types de données de chaîne, par conséquent ne sera pas implicitement convert *exp_chaîne* en chaîne mais retournera la taille (interne) de quelque type de données lui est attribué.|  
|**POSITION(** _character_exp_ **IN** _character_exp_ **)** (ODBC 3.0)|Retourne la position de la première expression de caractère dans la deuxième expression de caractères. Le résultat est une valeur numérique exacte avec une précision définie par l’implémentation et une échelle de 0.|  
|**RÉPÉTEZ (** _exp_chaîne,_ _nombre_ **)** (ODBC version 1.0)|Retourne une chaîne de caractères composée de *exp_chaîne* répété *nombre* fois.|  
|**Remplacer (** _string_exp1_, *string_exp2*, _exp_chaîne3_ **)** (ODBC 1.0)|Recherche *string_exp1* foroccurrences de *string_exp2*et remplacez-les par *exp_chaîne3*.|  
|**DROITE (** _exp_chaîne_, _nombre_ **)** (ODBC version 1.0)|Retourne le plus à droite *nombre* caractères de *exp_chaîne*.|  
|**RTRIM (** _exp_chaîne_ **)** (ODBC version 1.0)|Retourne les caractères de *exp_chaîne* avec espaces de fin supprimés.|  
|**SOUNDEX (** _exp_chaîne_ **)** (ODBC 2.0)|Retourne une chaîne de caractères dépendante de la source de données représentant le son de mots contenus dans *exp_chaîne*. Par exemple, SQL Server retourne un code SOUNDEX de 4 chiffres ; Oracle retourne une représentation phonétique de chaque mot.|  
|**ESPACE (** _nombre_ **)** (ODBC 2.0)|Retourne une chaîne de caractères composée de *nombre* espaces.|  
|**SUBSTRING (** _exp_chaîne_, *Démarrer*, longueur **)** (ODBC version 1.0)|Retourne une chaîne de caractères qui est dérivée de *exp_chaîne*, en commençant à la position de caractère spécifiée par *Démarrer* pour *longueur* caractères.|  
|**UCASE (** _exp_chaîne_ **)** (ODBC version 1.0)|Retourne une chaîne égale à celle dans *exp_chaîne*, avec toutes les minuscules en majuscules.|

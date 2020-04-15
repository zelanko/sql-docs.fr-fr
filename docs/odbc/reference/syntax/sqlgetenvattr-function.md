---
title: Fonction SQLGetEnvAttr (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetEnvAttr
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLGetEnvAttr
helpviewer_keywords:
- SQLGetEnvAttr function [ODBC]
ms.assetid: 01f4590f-427a-4280-a1c3-18de9f7d86c1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 77cd24386a8eea6769aee59f3674b681c516d9ed
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285309"
---
# <a name="sqlgetenvattr-function"></a>SQLGetEnvAttr, fonction
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLGetEnvAttr** retourne le réglage actuel d’un attribut de l’environnement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLGetEnvAttr(  
     SQLHENV        EnvironmentHandle,  
     SQLINTEGER     Attribute,  
     SQLPOINTER     ValuePtr,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *EnvironnementHandle*  
 [Entrée] Poignée de l’environnement.  
  
 *Attribut*  
 [Entrée] Attribut à récupérer.  
  
 *ValuePtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner la valeur actuelle de l’attribut spécifié par *Attribut*.  
  
 Si *ValuePtr* est NULL, *StringLengthPtr* retournera toujours le nombre total d’octets (à l’exclusion du caractère de résiliation nulle pour les données de caractère) disponible pour revenir dans le tampon indiqué par *ValuePtr*.  
  
 *BufferLength*  
 [Entrée] Si *ValuePtr* pointe vers une chaîne de caractères, cet argument devrait être la longueur de \* *ValuePtr*. Si \* *ValuePtr* est un intégrateur, *BufferLength* est ignoré. Si * \*ValuePtr* est une chaîne Unicode (lorsqu’il appelle **SQLGetEnvAttrW**), l’argument *BufferLength* doit être un nombre pair. Si la valeur d’attribut n’est pas une chaîne de caractères, *BufferLength* n’est pas utilisé.  
  
 *StringLengthPtr*  
 [Sortie] Un pointeur à un tampon dans lequel retourner le nombre total d’octets (à l’exclusion du caractère de résiliation nulle) disponible pour revenir dans * \*ValuePtr*. Si *ValuePtr* est un pointeur nul, aucune longueur n’est retournée. Si la valeur d’attribut est une chaîne de caractères et que le nombre d’octets disponibles pour revenir est supérieur ou égal à *BufferLength*, les données de \* *ValuePtr* sont tronquées à *BufferLength* moins la longueur d’un caractère de résiliation nulle et sont annulées par le conducteur.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetEnvAttr** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_ENV et une *poignée* *d’EnvironnementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLGetEnvAttr** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Les données \*retournées dans *ValuePtr* ont été tronquées pour être *BufferLength* moins le caractère de résiliation nulle. La longueur de la valeur de la chaîne fausse est retournée dans*stringLengthPtr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) **SQL_ATTR_ODBC_VERSION** n’a pas encore été fixé via **SQLSetEnvAttr**. Vous n’avez pas besoin de définir **SQL_ATTR_ODBC_VERSION** explicitement si vous utilisez **SQLAllocHandleStd**.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY092 HY092|Identification d’attribut/option invalide|La valeur spécifiée pour l’argument *Attribut* n’était pas valide pour la version d’ODBC étayée par le conducteur.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|La valeur spécifiée pour l’argument *Attribut* était un attribut d’environnement ODBC valide pour la version d’ODBC pris en charge par le conducteur, mais n’a pas été pris en charge par le conducteur.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur correspondant à *l’EnvironnementHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Pour une liste d’attributs, voir [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md). Il n’y a pas d’attributs d’environnement spécifiques au conducteur. Si *Attribute* spécifie un attribut qui renvoie une chaîne, *ValuePtr* doit être un pointeur à un tampon dans lequel retourner la chaîne. La longueur maximale de la chaîne, y compris le octet de terminaison nulle, sera les octets *BufferLength.*  
  
 **SQLGetEnvAttr** peut être appelé à tout moment entre l’allocation et la libération d’une poignée d’environnement. Tous les attributs de l’environnement définis avec succès par l’application pour l’environnement persistent jusqu’à ce que **SQLFreeHandle** soit appelé sur le *EnvironmentHandle* avec un *HandleType* de SQL_HANDLE_ENV. Plus d’une poignée d’environnement peut être allouée simultanément dans ODBC 3 *.x*. Un attribut de l’environnement sur un environnement n’est pas affecté lorsqu’un autre environnement a été attribué.  
  
> [!NOTE]
>  L’attribut SQL_ATTR_OUTPUT_NTS environnement est pris en charge par des applications conformes aux normes. Lorsque **SQLGetEnvAttr** est appelé, l’ODBC 3 *.x* Driver Manager retourne toujours SQL_TRUE pour cet attribut. SQL_ATTR_OUTPUT_NTS ne peut être mis à SQL_TRUE que par un appel à **SQLSetEnvAttr**.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Retour du paramètre d’un attribut de connexion|[Fonction SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Retour du paramètre d’un attribut de déclaration|[Fonction SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|Définir un attribut de connexion|[Fonction SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Définir un attribut d’environnement|[Fonction SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|Définir un attribut de déclaration|[Fonction SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)

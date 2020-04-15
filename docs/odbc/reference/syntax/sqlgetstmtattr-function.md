---
title: Fonction SQLGetStmtAttr (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetStmtAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetStmtAttr
helpviewer_keywords:
- SQLGetStmtAttr function [ODBC]
ms.assetid: e321d460-e997-4527-aee6-207cf5a498e9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89e7c75b412a6358806017102915989a8370dd43
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303303"
---
# <a name="sqlgetstmtattr-function"></a>Fonction SQLGetStmtAttr
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLGetStmtAttr** retourne le paramètre actuel d’un attribut d’instruction.  
  
> [!NOTE]  
>  Pour plus d’informations sur ce que le Driver Manager cartographie cette fonction à quand un ODBC 3. *x* application fonctionne avec un ODBC 2. *x* pilote, voir [Mapping Replacement Functions for Backward Compatibility of Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLGetStmtAttr(  
     SQLHSTMT        StatementHandle,  
     SQLINTEGER      Attribute,  
     SQLPOINTER      ValuePtr,  
     SQLINTEGER      BufferLength,  
     SQLINTEGER *    StringLengthPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *StatementHandle (en)*  
 [Entrée] Poignée de déclaration.  
  
 *Attribut*  
 [Entrée] Attribut à récupérer.  
  
 *ValuePtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner la valeur de l’attribut spécifié dans *Attribut*.  
  
 Si *ValuePtr* est NULL, *StringLengthPtr* retournera toujours le nombre total d’octets (à l’exclusion du caractère de résiliation nulle pour les données de caractère) disponible pour revenir dans le tampon indiqué par *ValuePtr*.  
  
 *BufferLength*  
 [Entrée] Si *Attribut* est un attribut défini par ODBC et *que ValuePtr* pointe vers une \*chaîne de caractères ou un tampon binaire, cet argument doit être la longueur de *ValuePtr*. Si *Attribut* est un attribut défini \*par ODBC et *que ValuePtr* est un intégrateur, *BufferLength* est ignoré. Si la valeur retournée dans * \*ValuePtr* est une chaîne Unicode (lorsqu’on appelle **SQLGetStmtAttrW**), l’argument *BufferLength* doit être un nombre pair.  
  
 Si *Attribut* est un attribut défini par le conducteur, l’application indique la nature de l’attribut au gestionnaire de conducteur en définissant l’argument *De bufferLength.* *BufferLength* peut avoir les valeurs suivantes :  
  
-   Si * \*ValuePtr* est un pointeur d’une chaîne de caractères, alors *BufferLength* est la longueur de la chaîne ou SQL_NTS.  
  
-   Si * \*ValuePtr* est un pointeur à un tampon binaire, alors l’application place le résultat de la SQL_LEN_BINARY_ATTR(*longueur)* macro dans *BufferLength*. Cela place une valeur négative dans *BufferLength*.  
  
-   Si * \*ValuePtr* est un pointeur à une valeur autre qu’une chaîne de caractère ou une chaîne binaire, alors *BufferLength* devrait avoir la valeur SQL_IS_POINTER.  
  
-   Si * \*ValuePtr* contient un type de données à durée fixe, *BufferLength* est soit SQL_IS_INTEGER, soit SQL_IS_UINTEGER, le cas échéant.  
  
 *StringLengthPtr*  
 [Sortie] Un pointeur à un tampon dans lequel retourner le nombre total d’octets (à l’exclusion du caractère de résiliation nulle) disponible pour revenir dans * \*ValuePtr*. Si *ValuePtr* est un pointeur nul, aucune longueur n’est retournée. Si la valeur d’attribut est une chaîne de caractère, et le nombre d’octets disponibles pour revenir est supérieur ou égal à *BufferLength*, les données dans * \*ValuePtr* est tronquée à *BufferLength* moins la longueur d’un caractère de non-termination et est annulée par le conducteur.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetStmtAttr** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_STMT et une *poignée* de *StatementHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLGetStmtAttr** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Les données retournées dans * \*ValuePtr* ont été tronquées pour être *BufferLength* moins la longueur d’un caractère de résiliation nulle. La longueur de la valeur de la chaîne fausse est retournée dans*stringLengthPtr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|24 000|État de curseur non valide|L’argument *Attribut* était SQL_ATTR_ROW_NUMBER et le curseur n’était pas ouvert, ou le curseur a été positionné avant le début de l’ensemble de résultat ou après la fin de l’ensemble de résultat.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans l’argument *MessageText* décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour la poignée de connexion qui est associée à la *StatementHandle*. Cette fonction asynchrone était encore en cours d’exécution lorsque la fonction **SQLGetStmtAttr** a été appelée.<br /><br /> (DM) Une fonction d’exécution asynchrone a été appelée pour le *StatementHandle* et était toujours en exécution lorsque cette fonction a été appelée.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, ou **SQLSetPos** a été appelé pour le *StatementHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant que les données ne soient envoyées pour tous les paramètres ou colonnes de données à l’exécution.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|*(DM) \*ValuePtr* est une chaîne de caractères, et BufferLength était moins que zéro, mais pas égal à SQL_NTS.|  
|HY092 HY092|Identification d’attribut/option invalide|La valeur spécifiée pour l’argument *Attribut* n’était pas valide pour la version d’ODBC étayée par le conducteur.|  
|HY109 HY109|Position de curseur invalide|*L’argument d’attribut* était SQL_ATTR_ROW_NUMBER et la rangée avait été supprimée ou ne pouvait pas être récupérée.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|La valeur spécifiée pour l’argument *Attribut* était un attribut valide de déclaration ODBC pour la version d’ODBC soutenue par le conducteur, mais n’a pas été pris en charge par le conducteur.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur correspondant à la *DéclarationHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Pour obtenir des renseignements généraux sur les attributs des relevés, voir [Attributs d’énoncés](../../../odbc/reference/develop-app/statement-attributes.md).  
  
 Un appel à **SQLGetStmtAttr** renvoie dans * \*ValuePtr* la valeur de l’attribut de déclaration spécifié dans *Attribut*. Cette valeur peut être soit une valeur SQLULEN ou une chaîne de caractères à durée nulle. Si la valeur est une valeur SQLULEN, certains conducteurs ne peuvent écrire le moins 32 ou 16 bits d’un tampon et laisser le bit de l’ordre supérieur inchangé. Par conséquent, les applications doivent utiliser un tampon de SQLULEN et initialiser la valeur à 0 avant d’appeler cette fonction. En outre, les arguments *BufferLength* et *StringLengthPtr* ne sont pas utilisés. Si la valeur est une chaîne non terminée, l’application spécifie la longueur maximale de cette chaîne dans l’argument *BufferLength,* et le conducteur retourne la longueur de cette chaîne dans le * \*tampon StringLengthPtr.*  
  
 Permettre aux applications appelant **SQLGetStmtAttr** de travailler avec ODBC 2. *x* conducteurs, un appel à **SQLGetStmtAttr** est cartographié dans le gestionnaire de conducteur à **SQLGetStmtOption**.  
  
 Les attributs de déclaration suivants sont lus uniquement, donc peuvent être récupérés par **SQLGetStmtAttr**, mais pas défini par **SQLSetStmtAttr**:  
  
-   SQL_ATTR_IMP_PARAM_DESC  
  
-   SQL_ATTR_IMP_ROW_DESC  
  
-   SQL_ATTR_ROW_NUMBER  
  
 Pour une liste d’attributs qui peuvent être définis et récupérés, voir [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Retour du paramètre d’un attribut de connexion|[Fonction SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Définir un attribut de connexion|[Fonction SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Définir un attribut de déclaration|[Fonction SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)

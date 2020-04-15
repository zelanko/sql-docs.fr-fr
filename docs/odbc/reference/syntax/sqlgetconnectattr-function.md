---
title: Fonction SQLGetConnectAttr (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectAttr
helpviewer_keywords:
- SQLGetConnectAttr function [ODBC]
ms.assetid: 2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e6076f14ff0c33fec38b99e9c43b8a688970a7a9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285629"
---
# <a name="sqlgetconnectattr-function"></a>Fonction SQLGetConnectAttr
**Conformité**  
 Version introduite: ODBC 3.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLGetConnectAttr** retourne le paramètre actuel d’un attribut de connexion.  
  
> [!NOTE]
>  Pour plus d’informations sur ce que le Gestionnaire de conducteur cartographie cette fonction à quand une application ODBC 3 *.x* travaille avec un pilote ODBC 2 *.x,* voir [Mapping Replacement Functions for Backward Compatibility of Applications](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLGetConnectAttr(  
     SQLHDBC        ConnectionHandle,  
     SQLINTEGER     Attribute,  
     SQLPOINTER     ValuePtr,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *ConnexionHandle*  
 [Entrée] Handle de connexion.  
  
 *Attribut*  
 [Entrée] Attribut à récupérer.  
  
 *ValuePtr*  
 [Sortie] Un pointeur à la mémoire dans lequel retourner la valeur actuelle de l’attribut spécifié par *Attribut*. Pour les attributs de type intégrer, certains conducteurs ne peuvent écrire que le moins bas 32 bits ou 16 bits d’un tampon et laisser le bit de l’ordre supérieur inchangé. Par conséquent, les applications doivent utiliser un tampon de SQLULEN et initialiser la valeur à 0 avant d’appeler cette fonction.  
  
 Si *ValuePtr* est NULL, *StringLengthPtr* retournera toujours le nombre total d’octets (à l’exclusion du caractère de résiliation nulle pour les données de caractère) disponible pour revenir dans le tampon indiqué par *ValuePtr*.  
  
 *BufferLength*  
 [Entrée] Si *Attribut* est un attribut défini par ODBC et *que ValuePtr* pointe vers une \*chaîne de caractères ou un tampon binaire, cet argument doit être la longueur de *ValuePtr*. Si *Attribut* est un attribut défini \*par ODBC et *que ValuePtr* est un intégrateur, *BufferLength* est ignoré. Si la valeur de * \*ValuePtr* est une chaîne Unicode (lorsqu’on appelle **SQLGetConnectAttrW**), l’argument *BufferLength* doit être un nombre pair.  
  
 Si *Attribut* est un attribut défini par le conducteur, l’application indique la nature de l’attribut au gestionnaire de conducteur en définissant l’argument *De bufferLength.* *BufferLength* peut avoir les valeurs suivantes :  
  
-   Si * \*ValuePtr* est un pointeur d’une chaîne de caractères, *BufferLength* est la longueur de la chaîne.  
  
-   Si * \*ValuePtr* est un pointeur vers un tampon binaire, l’application place le résultat de la SQL_LEN_BINARY_ATTR (*longueur)* macro dans *BufferLength*. Cela place une valeur négative dans *BufferLength*.  
  
-   Si * \*ValuePtr* est un pointeur d’une valeur autre qu’une chaîne de caractères ou une chaîne binaire, *BufferLength* devrait avoir la valeur SQL_IS_POINTER.  
  
-   Si * \*ValuePtr* contient un type de données à durée fixe, *BufferLength* est soit SQL_IS_INTEGER, soit SQL_IS_UINTEGER, le cas échéant.  
  
 *StringLengthPtr*  
 [Sortie] Un pointeur à un tampon dans lequel retourner le nombre total d’octets \*(à l’exclusion du caractère de résiliation nulle) disponible pour revenir dans *ValuePtr*. Si \* *ValuePtr* est un pointeur nul, aucune longueur n’est retournée. Si la valeur d’attribut est une chaîne de caractères et que le nombre d’octets disponibles pour revenir est supérieur à *Celui de BufferLength* moins la longueur du caractère de terminaison nulle, les données de * \*ValuePtr* sont tronquées à *BufferLength* moins la longueur du caractère de résiliation nulle et sont annulées par le conducteur.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetConnectAttr** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue à partir de la structure de données diagnostiques en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DBC et une *poignée* de *ConnectionHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLGetConnectAttr** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Les données \*retournées dans *ValuePtr* ont été tronquées pour être *BufferLength* moins la longueur d’un caractère de résiliation nulle. La longueur de la valeur de la chaîne fausse est retournée dans*stringLengthPtr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08003|Connexion non ouverte|(DM) Une valeur *d’attribut* qui nécessitait une connexion ouverte a été spécifiée.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné de la structure de données diagnostiques par l’argument *MessageText* dans **SQLGetDiagField** décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) **SQLBrowseConnect** a été appelé pour le *ConnectionHandle* et retourné SQL_NEED_DATA. Cette fonction a été appelée avant **que SQLBrowseConnect** ne revienne SQL_SUCCESS_WITH_INFO ou SQL_SUCCESS.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *ConnectionHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) * \*ValuePtr* est une chaîne de caractères, et BufferLength était moins que zéro, mais pas égal à SQL_NTS.|  
|HY092 HY092|Identification d’attribut/option invalide|La valeur spécifiée pour l’argument *Attribut* n’était pas valide pour la version d’ODBC étayée par le conducteur.|  
|HY114|Le conducteur ne prend pas en charge l’exécution de fonction asynchrone au niveau de connexion|(DM) Une application a tenté d’activer l’exécution de la fonction asynchrone avec SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE pour un conducteur qui ne prend pas en charge les opérations de connexion asynchrones.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYC00|Fonctionnalité facultative non implémentée|La valeur spécifiée pour l’argument *Attribut* était un attribut de connexion ODBC valide pour la version d’ODBC pris en charge par le conducteur, mais n’était pas pris en charge par le conducteur.|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur qui correspond à la *ConnectionHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Pour plus d’informations générales sur les attributs de connexion, voir [Attributs de connexion](../../../odbc/reference/develop-app/connection-attributes.md).  
  
 Pour une liste d’attributs qui peuvent être définis, voir [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md). Notez que si *Attribute* spécifie un attribut qui renvoie une chaîne, *ValuePtr* doit être un pointeur à un tampon pour la chaîne. La longueur maximale de la chaîne retournée, y compris le caractère de résiliation nulle, sera les octets *BufferLength.*  
  
 Selon l’attribut, une application n’a pas à établir une connexion avant d’appeler **SQLGetConnectAttr**. Toutefois, si **SQLGetConnectAttr** est appelé et que l’attribut spécifié n’a pas de défaut et n’a pas été réglé par un appel antérieur à **SQLSetConnectAttr**, **SQLGetConnectAttr** retournera SQL_NO_DATA.  
  
 Si *l’attribut* est SQL_ATTR_ TRACE ou SQL_ATTR_ TRACEFILE, *ConnectionHandle* n’a pas besoin d’être valide, et **SQLGetConnectAttr** ne retournera pas SQL_ERROR ou SQL_INVALID_HANDLE si *ConnectionHandle* est invalide. Ces attributs s’appliquent à toutes les connexions. **SQLGetConnectAttr** retournera SQL_ERROR ou SQL_INVALID_HANDLE si un autre argument est invalide.  
  
 Bien qu’une application puisse définir des attributs de relevé en utilisant **SQLSetConnectAttr**, une application ne peut pas utiliser **SQLGetConnectAttr** pour récupérer les valeurs d’attributs de déclaration; il doit appeler **SQLGetStmtAttr** pour récupérer le paramètre des attributs de déclaration.  
  
 Les attributs de connexion SQL_ATTR_AUTO_IPD et SQL_ATTR_CONNECTION_DEAD peuvent être retournés par un appel à **SQLGetConnectAttr,** mais ne peuvent pas être fixés par un appel à **SQLSetConnectAttr**.  
  
> [!NOTE]  
>  Il n’y a pas de support asynchrone pour **SQLGetConnectAttr**. Lors de la mise en œuvre **de SQLGetConnectAttr**, un pilote peut améliorer les performances en minimisant le nombre de fois que les informations sont envoyées ou demandées sur le serveur.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Retour du paramètre d’un attribut de déclaration|[Fonction SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|Définir un attribut de connexion|[Fonction SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|Définir un attribut d’environnement|[Fonction SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|Définir un attribut de déclaration|[Fonction SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)

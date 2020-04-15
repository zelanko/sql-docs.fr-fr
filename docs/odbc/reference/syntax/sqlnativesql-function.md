---
title: Fonction SQLNativeSql (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLNativeSql
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLNativeSql
helpviewer_keywords:
- SQLNativeSql function [ODBC]
ms.assetid: b8efc247-27ab-4a00-92b6-1400785783fe
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9666bc767affb3b6bb624c416614079193d4b921
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304720"
---
# <a name="sqlnativesql-function"></a>Fonction SQLNativeSql
**Conformité**  
 Version introduite : ODBC 1.0 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLNativeSql** retourne la chaîne SQL modifiée par le conducteur. **SQLNativeSql** n’exécute pas la déclaration SQL.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLNativeSql(  
     SQLHDBC        ConnectionHandle,  
     SQLCHAR *      InStatementText,  
     SQLINTEGER     TextLength1,  
     SQLCHAR *      OutStatementText,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   TextLength2Ptr);  
```  
  
## <a name="arguments"></a>Arguments  
 *ConnexionHandle*  
 [Entrée] Handle de connexion.  
  
 *InStatementText*  
 [Entrée] Chaîne de texte SQL à traduire.  
  
 *TextLength1 (en)*  
 [Entrée] Longueur dans les caractères de la chaîne de texte*InStatementText.*  
  
 *OutStatementText*  
 [Sortie] Pointeur vers un tampon dans lequel retourner la chaîne SQL traduite.  
  
 Si *OutStatementText* est NULL, *TextLength2Ptr* retournera toujours le nombre total de caractères (à l’exclusion du caractère de non-termination pour les données de caractère) disponibles pour revenir dans le tampon indiqué par *OutStatementText*.  
  
 *BufferLength*  
 [Entrée] Nombre de caractères dans le \*tampon *OutStatementText.* Si la valeur retournée dans * \*InStatementText* est une chaîne Unicode (lorsqu’elle appelle **SQLNativeSqlW**), l’argument *BufferLength* doit être un nombre pair.  
  
 *TextLength2Ptr TextLength2Ptr TextLength2Ptr TextLe*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre total de \*caractères (à l’exclusion de la résiliation nulle) disponibles pour revenir dans *OutStatementText*. Si le nombre de caractères disponibles pour revenir est supérieur ou égal \*à *BufferLength*, la chaîne SQL traduite dans *OutStatementText* est tronquée à *BufferLength* moins la longueur d’un caractère de non-termination.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLNativeSql** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DBC et une *poignée* de *ConnectionHandle*. Le tableau suivant énumère les valeurs SQLSTATE couramment retournées par **SQLNativeSql** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifique au conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|Le \*tampon *OutStatementText* n’était pas assez grand pour retourner toute la chaîne SQL, de sorte que la chaîne SQL a été tronquée. La longueur de la corde SQL fausse est retournée dans*le textlength2Ptr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|08003|Connexion non ouverte|Le *ConnectionHandle* n’était pas dans un état connecté.|  
|08S01|Défaillance du lien de communication|Le lien de communication entre le conducteur et la source de données à laquelle le conducteur était connecté a échoué avant que la fonction ne termine le traitement.|  
|22007|Format de date invalide|**InStatementText* contenait une clause d’évasion avec une date, une heure ou une valeur temporelle non valides.|  
|24 000|État de curseur non valide|Le curseur mentionné dans l’énoncé a été positionné avant le début de l’ensemble de résultats ou après la fin de l’ensemble de résultats. Cette erreur ne peut pas être retournée par un conducteur ayant une implémentation de curseur DBMS indigène.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|Le conducteur n’a pas été en mesure d’allouer la mémoire nécessaire pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY009|Utilisation invalide du pointeur nul|(DM) -*InStatementText* était un pointeur nul.|  
|HY010|Erreur de séquence de fonction|(DM) Une fonction d’exécution asynchrone a été appelée pour le *ConnectionHandle* et était toujours en exécution lorsque cette fonction a été appelée.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) L’argument *TextLength1* était inférieur à 0, mais pas égal à SQL_NTS.|  
|||(DM) L’argument *BufferLength* était inférieur à 0 et l’argument *OutStatementText* n’était pas un pointeur nul.|  
|HY109 HY109|Position de curseur invalide|La rangée actuelle du curseur avait été supprimée ou n’avait pas été récupérée. Cette erreur ne peut pas être retournée par un conducteur ayant une implémentation de curseur DBMS indigène.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01 (HYT01)|Délai de connexion expiré|La période de délai de connexion a expiré avant que la source de données ne réponde à la demande. La période de délai de connexion est définie par **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Le conducteur ne prend pas en charge cette fonction|(DM) Le conducteur associé au *ConnectionHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Voici des exemples de ce que **SQLNativeSql** pourrait revenir pour la chaîne SQL entrée suivante contenant la fonction scalaire CONVERT. Supposons que l’empid colonne est de type INTEGER dans la source de données:  
  
```sql  
SELECT { fn CONVERT (empid, SQL_SMALLINT) } FROM employee  
```  
  
 Un pilote de Microsoft SQL Server peut retourner la chaîne SQL traduite suivante :  
  
```sql  
SELECT convert (smallint, empid) FROM employee  
```  
  
 Un pilote d’ORACLE Server peut retourner la chaîne SQL traduite suivante :  
  
```sql  
SELECT to_number (empid) FROM employee  
```  
  
 Un conducteur d’Ingres peut retourner la chaîne SQL traduite suivante :  
  
```sql  
SELECT int2 (empid) FROM employee  
```  
  
 Pour plus d’informations, voir [Exécution directe](../../../odbc/reference/develop-app/direct-execution-odbc.md) et [exécution préparée](../../../odbc/reference/develop-app/prepared-execution-odbc.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
 Aucun.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)

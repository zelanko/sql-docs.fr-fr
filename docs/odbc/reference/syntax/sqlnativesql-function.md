---
title: Sqlnativesql, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 719b34eef3eb51af1e5eeabce3a88d453f005eff
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68138817"
---
# <a name="sqlnativesql-function"></a>Fonction SQLNativeSql
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : ODBC  
  
 **Résumé**  
 **SQLNativeSql** retourne la chaîne SQL comme modifiée par le pilote. **SQLNativeSql** n’exécute pas l’instruction SQL.  
  
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
 *Handle de connexion*  
 [Entrée] Handle de connexion.  
  
 *InStatementText*  
 [Entrée] Chaîne de texte SQL à traduire.  
  
 *TextLength1*  
 [Entrée] Longueur en caractères de **InStatementText* chaîne de texte.  
  
 *OutStatementText*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner la chaîne SQL traduite.  
  
 Si *OutStatementText* est NULL, *TextLength2Ptr* retournera toujours le nombre total de caractères (sans le caractère de fin de la valeur null pour les données de type caractère) disponibles à renvoyer dans la mémoire tampon vers lequel pointe *OutStatementText*.  
  
 *BufferLength*  
 [Entrée] Nombre de caractères dans le \* *OutStatementText* mémoire tampon. Si la valeur retournée dans  *\*InStatementText* est une chaîne Unicode (lors de l’appel **SQLNativeSqlW**), la *BufferLength* argument doit être un nombre pair.  
  
 *TextLength2Ptr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner le nombre total de caractères (à l’exclusion de caractère nul de terminaison) disponibles à renvoyer dans \* *OutStatementText*. Si le nombre de caractères à retourner est supérieur ou égal à *BufferLength*, la traduit la chaîne SQL dans \* *OutStatementText* est tronqué à  *BufferLength* moins la longueur d’un caractère du caractère nul de terminaison.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLNativeSql** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_DBC et un *gérer* de *ConnectionHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLNativeSql** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|Message d’information spécifiques au pilote. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne droite tronquées|La mémoire tampon \* *OutStatementText* n’est pas suffisamment grande pour retourner la chaîne SQL entière, donc la chaîne SQL a été tronquée. La longueur de la chaîne SQL non tronquée est retournée dans **TextLength2Ptr*. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|08003|Connexion non ouverte|Le *ConnectionHandle* n’était pas dans un état connecté.|  
|08S01|Échec de lien de communication|Échec de la liaison de communication entre le pilote et de la source de données à laquelle le pilote a été connecté avant le traitement de la fonction a été exécutée.|  
|22007|Format datetime non valide|**InStatementText* contenait une clause d’échappement avec une valeur de date, heure ou timestamp non valide.|  
|24000|État de curseur non valide|Le curseur fait référence dans l’instruction a été positionné avant le début du jeu de résultats ou après la fin du jeu de résultats. Cette erreur ne peut pas être retournée par un pilote d’une implémentation de curseur SGBD native.|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le pilote n’a pas pu allouer la mémoire requise pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY009|Utilisation non valide de pointeur null|(DM) **InStatementText* était un pointeur null.|  
|HY010|Erreur de séquence de fonction|(DM) une fonction de façon asynchrone en cours d’exécution a été appelée pour le *ConnectionHandle* et était en cours d’exécution quand cette fonction a été appelée.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|(DM) l’argument *TextLength1* était inférieur à 0, mais pas égale à SQL_NTS.|  
|||(DM) l’argument *BufferLength* était inférieure à 0 et l’argument *OutStatementText* n’était pas un pointeur null.|  
|HY109|Position de curseur non valide|La ligne actuelle du curseur a été supprimée ou n’a pas été extraites. Cette erreur ne peut pas être retournée par un pilote d’une implémentation de curseur SGBD native.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Délai de connexion expiré|Le délai de connexion a expiré avant que la source de données a répondu à la demande. Le délai de connexion est défini via **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Pilote ne prend pas en charge cette fonction|Le pilote (DM) associé le *ConnectionHandle* ne prend pas en charge la fonction.|  
  
## <a name="comments"></a>Commentaires  
 Voici des exemples de ce à quoi **SQLNativeSql** peut retourner pour la chaîne SQL d’entrée suivante contenant la fonction scalaire CONVERT. Supposons que la colonne empid est de type entier dans la source de données :  
  
```sql  
SELECT { fn CONVERT (empid, SQL_SMALLINT) } FROM employee  
```  
  
 Un pilote pour Microsoft SQL Server peut renvoyer la chaîne SQL traduite suivante :  
  
```sql  
SELECT convert (smallint, empid) FROM employee  
```  
  
 Un pilote pour le serveur ORACLE peut retourner la chaîne SQL traduite suivante :  
  
```sql  
SELECT to_number (empid) FROM employee  
```  
  
 Un pilote pour Ingres peut retourner la chaîne SQL traduite suivante :  
  
```sql  
SELECT int2 (empid) FROM employee  
```  
  
 Pour plus d’informations, consultez [l’exécution directe](../../../odbc/reference/develop-app/direct-execution-odbc.md) et [exécution préparée](../../../odbc/reference/develop-app/prepared-execution-odbc.md).  
  
## <a name="related-functions"></a>Fonctions connexes  
 Aucune.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)

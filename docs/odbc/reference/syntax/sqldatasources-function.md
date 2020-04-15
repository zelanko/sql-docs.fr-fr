---
title: Fonction SQLDataSources (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDataSources
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDataSources
helpviewer_keywords:
- SQLDataSources function [ODBC]
ms.assetid: 3f63b1b4-e70e-44cd-96c6-6878d50d0117
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b56a6c25e54897e67beaf39d3b7797ac45391d7b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301179"
---
# <a name="sqldatasources-function"></a>SQLDataSources, fonction
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: ISO 92  
  
 **Résumé**  
 **SQLDataSources** renvoie des informations sur une source de données. Cette fonction n’est mise en œuvre que par le Driver Manager.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLDataSources(  
     SQLHENV          EnvironmentHandle,  
     SQLUSMALLINT     Direction,  
     SQLCHAR *        ServerName,  
     SQLSMALLINT      BufferLength1,  
     SQLSMALLINT *    NameLength1Ptr,  
     SQLCHAR *        Description,  
     SQLSMALLINT      BufferLength2,  
     SQLSMALLINT *    NameLength2Ptr);  
```  
  
## <a name="arguments"></a>Arguments  
 *EnvironnementHandle*  
 [Entrée] Poignée de l’environnement.  
  
 *Sens*  
 [Entrée] Détermine la source de données sur laquelle le gestionnaire de conducteur renvoie des informations. Valeurs possibles :  
  
 SQL_FETCH_NEXT (pour obtenir le nom de source de données suivant dans la liste), SQL_FETCH_FIRST (à aller chercher dès le début de la liste), SQL_FETCH_FIRST_USER (pour aller chercher le premier utilisateur DSN), ou SQL_FETCH_FIRST_SYSTEM (pour aller chercher le premier système DSN).  
  
 Lorsque *la direction* est réglée pour SQL_FETCH_FIRST, les appels ultérieurs à **SQLDataSources** avec *Direction* réglé pour SQL_FETCH_NEXT retourner à la fois les DSN utilisateur et système. Lorsque *Direction* est réglée sur SQL_FETCH_FIRST_USER, tous les appels ultérieurs à **SQLDataSources** avec *Direction* réglé pour SQL_FETCH_NEXT retourner que les DSN utilisateur. Lorsque *la direction* est réglée pour SQL_FETCH_FIRST_SYSTEM, tous les appels ultérieurs à **SQLDataSources** avec *Direction* réglé pour SQL_FETCH_NEXT retourner uniquement les DSN système.  
  
 *Servername*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nom de source de données.  
  
 Si *ServerName* est NULL, *NameLength1Ptr* retournera toujours le nombre total de caractères (à l’exclusion du caractère de non-termination pour les données de caractère) disponibles pour revenir dans le tampon indiqué par *ServerName*.  
  
 *BufferLength1*  
 [Entrée] Longueur du tampon*ServerName,* en caractères; cela n’a pas besoin d’être plus long que SQL_MAX_DSN_LENGTH plus le caractère de résiliation nulle.  
  
 *NomLength1Ptr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre total de caractères \*(à l’exclusion du caractère de résiliation nulle) disponible pour revenir dans *ServerName*. Si le nombre de caractères disponibles pour revenir est supérieur ou égal à *BufferLength1*, le nom de source de données dans \* *ServerName* est tronqué à *BufferLength1* moins la longueur d’un caractère de non-terminaison.  
  
 *Description*  
 [Sortie] Pointeur vers un tampon dans lequel retourner la description du pilote associé à la source de données. Par exemple, dBASE ou SQL Server.  
  
 Si *la description* est NULL, *NameLength2Ptr* retournera toujours le nombre total de caractères (à l’exclusion du caractère de résiliation nulle pour les données de caractère) disponibles pour revenir dans le tampon indiqué par *description*.  
  
 *BufferLength2*  
 [Entrée] Longueur dans les caractères du tampon*de description.*  
  
 *NomLength2Ptr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre total de caractères \*(à l’exclusion du caractère de résiliation nulle) disponibles pour revenir dans *la description*. Si le nombre de caractères disponibles pour revenir est supérieur ou \*égal à *BufferLength2*, la description du pilote dans *Description* est tronquée à *BufferLength2* moins la longueur d’un caractère de résiliation nulle.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLDataSources** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_ENV et une *poignée* *d’EnvironnementHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLDataSources** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|(DM) Message d’information spécifique au gestionnaire de conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|(DM) Le \* *tampon ServerName* n’était pas assez grand pour retourner le nom complet de source de données. Par conséquent, le nom a été tronqué. La longueur de l’ensemble du \*nom de source de données est retournée dans *NameLength1Ptr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)<br /><br /> (DM) La \* *description* de mémoire tampon n’était pas assez grande pour retourner la description complète du conducteur. Par conséquent, la description a été tronquée. La longueur de la description de source de données fausse est retournée dans*nameLength2Ptr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|(DM) Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|(DM) Le gestionnaire de conducteur n’a pas été en mesure d’allouer la mémoire requise pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur spécifiée pour l’argument *BufferLength1* était inférieure à 0.<br /><br /> (DM) La valeur spécifiée pour l’argument *BufferLength2* était inférieure à 0.|  
|HY103|Code de récupération invalide|(DM) La valeur spécifiée pour l’argumenté *De l’orientation* n’était pas égale à SQL_FETCH_FIRST, SQL_FETCH_FIRST_USER, SQL_FETCH_FIRST_SYSTEM ou SQL_FETCH_NEXT.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Commentaires  
 Étant donné que **SQLDataSources** est mis en œuvre dans le gestionnaire de conducteur, il est pris en charge pour tous les conducteurs, indépendamment de la conformité aux normes d’un conducteur particulier.  
  
 Une application peut appeler **SQLDataSources** plusieurs fois pour récupérer tous les noms de source de données. Le gestionnaire de conducteur récupère ces informations à partir des informations du système. Lorsqu’il n’y a plus de noms de source de données, le gestionnaire de conducteur renvoie SQL_NO_DATA. Si **SQLDataSources** est appelé avec SQL_FETCH_NEXT immédiatement après son retour SQL_NO_DATA, il retournera le premier nom de source de données. Pour plus d’informations sur la façon dont une application utilise les informations retournées par **SQLDataSources**, voir [Choisir une source de données ou un pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Si SQL_FETCH_NEXT est transmise à **SQLDataSources** la toute première fois qu’elle est appelée, elle retournera le premier nom de source de données.  
  
 Le conducteur détermine comment les noms des sources de données sont cartographiés selon les sources de données réelles.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Découvrir et énumérer les valeurs requises pour se connecter à une source de données|[Fonction SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Connexion à une source de données|[Fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Connexion à une source de données à l’aide d’une chaîne de connexion ou d’une boîte de dialogue|[Fonction SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Retour des descriptions et attributs des conducteurs|[SQLDrivers, fonction](../../../odbc/reference/syntax/sqldrivers-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)

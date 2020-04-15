---
title: Fonction SQLDrivers (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDrivers
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDrivers
helpviewer_keywords:
- SQLDrivers function [ODBC]
ms.assetid: 6b5b7514-e9cb-4cfd-8b7a-ab51dfab9efa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2496e7cd5f2abe0831c72484bed374d7aa1513ce
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302760"
---
# <a name="sqldrivers-function"></a>SQLDrivers, fonction
**Conformité**  
 Version introduite : ODBC 2.0 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLDrivers** répertorie les descriptions des pilotes et les mots clés d’attribut du conducteur. Cette fonction n’est mise en œuvre que par le Driver Manager.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
SQLRETURN SQLDrivers(  
     SQLHENV         EnvironmentHandle,  
     SQLUSMALLINT    Direction,  
     SQLCHAR *       DriverDescription,  
     SQLSMALLINT     BufferLength1,  
     SQLSMALLINT *   DescriptionLengthPtr,  
     SQLCHAR *       DriverAttributes,  
     SQLSMALLINT     BufferLength2,  
     SQLSMALLINT *   AttributesLengthPtr);  
```  
  
## <a name="arguments"></a>Arguments  
 *EnvironnementHandle*  
 [Entrée] Poignée de l’environnement.  
  
 *Sens*  
 [Entrée] Détermine si le gestionnaire de conducteur récupère la description suivante du conducteur dans la liste (SQL_FETCH_NEXT) ou si la recherche commence dès le début de la liste (SQL_FETCH_FIRST).  
  
 *Déscription de conducteur*  
 [Sortie] Pointeur vers un tampon dans lequel retourner la description du conducteur.  
  
 Si *DriverDescription* est NULL, *DescriptionLengthPtr* retournera toujours le nombre total de caractères (à l’exclusion du caractère de non-termination pour les données de caractère) disponibles pour revenir dans le tampon indiqué par *DriverDescription*.  
  
 *BufferLength1*  
 [Entrée] Longueur du tampon*DriverDescription,* en caractères.  
  
 *DescriptionLengthPtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre total de caractères \*(à l’exclusion du caractère de résiliation nulle) disponible pour revenir dans *DriverDescription*. Si le nombre de caractères disponibles pour revenir est supérieur ou \*égal à *BufferLength1*, la description du pilote dans *DriverDescription* est tronquée à *BufferLength1* moins la longueur d’un caractère de non-termination.  
  
 *ChauffeurAttributes*  
 [Sortie] Pointeur vers un tampon dans lequel retourner la liste des paires de valeur d’attribut du conducteur (voir "Commentaires").  
  
 Si *DriverAttributes* est NULL, *AttributesLengthPtr* retournera toujours le nombre total d’octets (à l’exclusion du caractère de non-termination pour les données de caractère) disponibles pour revenir dans le tampon indiqué par *DriverAttributes*.  
  
 *BufferLength2*  
 [Entrée] Longueur du \*tampon *DriverAttributes,* en caractères. Si la * \*valeur DriverDescription* est une chaîne Unicode (lorsqu’elle appelle **SQLDriversW**), l’argument *BufferLength* doit être un nombre pair.  
  
 *AttributsLengthPtr*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre total d’octets (à l’exclusion du octet de cessation d’emploi nul) disponible pour revenir dans \* *DriverAttributes*. Si le nombre d’octets disponibles pour revenir est supérieur ou égal à \* *BufferLength2*, la liste des paires de valeur d’attribut dans *DriverAttributes* est tronquée à *BufferLength2* moins la longueur du caractère de non-termination.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLDrivers** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_ENV et une *poignée* *d’EnvironnementHandle*. Le tableau suivant énumère les valeurs SQLSTATE généralement retournées par **SQLDrivers** et explique chacune dans le cadre de cette fonction; la notation " (DM)" précède les descriptions des SQLSTATEs retournées par le gestionnaire de conducteur. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|(DM) Message d’information spécifique au gestionnaire de conducteur. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne, droite tronquées|(DM) Le \*tampon *DriverDescription* n’était pas assez grand pour retourner la description complète du conducteur. Par conséquent, la description a été tronquée. La longueur de la description \*complète du conducteur est retournée dans *DescriptionLengthPtr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)<br /><br /> (DM) Le \*tampon *DriverAttributes* n’était pas assez grand pour retourner la liste complète des paires de valeur d’attribut. Par conséquent, la liste a été tronquée. La longueur de la liste mensociée des paires de valeur d’attribut est retournée dans *'AttributesLengthPtr*. (Les retours de fonction SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle il n’y avait pas de SQLSTATE spécifique et pour laquelle aucun SQLSTATE spécifique à la mise en œuvre n’a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le * \** tampon MessageText décrit l’erreur et sa cause.|  
|HY001 (hy001)|Erreur d’allocation de mémoire|(DM) Le gestionnaire de conducteur n’a pas été en mesure d’allouer la mémoire requise pour soutenir l’exécution ou l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *StatementHandle* et retourné SQL_PARAM_DATA_AVAILABLE. Cette fonction a été appelée avant que les données ne soient récupérées pour tous les paramètres en streaming.|  
|HY013|Erreur de gestion de la mémoire|L’appel de fonction n’a pas pu être traité parce que les objets de mémoire sous-jacents n’ont pas pu être consultés, peut-être en raison de conditions de mémoire basse.|  
|HY090 HY090|Longueur invalide de ficelle ou de tampon|(DM) La valeur spécifiée pour l’argument *BufferLength1* était inférieure à 0.<br /><br /> (DM) La valeur spécifiée pour l’argument *BufferLength2* était inférieure à 0 ou égale à 1.|  
|HY103|Code de récupération invalide|(DM) La valeur spécifiée pour l’argumenté *De l’instruction* n’était pas égale à SQL_FETCH_FIRST ou SQL_FETCH_NEXT.|  
|HY117|La connexion est suspendue en raison d’un état de transaction inconnu. Seules les fonctions de déconnexion et de lecture seulement sont autorisées.|(DM) Pour plus d’informations sur l’état suspendu, voir [SQLEndTran Fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Commentaires  
 **SQLDrivers** retourne la description \*du conducteur dans le tampon *DriverDescription.* Il renvoie des informations \*supplémentaires sur le pilote dans le tampon *DriverAttributes* comme une liste de paires de valeur de mots clés. Tous les mots clés indiqués dans les informations du système pour les conducteurs seront retournés pour tous les pilotes, à l’exception **de CreateDSN**, qui est utilisé pour inciter à la création de sources de données et est donc facultatif. Chaque paire est terminée avec un octet nul, et la liste complète est terminée avec un octet nul (c’est-à-dire, deux octets nuls marquent la fin de la liste). Par exemple, un pilote basé sur un fichier utilisant la syntaxe C peut retourner la liste suivante des attributs (« 0 » représente un caractère nul ) :  
  
```  
FileUsage=1\0FileExtns=*.dbf\0\0  
```  
  
 Si \* *DriverAttributes n’est* pas assez grand pour tenir la liste entière, la liste est tronquée, **SQLDrivers** retourne SQLSTATE 01004 (Data tronqué), et la longueur de la liste (à l’exclusion du octet final de non-terminaison) est retournée dans '*AttributsLengthPtr*.  
  
 Les mots clés d’attribut du conducteur sont ajoutés à partir des informations du système lorsque le pilote est installé. Pour plus d’informations, voir [Installer des composants ODBC](../../../odbc/reference/install/installing-odbc-components.md).  
  
 Une application peut appeler **SQLDrivers** plusieurs fois pour récupérer toutes les descriptions du pilote. Le gestionnaire de conducteur récupère ces informations à partir des informations du système. Lorsqu’il n’y a plus de descriptions de conduite, **SQLDrivers** retourne SQL_NO_DATA. Si **SQLDrivers** est appelé avec SQL_FETCH_NEXT immédiatement après son retour SQL_NO_DATA, il renvoie la première description du conducteur. Pour plus d’informations sur la façon dont une application utilise les informations retournées par **SQLDrivers**, voir [Choisir une source de données ou un pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Si SQL_FETCH_NEXT est transmise à **SQLDrivers** la toute première fois qu’elle est appelée, **SQLDrivers** renvoie le premier nom de source de données.  
  
 Étant donné que **SQLDrivers** est mis en œuvre dans le gestionnaire de conducteur, il est pris en charge pour tous les conducteurs, indépendamment de la conformité aux normes d’un conducteur particulier.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Découvrir et énumérer les valeurs requises pour se connecter à une source de données|[Fonction SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Connexion à une source de données|[Fonction SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Noms de source de données de retour|[SQLDataSources, fonction](../../../odbc/reference/syntax/sqldatasources-function.md)|  
|Connexion à une source de données à l’aide d’une chaîne de connexion ou d’une boîte de dialogue|[Fonction SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)

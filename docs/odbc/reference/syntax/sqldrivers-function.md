---
title: Sqldrivers, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bac7f88dcbd9895cfd0d07a5993ab9e38a4608d0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63061897"
---
# <a name="sqldrivers-function"></a>SQLDrivers, fonction
**Conformité**  
 Version introduite : Conformité aux normes 2.0 ODBC : ODBC  
  
 **Résumé**  
 **SQLDrivers** répertorie les descriptions de pilote et les mots clés des attributs pilote. Cette fonction est implémentée uniquement par le Gestionnaire de pilotes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
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
 *EnvironmentHandle*  
 [Entrée] Handle d’environnement.  
  
 *Sens*  
 [Entrée] Détermine si le Gestionnaire de pilotes extrait la description du pilote suivante dans la liste (SQL_FETCH_NEXT) ou si la recherche commence au début de la liste (SQL_FETCH_FIRST).  
  
 *DriverDescription*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner la description du pilote.  
  
 Si *DriverDescription* est NULL, *DescriptionLengthPtr* retournera toujours le nombre total de caractères (sans le caractère de fin de la valeur null pour les données de type caractère) disponibles à renvoyer dans le mémoire tampon vers laquelle pointe *DriverDescription*.  
  
 *BufferLength1*  
 [Entrée] Longueur de la **DriverDescription* mémoire tampon, en caractères.  
  
 *DescriptionLengthPtr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner le nombre total de caractères (sans le caractère de fin de la valeur null) disponibles à renvoyer dans \* *DriverDescription*. Si le nombre de caractères à retourner est supérieur ou égal à *BufferLength1*, la description du pilote dans \* *DriverDescription* est tronqué à  *BufferLength1* moins la longueur d’un caractère du caractère nul de terminaison.  
  
 *DriverAttributes*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner la liste de paires de valeur d’attribut de pilote (voir « Commentaires »).  
  
 Si *DriverAttributes* est NULL, *AttributesLengthPtr* retournera toujours le nombre total d’octets (sans le caractère de fin de la valeur null pour les données de type caractère) disponibles à renvoyer dans la mémoire tampon vers lequel pointe *DriverAttributes*.  
  
 *BufferLength2*  
 [Entrée] Longueur de la \* *DriverAttributes* mémoire tampon, en caractères. Si le  *\*DriverDescription* valeur est une chaîne Unicode (lors de l’appel **SQLDriversW**), la *BufferLength* argument doit être un nombre pair.  
  
 *AttributesLengthPtr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner le nombre total d’octets (à l’exception de l’octet de caractère nul de terminaison) disponibles à renvoyer dans \* *DriverAttributes*. Si le nombre d’octets à retourner est supérieur ou égal à *BufferLength2*, la liste de paires de valeur d’attribut dans \* *DriverAttributes* est tronqué à  *BufferLength2* moins la longueur du caractère de fin de null.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLDrivers** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType* de SQL_HANDLE_ENV et un *gérer* de *EnvironmentHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLDrivers** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|(DM) message d’information du Gestionnaire de pilotes spécifiques. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne droite tronquées|(DM) la mémoire tampon \* *DriverDescription* n’est pas suffisamment grande pour retourner la description complète de pilote. Par conséquent, la description a été tronquée. La longueur de la description complète de pilote est retournée dans \* *DescriptionLengthPtr*. (La fonction retourne SQL_SUCCESS_WITH_INFO.)<br /><br /> (DM) la mémoire tampon \* *DriverAttributes* n’est pas suffisamment grande pour retourner la liste complète des paires de valeur d’attribut. Par conséquent, la liste a été tronquée. La longueur de la liste non tronquée de paires de valeur d’attribut est retournée dans **AttributesLengthPtr*. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|Une erreur s’est produite pour laquelle aucun code SQLSTATE spécifique est survenu et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le Gestionnaire de pilotes (DM) n’a pas pu allouer de la mémoire qui est nécessaire pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *au paramètre StatementHandle* et retourné SQL_PARAM_DATA_ DISPONIBLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|(DM) la valeur spécifiée pour l’argument *BufferLength1* était inférieure à 0.<br /><br /> (DM) la valeur spécifiée pour l’argument *BufferLength2* était inférieur à 0 ou égal à 1.|  
|HY103|Code de récupération non valide|(DM) la valeur spécifiée pour l’argument *Direction* n’était pas égale à SQL_FETCH_FIRST ou SQL_FETCH_NEXT.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Commentaires  
 **SQLDrivers** retourne la description du pilote dans le \* *DriverDescription* mémoire tampon. Il retourne des informations supplémentaires sur le pilote dans le \* *DriverAttributes* mémoire tampon sous forme de liste de paires mot clé-valeur. Tous les mots clés indiqués dans les informations système pour les pilotes sont retournées pour tous les pilotes, à l’exception de **CreateDSN**, qui est utilisé pour demander la création de sources de données et par conséquent est facultatif. Chaque paire se termine par un octet null, et la liste complète se termine par un octet null (autrement dit, deux octets null marquent la fin de la liste). Par exemple, un pilote de fichier à l’aide de la syntaxe C peut retourner la liste d’attributs (« \0 » représente un caractère null) suivante :  
  
```  
FileUsage=1\0FileExtns=*.dbf\0\0  
```  
  
 Si \* *DriverAttributes* est pas suffisamment grande pour contenir l’intégralité de la liste, la liste est tronquée, **SQLDrivers** retourne SQLSTATE 01004 (données tronquées) et la longueur de la liste (à l’exclusion de la dernier octet de caractère nul de terminaison) est retourné dans **AttributesLengthPtr*.  
  
 Mots clés des attributs pilote sont ajoutées à partir des informations système lorsque le pilote est installé. Pour plus d’informations, consultez [installation des composants ODBC](../../../odbc/reference/install/installing-odbc-components.md).  
  
 Une application peut appeler **SQLDrivers** plusieurs fois afin de récupérer toutes les descriptions de pilote. Le Gestionnaire de pilotes récupère ces informations à partir des informations système. Lorsqu’il n’y a aucune plusieurs descriptions de pilote, **SQLDrivers** retourne SQL_NO_DATA. Si **SQLDrivers** est appelée avec SQL_FETCH_NEXT immédiatement après son retour SQL_NO_DATA, elle retourne la première description du pilote. Pour plus d’informations sur la façon dont une application utilise les informations retournées par **SQLDrivers**, consultez [choisir une Source de données ou le pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Si SQL_FETCH_NEXT est passé à **SQLDrivers** la première fois qu’elle est appelée, **SQLDrivers** retourne le premier nom de source de données.  
  
 Étant donné que **SQLDrivers** est implémentée dans le Gestionnaire de pilotes, il est pris en charge pour tous les pilotes indépendamment de la conformité aux normes d’un pilote spécifique.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Découverte et la liste des valeurs requises pour se connecter à une source de données|[SQLBrowseConnect, fonction](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Connexion à une source de données|[SQLConnect, fonction](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Retourner les noms de source de données|[SQLDataSources, fonction](../../../odbc/reference/syntax/sqldatasources-function.md)|  
|Connexion à une source de données à l’aide d’une boîte de dialogue ou de chaîne de connexion|[SQLDriverConnect, fonction](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)

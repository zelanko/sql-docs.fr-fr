---
title: Sqldatasources, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7b04dc2554b820fc6ac8344457754aae984d4b8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63258849"
---
# <a name="sqldatasources-function"></a>SQLDataSources, fonction
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : ISO 92  
  
 **Résumé**  
 **SQLDataSources** renvoie des informations sur une source de données. Cette fonction est implémentée uniquement par le Gestionnaire de pilotes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
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
 *EnvironmentHandle*  
 [Entrée] Handle d’environnement.  
  
 *Sens*  
 [Entrée] Détermine quelle source de données retourne des informations sur le Gestionnaire de pilotes. Valeurs possibles :  
  
 SQL_FETCH_NEXT (pour extraire le nom de source de données suivant dans la liste), SQL_FETCH_FIRST (pour récupérer à partir du début de la liste), SQL_FETCH_FIRST_USER (pour extraire le premier de DSN utilisateur) ou SQL_FETCH_FIRST_SYSTEM (pour extraire le premier système DSN).  
  
 Lorsque *Direction* est défini sur SQL_FETCH_FIRST, les appels suivants à **SQLDataSources** avec *Direction* défini sur SQL_FETCH_NEXT renvoyer les sources de données utilisateur et système. Lorsque *Direction* est défini sur SQL_FETCH_FIRST_USER, tous les appels ultérieurs à **SQLDataSources** avec *Direction* défini sur SQL_FETCH_NEXT retourner uniquement les sources de données utilisateur. Lorsque *Direction* est défini sur SQL_FETCH_FIRST_SYSTEM, tous les appels ultérieurs à **SQLDataSources** avec *Direction* défini sur SQL_FETCH_NEXT retourner uniquement les sources de données système.  
  
 *ServerName*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner le nom de source de données.  
  
 Si *nom_serveur* est NULL, *NameLength1Ptr* retournera toujours le nombre total de caractères (sans le caractère de fin de la valeur null pour les données de type caractère) disponibles à renvoyer dans la mémoire tampon vers laquelle pointée *Nom_serveur*.  
  
 *BufferLength1*  
 [Entrée] Longueur de la **nom_serveur* de la mémoire tampon, en caractères ; il ne doit pas plus long que SQL_MAX_DSN_LENGTH ainsi que le caractère de fin de la valeur null.  
  
 *NameLength1Ptr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner le nombre total de caractères (sans le caractère de fin de la valeur null) disponibles à renvoyer dans \* *nom_serveur*. Si le nombre de caractères à retourner est supérieur ou égal à *BufferLength1*, le nom de source de données dans \* *nom_serveur* est tronqué à *BufferLength1* moins la longueur d’un caractère du caractère nul de terminaison.  
  
 *Description*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner la description du pilote associé à la source de données. Par exemple, dBASE ou SQL Server.  
  
 Si *Description* est NULL, *NameLength2Ptr* retournera toujours le nombre total de caractères (sans le caractère de fin de la valeur null pour les données de type caractère) disponibles à renvoyer dans la mémoire tampon vers laquelle pointée *Description*.  
  
 *BufferLength2*  
 [Entrée] Longueur en caractères de la **Description* mémoire tampon.  
  
 *NameLength2Ptr*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner le nombre total de caractères (sans le caractère de fin de la valeur null) disponibles à renvoyer dans \* *Description*. Si le nombre de caractères à retourner est supérieur ou égal à *BufferLength2*, la description du pilote dans \* *Description* est tronqué à *BufferLength2*  moins la longueur d’un caractère du caractère nul de terminaison.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_ERROR ou SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLDataSources** retourne SQL_ERROR ou SQL_SUCCESS_WITH_INFO, une valeur SQLSTATE associée peut être obtenue en appelant **SQLGetDiagRec** avec un *HandleType*de SQL_HANDLE_ENV et un *gérer* de *EnvironmentHandle*. Le tableau suivant répertorie les valeurs SQLSTATE généralement retournées par **SQLDataSources** et explique chacune dans le contexte de cette fonction ; la notation « (DM) » précède les descriptions de SQLSTATE retournée par le Gestionnaire de pilotes. Le code de retour associé à chaque valeur SQLSTATE est SQL_ERROR, sauf indication contraire.  
  
|SQLSTATE|Error|Description|  
|--------------|-----------|-----------------|  
|01000|Avertissement général|(DM) message d’information du Gestionnaire de pilotes spécifiques. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|01004|Données de chaîne droite tronquées|(DM) la mémoire tampon \* *nom_serveur* n’est pas suffisamment grande pour retourner le nom de source de données complète. Par conséquent, le nom a été tronqué. La longueur du nom de source de données entière est retournée dans \* *NameLength1Ptr*. (La fonction retourne SQL_SUCCESS_WITH_INFO.)<br /><br /> (DM) la mémoire tampon \* *Description* n’est pas suffisamment grande pour retourner la description complète de pilote. Par conséquent, la description a été tronquée. La longueur de la description de source de données non tronqué est retournée dans **NameLength2Ptr*. (La fonction retourne SQL_SUCCESS_WITH_INFO.)|  
|HY000|Erreur générale|(DM) une erreur s’est produite pour lequel il n’a aucun code SQLSTATE spécifique et pour lequel aucune SQLSTATE spécifiques à l’implémentation a été défini. Le message d’erreur retourné par **SQLGetDiagRec** dans le  *\*MessageText* tampon décrit l’erreur et sa cause.|  
|HY001|Erreur d’allocation de mémoire|Le Gestionnaire de pilotes (DM) n’a pas pu allouer de la mémoire qui est nécessaire pour prendre en charge l’exécution ou à l’achèvement de la fonction.|  
|HY010|Erreur de séquence de fonction|(DM) **SQLExecute**, **SQLExecDirect**, ou **SQLMoreResults** a été appelé pour le *au paramètre StatementHandle* et retourné SQL_PARAM_DATA_ DISPONIBLE. Cette fonction a été appelée avant que les données ont été récupérées pour tous les paramètres transmis en continu.|  
|HY013|Erreur de gestion de mémoire|L’appel de fonction n’a pas pu être traité, car les objets sous-jacents de la mémoire ne sont pas accessible, probablement en raison de conditions de mémoire insuffisante.|  
|HY090|Longueur de chaîne ou une mémoire tampon non valide|(DM) la valeur spécifiée pour l’argument *BufferLength1* était inférieure à 0.<br /><br /> (DM) la valeur spécifiée pour l’argument *BufferLength2* était inférieure à 0.|  
|HY103|Code de récupération non valide|(DM) la valeur spécifiée pour l’argument *Direction* n’était pas égale à SQL_FETCH_FIRST, SQL_FETCH_FIRST_USER, SQL_FETCH_FIRST_SYSTEM ou SQL_FETCH_NEXT.|  
|HY117|Connexion est suspendue en raison de l’état de transaction inconnu. Déconnecter uniquement et les fonctions en lecture seule sont autorisées.|(DM) pour plus d’informations sur l’état suspendu, consultez [SQLEndTran, fonction](../../../odbc/reference/syntax/sqlendtran-function.md).|  
  
## <a name="comments"></a>Commentaires  
 Étant donné que **SQLDataSources** est implémentée dans le Gestionnaire de pilotes, il est pris en charge pour tous les pilotes indépendamment de la conformité aux normes d’un pilote spécifique.  
  
 Une application peut appeler **SQLDataSources** plusieurs fois afin de récupérer tous les noms de source de données. Le Gestionnaire de pilotes récupère ces informations à partir des informations système. Lorsqu’il n’y a aucun nom de source de données plus, le Gestionnaire de pilotes retourne SQL_NO_DATA. Si **SQLDataSources** est appelée avec SQL_FETCH_NEXT immédiatement après son retour SQL_NO_DATA, elle retournera le premier nom de source de données. Pour plus d’informations sur la façon dont une application utilise les informations retournées par **SQLDataSources**, consultez [choisir une Source de données ou le pilote](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md).  
  
 Si SQL_FETCH_NEXT est passé à **SQLDataSources** la première fois qu’elle est appelée, elle retourne le premier nom de source de données.  
  
 Le pilote détermine la façon dont les noms de source de données sont mappés à des sources de données réelles.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Découverte et la liste des valeurs requises pour se connecter à une source de données|[SQLBrowseConnect, fonction](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|Connexion à une source de données|[SQLConnect, fonction](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|Connexion à une source de données à l’aide d’une boîte de dialogue ou de chaîne de connexion|[SQLDriverConnect, fonction](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Renvoi de descriptions de pilote et attributs|[SQLDrivers, fonction](../../../odbc/reference/syntax/sqldrivers-function.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)

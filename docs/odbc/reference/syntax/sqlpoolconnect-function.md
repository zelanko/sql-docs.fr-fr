---
title: Sqlpoolconnect, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPoolConnect function [ODBC]
ms.assetid: 41322737-890d-4a81-aed2-06cc3d546962
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4dda69fa741555f4402bded930f68260b154fd30
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63262259"
---
# <a name="sqlpoolconnect-function"></a>SQLPoolConnect, fonction
**Conformité**  
 Version introduite : Conformité aux normes 3,8 ODBC : ODBC  
  
 **Résumé**  
 **SQLPoolConnect** est utilisé pour créer une nouvelle connexion si aucune connexion dans le pool ne peut être réutilisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SQLRETURN  SQLPoolConnect(  
                SQLHDBC              hDbc,  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              wszOutConnectString,  
                SQLSMALLINT          cchConnectStringBuffer,  
                SQLSMALLINT *        cchConnectStringLen );  
```  
  
## <a name="arguments"></a>Arguments  
 *hDbc*  
 [Entrée] Le handle de connexion.  
  
 *hDbcInfoToken*  
 [Entrée] Le handle de jeton pour la nouvelle demande de connexion d’application.  
  
 *wszOutConnectString*  
 [Sortie] Pointeur vers une mémoire tampon pour la chaîne de connexion terminée. Lors de la connexion réussie à la source de données cible, cette mémoire tampon contient la chaîne de connexion terminée. Pour cette mémoire tampon d’applications doivent allouer au moins 1 024 caractères.  
  
 Si *wszOutConnectString* est NULL, *cchConnectStringLen* retournera toujours le nombre total de caractères (sans le caractère de fin de la valeur null pour les données de type caractère) disponibles à renvoyer dans le mémoire tampon vers laquelle pointe *wszOutConnectString*.  
  
 *cchConnectStringBuffer*  
 [Entrée] Longueur de la **wszOutConnectString* mémoire tampon, en caractères.  
  
 *cchConnectStringLen*  
 [Sortie] Pointeur vers une mémoire tampon dans lequel retourner le nombre total de caractères (sans le caractère de fin de la valeur null) disponibles à renvoyer dans \* *wszOutConnectString*. Si le nombre de caractères à retourner est supérieur ou égal à *cchConnectStringBuffer*, la fin de chaîne de connexion dans \* *wszOutConnectString* est tronqué à *cchConnectStringBuffer* moins la longueur d’un caractère du caractère nul de terminaison.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, or, SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Semblable à [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) pour tout d’entrée d’une erreur de validation, à ceci près que le Gestionnaire de pilotes utilisera un **HandleType** de SQL_HANDLE_DBC_INFO_TOKEN et un **gérer** de *hDbcInfoToken*.  
  
## <a name="remarks"></a>Notes  
 Le Gestionnaire de pilotes garantit que le parent HENV gérer de *pas* et *hDbcInfoToken* sont les mêmes.  
  
 Contrairement aux [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md), il existe aucune *DriverCompletion* argument pour inviter les utilisateurs à entrer des informations de connexion. Une boîte de dialogue invite n’est pas autorisée dans le scénario de regroupement.  
  
 Applications ne doivent pas appeler cette fonction directement. Un pilote ODBC qui prend en charge le regroupement de connexions prenant en charge les pilotes doive implémenter cette fonction.  
  
 Chaque fois qu’un pilote retourne SQL_ERROR ou SQL_INVALID_HANDLE, le Gestionnaire de pilotes retourne l’erreur à l’application (dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) ou [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)).  
  
 Chaque fois qu’un pilote retourne SQL_SUCCESS_WITH_INFO, le Gestionnaire de pilotes obtiendront les informations de diagnostic à partir de *hDbcInfoToken*et retourne SQL_SUCCESS_WITH_INFO, à l’application dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)et [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Lorsqu’une application utilise [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md), *wszOutConnectString* sera une mémoire tampon NULL (les trois derniers paramètres sont toutes définies sur NULL, 0, NULL). Sinon, le pilote doit retourner la chaîne de connexion de sortie, qui s’affichera à l’application [fonction SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) appeler.  
  
 Inclure sqlspi.h pour le développement de pilote ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Le regroupement de connexions prenant en charge de pilote](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)

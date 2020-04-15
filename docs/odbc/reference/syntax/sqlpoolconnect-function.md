---
title: Fonction SQLPoolConnect (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5045fe47683529f858b01e69f6af696e2821ca4c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306900"
---
# <a name="sqlpoolconnect-function"></a>SQLPoolConnect, fonction
**Conformité**  
 Version introduite : ODBC 3.8 Standards Compliance: ODBC  
  
 **Résumé**  
 **SQLPoolConnect** est utilisé pour créer une nouvelle connexion si aucune connexion dans la piscine ne peut être réutilisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
  
SQLRETURN  SQLPoolConnect(  
                SQLHDBC              hDbc,  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              wszOutConnectString,  
                SQLSMALLINT          cchConnectStringBuffer,  
                SQLSMALLINT *        cchConnectStringLen );  
```  
  
## <a name="arguments"></a>Arguments  
 *Hdbc*  
 [Entrée] La poignée de connexion.  
  
 *hDbcInfoToken (en anglais seulement)*  
 [Entrée] La poignée de jetons pour la nouvelle demande de connexion d’application.  
  
 *wszOutConnectString (wszOutConnectString)*  
 [Sortie] Pointeur vers un tampon pour la chaîne de connexion terminée. Lors de la connexion réussie à la source de données cible, ce tampon contient la chaîne de connexion terminée. Les demandes doivent allouer au moins 1 024 caractères pour ce tampon.  
  
 Si *wszOutConnectString* est NULL, *cchConnectStringLen* retournera toujours le nombre total de caractères (à l’exclusion du caractère de non-termination pour les données de caractère) disponibles pour revenir dans le tampon indiqué par *wszOutConnectString*.  
  
 *cchConnectStringBuffer*  
 [Entrée] Longueur du tampon*wszOutConnectString,* en caractères.  
  
 *cchConnectStringLen*  
 [Sortie] Pointeur vers un tampon dans lequel retourner le nombre total de caractères \*(à l’exclusion du caractère de non-termination) disponible pour revenir dans *wszOutConnectString*. Si le nombre de caractères disponibles pour revenir est supérieur ou égal à \* *cchConnectStringBuffer*, la chaîne de connexion terminée dans *wszOutConnectString* est tronquée à *cchConnectStringBuffer* moins la longueur d’un caractère de non-termination.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, ou, SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Semblable à [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) pour toute erreur de validation d’entrée, sauf que le gestionnaire de pilote utilisera un **HandleType** de SQL_HANDLE_DBC_INFO_TOKEN et une **poignée** de *hDbcInfoToken*.  
  
## <a name="remarks"></a>Notes  
 Le Driver Manager garantit que la poignée mère HENV de *hDbc* et *hDbcInfoToken* sont les mêmes.  
  
 Contrairement à [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md), il n’y a pas *d’argument De conformité de conducteur* pour inciter les utilisateurs à saisir des informations de connexion. Un dialogue incitant est refusé dans le scénario de mise en commun.  
  
 Les applications ne doivent pas appeler cette fonction directement. Un conducteur ODBC qui prend en charge la mise en commun des connexions consciente du conducteur doit mettre en œuvre cette fonction.  
  
 Chaque fois qu’un pilote retourne SQL_ERROR ou SQL_INVALID_HANDLE, le gestionnaire de pilote renvoie l’erreur à l’application (dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) ou [SQLDriverConnect).](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Chaque fois qu’un pilote retourne SQL_SUCCESS_WITH_INFO, le gestionnaire de conducteur obtiendra les informations diagnostiques de *hDbcInfoToken*, et retournera SQL_SUCCESS_WITH_INFO à l’application dans [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) et [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md).  
  
 Lorsqu’une application utilise [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md), *wszOutConnectString* sera un tampon NULL (les trois derniers paramètres seront tous définis à NULL, 0, NULL). Dans le cas contraire, le pilote doit retourner la chaîne de connexion de sortie, qui sera retournée à l’appel [SQLDriverConnect Function](../../../odbc/reference/syntax/sqldriverconnect-function.md) de l’application.  
  
 Inclure sqlspi.h pour le développement du pilote ODBC.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Mise en commun des connexions conscientes du conducteur](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [Développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)

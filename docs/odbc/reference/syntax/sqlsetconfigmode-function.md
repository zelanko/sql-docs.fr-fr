---
title: Sqlsetconfigmode, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConfigMode
helpviewer_keywords:
- SQLSetConfigMode function [ODBC]
ms.assetid: 09eb88ea-b6f6-4eca-b19d-0951cebc6c0a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b40da961e3e659bf4cd3e3692b4674399bce47a6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537214"
---
# <a name="sqlsetconfigmode-function"></a>SQLSetConfigMode, fonction
**Conformité**  
 Version introduite : ODBC 3.0  
  
 **Résumé**  
 **SQLSetConfigMode** définit le mode de configuration qui indique où l’entrée de fichier Odbc.ini répertoriant les valeurs de la source de données est dans les informations système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>Arguments  
 *wConfigMode*  
 [Entrée] Le mode de configuration du programme d’installation (voir « Commentaires »). La valeur dans *wConfigMode* peut être :  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLSetConfigMode** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Séquence de paramètres non valide|Le *wConfigMode* argument ne contenait pas ODBC_USER_DSN, ODBC_SYSTEM_DSN ou ODBC_BOTH_DSN.|  
  
## <a name="comments"></a>Commentaires  
 Cette fonction est utilisée pour définir où l’entrée de fichier Odbc.ini répertoriant les valeurs de la source de données est dans les informations système. Si *wConfigMode* est ODBC_USER_DSN, la source de données est une source de données utilisateur et la fonction lit à partir de l’entrée de fichier Odbc.ini dans HKEY_CURRENT_USER. Si elle est ODBC_SYSTEM_DSN, la source de données est une source de données système et la fonction lit à partir de l’entrée de fichier Odbc.ini dans HKEY_LOCAL_MACHINE. Si elle est ODBC_BOTH_DSN, HKEY_CURRENT_USER est tentée, et si elle échoue, HKEY_LOCAL_MACHINE est utilisée.  
  
 Cette fonction n’affecte pas **SQLCreateDataSource** et **SQLDriverConnect**. Le mode de configuration doit être définie lorsqu’un pilote lit à partir du Registre en appelant **SQLGetPrivateProfileString** ou écrit dans le Registre en appelant **SQLWritePrivateProfileString**. Les appels à **SQLGetPrivateProfileString** et **SQLWritePrivateProfileString** utiliser le mode de configuration pour savoir quelle partie du Registre à utiliser.  
  
> [!CAUTION]  
>  **SQLSetConfigMode** doit être appelée uniquement lorsque cela est nécessaire ; si le mode est défini correctement, le programme d’installation ODBC peut ne pas fonctionner correctement.  
  
 **SQLSetConfigMode** apporte une modification directe du Registre du mode de configuration. Il s’agit en dehors du processus de modification du mode de configuration par un appel à **SQLConfigDataSource**. Un appel à **SQLConfigDataSource** définit le mode de configuration pour distinguer les sources de données système et utilisateur lorsque vous modifiez une source de données. Avant de retourner, **SQLConfigDataSource** BOTHDSN rétablit le mode de configuration.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Création d’une source de données|[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|Connexion à une source de données à l’aide d’une boîte de dialogue ou de chaîne de connexion|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Récupérer le mode de configuration|[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|

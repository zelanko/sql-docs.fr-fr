---
title: Fonction SQLSetConfigMode (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c36da48fa1493f61131d23a07f7a820b67ebac82
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293279"
---
# <a name="sqlsetconfigmode-function"></a>SQLSetConfigMode, fonction
**Conformité**  
 Version introduite: ODBC 3.0  
  
 **Résumé**  
 **SQLSetConfigMode** définit le mode de configuration qui indique où les valeurs DSN de liste d’entrée Odbc.ini sont dans l’information du système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>Arguments  
 *wConfigMode (en)*  
 [Entrée] Le mode de configuration de l’installateur (voir "Commentaires"). La valeur de *wConfigMode* peut être:  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLSetConfigMode** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Séquence de paramètres invalides|*L’argument de wConfigMode* ne contenait pas de ODBC_USER_DSN, de ODBC_SYSTEM_DSN ou de ODBC_BOTH_DSN.|  
  
## <a name="comments"></a>Commentaires  
 Cette fonction est utilisée pour définir où l’entrée Odbc.ini énumérant les valeurs DSN est dans les informations du système. Si *wConfigMode* est ODBC_USER_DSN, le DSN est un DSN utilisateur et la fonction se lit à partir de l’entrée Odbc.ini dans HKEY_CURRENT_USER. S’il est ODBC_SYSTEM_DSN, le DSN est un DSN système et la fonction se lit à partir de l’entrée Odbc.ini dans HKEY_LOCAL_MACHINE. S’il est ODBC_BOTH_DSN, HKEY_CURRENT_USER est essayé, et si elle échoue, alors HKEY_LOCAL_MACHINE est utilisé.  
  
 Cette fonction n’affecte pas **SQLCreateDataSource** et **SQLDriverConnect**. Le mode de configuration doit être défini lorsqu’un conducteur lit à partir du registre en appelant **SQLGetPrivateProfileString** ou écrit au registre en appelant **SQLWritePrivateProfileString**. Les appels à **SQLGetPrivateProfileString** et **SQLWritePrivateProfileString** utilisent le mode de configuration pour savoir sur quelle partie du registre fonctionner.  
  
> [!CAUTION]  
>  **SQLSetConfigMode** ne doit être appelé que si nécessaire; si le mode est mal défini, l’installateur ODBC peut ne pas fonctionner correctement.  
  
 **SQLSetConfigMode** apporte une modification directe du mode de configuration. Ceci est en dehors du processus de modification du mode de configuration par un appel à **SQLConfigDataSource**. Un appel à **SQLConfigDataSource** définit le mode de configuration pour distinguer les DNS des utilisateurs et du système lors de la modification d’un DSN. Avant de revenir, **SQLConfigDataSource** réinitialise le mode de configuration à BOTHDSN.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Création d’une source de données|[SQLCreateDataSource (en anglais)](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|Connexion à une source de données à l’aide d’une chaîne de connexion ou d’une boîte de dialogue|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Récupération du mode de configuration|[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|

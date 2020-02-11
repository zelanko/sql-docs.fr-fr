---
title: SQLSetConfigMode fonction) | Microsoft Docs
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
ms.openlocfilehash: e2f2bcd3fef2946e5b983c1bbdeee1efe4776512
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68018920"
---
# <a name="sqlsetconfigmode-function"></a>SQLSetConfigMode, fonction
**Conformité**  
 Version introduite : ODBC 3,0  
  
 **Résumé**  
 **SQLSetConfigMode** définit le mode de configuration qui indique où l’entrée ODBC. ini qui répertorie les valeurs DSN se trouve dans les informations système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLSetConfigMode(  
     UWORD     wConfigMode);  
```  
  
## <a name="arguments"></a>Arguments  
 *wConfigMode*  
 Entrée Le mode de configuration du programme d’installation (voir « commentaires »). La valeur de *wConfigMode* peut être :  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Retours  
 La fonction retourne TRUE si elle réussit, FALSe en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Quand **SQLSetConfigMode** retourne false, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie * \** les valeurs pfErrorCode qui peuvent être retournées par **SQLInstallerError** et les explique dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Séquence de paramètres non valide|L’argument *wConfigMode* ne contenait pas ODBC_USER_DSN, ODBC_SYSTEM_DSN ou ODBC_BOTH_DSN.|  
  
## <a name="comments"></a>Commentaires  
 Cette fonction est utilisée pour définir l’emplacement où l’entrée ODBC. ini qui répertorie les valeurs DSN se trouve dans les informations système. Si *wConfigMode* est ODBC_USER_DSN, le DSN est un DSN utilisateur et la fonction lit à partir de l’entrée ODBC. ini dans HKEY_CURRENT_USER. S’il est ODBC_SYSTEM_DSN, le DSN est un DSN système et la fonction lit à partir de l’entrée ODBC. ini dans HKEY_LOCAL_MACHINE. S’il est ODBC_BOTH_DSN, HKEY_CURRENT_USER est essayé et, en cas d’échec, HKEY_LOCAL_MACHINE est utilisé.  
  
 Cette fonction n’affecte pas **SQLCreateDataSource** et **SQLDriverConnect**. Le mode de configuration doit être défini lorsqu’un pilote lit à partir du registre en appelant **SQLGetPrivateProfileString** ou écrit dans le registre en appelant **SQLWritePrivateProfileString**. Les appels à **SQLGetPrivateProfileString** et **SQLWritePrivateProfileString** utilisent le mode de configuration pour savoir quelle partie du Registre utiliser.  
  
> [!CAUTION]  
>  **SQLSetConfigMode** doit être appelé uniquement lorsque cela est nécessaire ; Si le mode n’est pas correctement défini, le programme d’installation ODBC peut ne pas fonctionner correctement.  
  
 **SQLSetConfigMode** effectue une modification directe du Registre du mode de configuration. En dehors du processus de modification du mode de configuration par un appel à **SQLConfigDataSource**. Un appel à **SQLConfigDataSource** définit le mode de configuration pour distinguer les noms DSN utilisateur et système lors de la modification d’un DSN. Avant de retourner, **SQLConfigDataSource** réinitialise le mode de configuration sur BOTHDSN.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Création d’une source de données|[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|  
|Connexion à une source de données à l’aide d’une chaîne de connexion ou d’une boîte de dialogue|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|Récupération du mode de configuration|[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|

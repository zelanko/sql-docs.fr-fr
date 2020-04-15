---
title: Fonction SQLGetConfigMode (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConfigMode
helpviewer_keywords:
- SQLGetConfigMode function [ODBC]
ms.assetid: b96ab3b8-08d5-4fea-9ffe-e03043efbf2d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cc11bec24ede3352dd43f3645fb8c720b77fdabe
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285689"
---
# <a name="sqlgetconfigmode-function"></a>SQLGetConfigMode, fonction
**Conformité**  
 Version introduite: ODBC 3.0  
  
 **Résumé**  
 **SQLGetConfigMode** récupère le mode de configuration qui indique où les valeurs DSN de liste Odbc.ini sont dans l’information du système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>Arguments  
 *pwConfigMode*  
 [Sortie] Pointeur vers le tampon contenant le mode de configuration. (Voir "Commentaires.") La valeur de * \*pwConfigMode* peut être :  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetConfigMode** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 Cette fonction est utilisée pour déterminer où l’entrée Odbc.ini énumérant les valeurs DSN est dans les informations du système. Si * \*pwConfigMode* est ODBC_USER_DSN, le DSN est un DSN utilisateur et la fonction se lit à partir de l’entrée Odbc.ini dans HKEY_CURRENT_USER. S’il est ODBC_SYSTEM_DSN, le DSN est un DSN système et la fonction se lit à partir de l’entrée Odbc.ini dans HKEY_LOCAL_MACHINE. S’il est ODBC_BOTH_DSN, HKEY_CURRENT_USER est essayé, et si elle échoue, HKEY_LOCAL_MACHINE est utilisé.  
  
 Par défaut, **SQLGetConfigMode** revient ODBC_BOTH_DSN. Lorsqu’un DSN utilisateur ou un DSN système est créé par un appel à **SQLConfigDataSource**, la fonction définit le mode de configuration pour ODBC_USER_DSN ou ODBC_SYSTEM_DSN pour distinguer les DNS des utilisateurs et du système tout en modifiant un DSN. Avant de revenir, **SQLConfigDataSource** réinitialise le mode de configuration pour ODBC_BOTH_DSN.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Définition du mode de configuration|[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|

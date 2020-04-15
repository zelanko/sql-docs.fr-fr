---
title: Fonction SQLValidDSN (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLValidDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLValidDSN
helpviewer_keywords:
- SQLValidDSN [ODBC]
ms.assetid: 930d1d89-337a-4429-85a2-84ee10555ac9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6dfafca22d0b04f2147b1af24b53e787493efe67
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286969"
---
# <a name="sqlvaliddsn-function"></a>SQLValidDSN, fonction
**Conformité**  
 Version introduite: ODBC 2.0  
  
 **Résumé**  
 **SQLValidDSN** vérifie la durée et la validité du nom de la source de données avant que le nom ne soit ajouté aux informations du système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLValidDSN(  
     LPCSTR    lpszDSN);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszDSN (LpszDSN)*  
 [Entrée] Nom de source de données à vérifier.  
  
## <a name="returns"></a>Retours  
 La fonction renvoie TRUE si le nom de source de données est valide. Il renvoie FALSE si le nom de source de données est invalide ou si l’appel de fonction a échoué.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLValidDSN** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Un * \*pfErrorCode* n’est retourné que si l’appel de fonction a échoué, pas si FALSE a été retourné parce que le nom de source de données est invalide. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLValidDSN** est appelé par un [conducteur ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) pour vérifier la longueur du nom de la source de données et la validité des caractères individuels dans le nom de source de données. Il vérifie si la longueur du nom est supérieure à SQL_MAX_DSN_LENGTH, tel que défini dans Sqlext.h. (La longueur du nom de la source de données est également vérifiée par [SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md).) **SQLValidDSN** vérifie si l’un des caractères invalides suivants est inclus dans le nom de source de données :  
  
 [ ] { } ( ) , ; ? * = ! \@ \  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’une source de données|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (dans la configuration DLL)|  
|Ajout, modification ou suppression d’une source de données|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Rédaction d’un nom de source de données aux informations du système|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|

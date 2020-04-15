---
title: Fonction SQLRemoveDSNDeIni (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDSNFromIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDSNFromIni
helpviewer_keywords:
- SQLRemoveDSNFromIni function [ODBC]
ms.assetid: bb2e8273-7b61-4113-bfc8-f7ccc607c811
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 848e82741954ab24941d5d519699292727ca25d6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301798"
---
# <a name="sqlremovedsnfromini-function"></a>SQLRemoveDSNFromIni, fonction
**Conformité**  
 Version introduite: ODBC 1.0  
  
 **Résumé**  
 **SQLRemoveDSNFromIni** supprime une source de données de l’information du système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLRemoveDSNFromIni(  
     LPCSTR   lpszDSN);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszDSN (LpszDSN)*  
 [Entrée] Nom de la source de données à supprimer.  
  
## <a name="returns"></a>Retours  
 La fonction renvoie TRUE si elle supprime la source de données ou la source de données n’était pas dans le fichier Odbc.ini. Il renvoie FALSE s’il ne parvient pas à supprimer la source de données.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLRemoveDSNFromIni** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_INVALID_DSN|DSN invalide|*L’argument de lpszDSN* était invalide.|  
|ODBC_ERROR_REQUEST_FAILED|Échec de la demande|L’installateur n’a pas pu retirer les informations DSN du registre.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLRemoveDSNFromIni** supprime le nom de source de données de la section [sources de données de l’ODBC] de l’information du système. Il supprime également la section de spécifications de source de données des informations du système.  
  
 Cette fonction ne doit être appelée que d’une bibliothèque d’installation de pilote.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’une source de données|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Ajout, modification ou suppression d’une source de données|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Suppression de la source de données par défaut|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Ajout d’un nom de source de données aux informations du système|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|

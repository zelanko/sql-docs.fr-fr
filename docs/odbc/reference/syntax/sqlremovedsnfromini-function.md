---
title: Sqlremovedsnfromini, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4cc83a8cafffc9b5d1166df76d91ce4c63f0b858
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68024533"
---
# <a name="sqlremovedsnfromini-function"></a>SQLRemoveDSNFromIni, fonction
**Conformité**  
 Version introduite : ODBC 1.0  
  
 **Résumé**  
 **SQLRemoveDSNFromIni** supprime une source de données à partir des informations système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLRemoveDSNFromIni(  
     LPCSTR   lpszDSN);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszDSN*  
 [Entrée] Nom de la source de données à supprimer.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle supprime la source de données ou la source de données n’était pas dans le fichier Odbc.ini. Elle retourne FALSE si elle ne peut pas supprimer la source de données.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLRemoveDSNFromIni** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_INVALID_DSN|Source de données non valide|Le *lpszDSN* argument n’est pas valide.|  
|ODBC_ERROR_REQUEST_FAILED|Échoué de la demande|Le programme d’installation n’a pas pu supprimer les informations de source de données à partir du Registre.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLRemoveDSNFromIni** supprime le nom de source de données à partir de la section [ODBC Data Sources] des informations système. Elle supprime également la section de spécification de source de données à partir des informations système.  
  
 Cette fonction doit être appelée uniquement à partir d’une bibliothèque de programme d’installation du pilote.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’une source de données|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Ajout, modification ou suppression d’une source de données|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Suppression de la source de données par défaut|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|  
|Ajout d’un nom de source de données pour les informations système|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|

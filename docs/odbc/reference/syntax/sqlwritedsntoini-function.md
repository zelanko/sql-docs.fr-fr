---
title: Sqlwritedsntoini, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLWriteDSNToIni
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWriteDSNToIni
helpviewer_keywords:
- SQLWriteDSNToIni [ODBC]
ms.assetid: dc7018b2-18d4-4657-96d0-086479a47474
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8eece6a1347aa7fba41577f66493e35f92a69d6f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039512"
---
# <a name="sqlwritedsntoini-function"></a>SQLWriteDSNToIni, fonction
**Conformité**  
 Version introduite : ODBC 1.0  
  
 **Résumé**  
 **SQLWriteDSNToIni** ajoute une source de données pour les informations système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLWriteDSNToIni(  
     LPCSTR   lpszDSN,  
     LPCSTR   lpszDriver);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszDSN*  
 [Entrée] Nom de la source de données à ajouter.  
  
 *lpszDriver*  
 [Entrée] Description du pilote (généralement le nom du SGBD associé) présentée aux utilisateurs au lieu du nom de pilote physique.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLWriteDSNToIni** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_INVALID_DSN|Source de données non valide|Le *lpszDSN* argument contenue une chaîne qui n’était pas valide pour une source de données.|  
|ODBC_ERROR_INVALID_NAME|Nom de pilote ou de convertisseur non valide|Le *lpszDriver* argument n’est pas valide.|  
|ODBC_ERROR_REQUEST_FAILED|Échoué de la demande|Le programme d’installation a échoué créer une source de données dans le Registre.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLWriteDSNToIni** ajoute la source de données à la section [ODBC Data Sources] des informations système. Il crée une section de la spécification de la source de données, puis ajoute un mot clé unique (**pilote**) par le nom de la DLL en tant que sa valeur du pilote. Si la section de spécification de source de données existe déjà, **SQLWriteDSNToIni** supprime l’ancienne section avant de créer une nouvelle.  
  
 L’appelant de cette fonction doit ajouter des valeurs et les mots clés spécifiques au pilote à la section de spécification de source de données des informations système.  
  
 Si le nom de la source de données est par défaut, **SQLWriteDSNToIni** crée également la section de spécification de pilote par défaut dans les informations système.  
  
 Cette fonction doit être appelée uniquement à partir d’une DLL d’installation.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’une source de données|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)(dans la DLL d’installation)|  
|Ajout, modification ou suppression d’une source de données|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Suppression d’un nom de source de données à partir des informations système|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|

---
title: Fonction de SQLWriteDSNToIni | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLWriteDSNToIni
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLWriteDSNToIni
helpviewer_keywords: SQLWriteDSNToIni [ODBC]
ms.assetid: dc7018b2-18d4-4657-96d0-086479a47474
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 315ea45ac8f88d482f0b2cf81ed3b9d15b80a7b8
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlwritedsntoini-function"></a>SQLWriteDSNToIni (fonction)
**Mise en conformité**  
 Version introduite : ODBC 1.0  
  
 **Résumé**  
 **SQLWriteDSNToIni** ajoute une source de données pour les informations système.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL SQLWriteDSNToIni(  
     LPCSTR   lpszDSN,  
     LPCSTR   lpszDriver);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszDSN*  
 [Entrée] Nom de la source de données à ajouter.  
  
 *lpszDriver*  
 [Entrée] Description du pilote (généralement le nom du SGBD associé) présentée à l’utilisateur au lieu du nom de pilote physique.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne TRUE si l’opération a réussi, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLWriteDSNToIni** renvoie la valeur FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournées par **SQLInstallerError** et explique chacune d’elles dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générales|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_INVALID_DSN|Source de données non valide|Le *lpszDSN* argument contenue une chaîne qui n’était pas valide pour une source de données.|  
|ODBC_ERROR_INVALID_NAME|Nom de pilote ou de convertisseur non valide|Le *lpszDriver* argument n’était pas valide.|  
|ODBC_ERROR_REQUEST_FAILED|Échoué de la demande|Le programme d’installation a échoué créer une source de données dans le Registre.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLWriteDSNToIni** ajoute la source de données à la section [ODBC Data Sources] des informations système. Il crée une section de la spécification de la source de données et ajoute un mot clé unique (**pilote**) avec le nom de la DLL en tant que valeur du pilote. Si la section de spécification de source de données existe déjà, **SQLWriteDSNToIni** supprime l’ancienne section avant de créer une nouvelle.  
  
 L’appelant de cette fonction doit ajouter des valeurs et les mots clés spécifiques au pilote à la section de spécification de source de données des informations système.  
  
 Si le nom de la source de données est la valeur par défaut, **SQLWriteDSNToIni** crée également la section Spécification du pilote par défaut dans les informations système.  
  
 Cette fonction doit être appelée uniquement à partir d’une DLL d’installation.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’une source de données|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)(dans la DLL d’installation)|  
|Ajout, modification ou suppression d’une source de données|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Suppression d’un nom de source de données à partir des informations système|[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|

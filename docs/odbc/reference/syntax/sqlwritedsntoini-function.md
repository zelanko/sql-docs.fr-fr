---
title: Fonction SQLWriteDSNToIni (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8bb141c8f54c49ca3a5c6fc4bc15d434f91795c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286959"
---
# <a name="sqlwritedsntoini-function"></a>SQLWriteDSNToIni, fonction
**Conformité**  
 Version introduite: ODBC 1.0  
  
 **Résumé**  
 **SQLWriteDSNToIni** ajoute une source de données à l’information du système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLWriteDSNToIni(  
     LPCSTR   lpszDSN,  
     LPCSTR   lpszDriver);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszDSN (LpszDSN)*  
 [Entrée] Nom de la source de données à ajouter.  
  
 *lpszDriver (en)*  
 [Entrée] Description du pilote (généralement le nom du DBMS associé) présentée aux utilisateurs au lieu du nom du conducteur physique.  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLWriteDSNToIni** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_INVALID_DSN|DSN invalide|*L’argument de lpszDSN* contenait une chaîne qui était invalide pour un DSN.|  
|ODBC_ERROR_INVALID_NAME|Nom de conducteur ou traducteur invalide|*L’argument de lpszDriver* était invalide.|  
|ODBC_ERROR_REQUEST_FAILED|Échec de la demande|L’installateur n’a pas réussi à créer un DSN dans le registre.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLWriteDSNToIni** ajoute la source de données à la section [sources de données de l’ODBC] de l’information du système. Il crée ensuite une section de spécification pour la source de données et ajoute un seul mot clé (**Pilote**) avec le nom du pilote DLL comme valeur. Si la section de spécifications de source de données existe déjà, **SQLWriteDSNToIni** supprime l’ancienne section avant de créer la nouvelle.  
  
 L’appelant de cette fonction doit ajouter tous les mots clés et valeurs spécifiques au conducteur à la section de spécifications source de données des informations du système.  
  
 Si le nom de la source de données est par défaut, **SQLWriteDSNToIni** crée également la section de spécification du conducteur par défaut dans les informations du système.  
  
 Cette fonction ne doit être appelée que d’une configuration DLL.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’une source de données|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)(dans la configuration DLL)|  
|Ajout, modification ou suppression d’une source de données|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Suppression d’un nom de source de données des informations du système|[SQLRemoveDSNDeIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|

---
title: Fonction SQLRemoveDriver (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDriver
helpviewer_keywords:
- SQLRemoveDriver function [ODBC]
ms.assetid: 9a3b4f8b-982b-44b9-ade6-754ff026dc90
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 205c5b46e5f6cea195094f7a50e81d7509927d1a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303930"
---
# <a name="sqlremovedriver-function"></a>SQLRemoveDriver, fonction
**Conformité**  
 Version introduite: ODBC 3.0  
  
 **Résumé**  
 **SQLRemoveDriver** modifie ou supprime les informations sur le conducteur de l’entrée Odbcinst.ini dans les informations du système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLRemoveDriver(  
     LPCSTR   lpszDriver,  
     BOOL     fRemoveDSN,  
     LPDWORD  lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszDriver (en)*  
 [Entrée] Le nom du conducteur tel qu’enregistré dans la clé Odbcinst.ini de l’information du système.  
  
 *fRemoveDSN*  
 [Entrée] Les valeurs valides sont les :  
  
 VRAI: Supprimer les DSN associés au conducteur spécifiés dans *lpszDriver*. FALSE: Ne supprimez pas les DSN associés au conducteur spécifié dans *lpszDriver*.  
  
 *lpdwUsageCount (en)*  
 [Sortie] Le nombre d’utilisation du conducteur après que cette fonction a été appelée.  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue. Si aucune entrée n’existe dans les informations du système lorsque cette fonction est appelée, la fonction renvoie FALSE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLRemoveDriver** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Composant non trouvé dans le registre|L’installateur n’a pas pu retirer les renseignements sur le conducteur parce qu’il n’existait pas dans le registre ou qu’il n’y avait pas de documents dans le registre.|  
|ODBC_ERROR_INVALID_NAME|Nom de conducteur ou traducteur invalide|*L’argument de lpszDriver* était invalide.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossible d’incrémenter ou de décroisser le nombre d’utilisation des composants|L’installateur n’a pas réussi à décroisser le nombre d’utilisation du conducteur.|  
|ODBC_ERROR_REQUEST_FAILED|Échec de la demande|*L’argument fRemoveDSN* était VRAI; cependant, un ou plusieurs DSN n’ont pas pu être supprimés. L’appel à **SQLConfigDriver** avec la demande ODBC_REMOVE_DRIVER a échoué.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLRemoveDriver** complète la fonction [SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md) et met à jour le nombre d’utilisation des composants dans les informations du système. Cette fonction ne doit être appelée que d’une application de configuration.  
  
 **SQLRemoveDriver** décrètera la valeur du nombre d’utilisation des composants par 1. Si le nombre d’utilisation des composants passe à 0, ce qui suit se produira :  
  
1.  La fonction **SQLConfigDriver** avec l’option ODBC_REMOVE_DRIVER sera appelée. Si *l’option fRemoveDSN* est définie sur TRUE, la fonction **ConfigDSN** appelle **SQLRemoveDSNFromIni** pour supprimer toutes les sources de données associées au pilote spécifiés dans *lpszDriver.* Si l’option *fRemoveDSN* est définie sur FALSE, les sources de données ne seront pas supprimées.  
  
2.  L’entrée du conducteur dans les informations du système sera supprimée. L’entrée du conducteur se trouve dans l’emplacement d’information du système suivant, sous le nom du conducteur :  
  
     `HKEY_LOCAL_MACHINE`  
  
     `SOFTWARE`  
  
     `ODBC`  
  
     `Odbcinst.ini`  
  
 **SQLRemoveDriver** ne supprime pas réellement les fichiers. Le programme d’appels est responsable de la suppression des fichiers et du maintien du nombre d’utilisation du fichier. Ce n’est qu’après que le nombre d’utilisation des composants et le nombre d’utilisation du fichier ont atteint zéro qu’un fichier a été supprimé physiquement. Certains fichiers d’un composant peuvent être supprimés, et d’autres non supprimés, selon que les fichiers sont utilisés par d’autres applications qui ont incrémenté le nombre d’utilisation du fichier.  
  
 **SQLRemoveDriver** est également appelé dans le cadre d’un processus de mise à niveau. Si une application détecte qu’elle doit effectuer une mise à niveau et qu’elle a déjà installé le conducteur, le conducteur doit être retiré puis réinstallé. **SQLRemoveDriver** devrait d’abord être appelé à décroisser le nombre d’utilisation des composants, puis **SQLInstallDriverEx** devrait être appelé à incrémenter le nombre d’utilisation des composants. Le programme de configuration d’application doit remplacer les anciens fichiers par les nouveaux fichiers. Le nombre d’utilisations de fichiers restera le même, et d’autres applications qui utilisent les fichiers de version plus anciens utiliseront désormais la version la plus récente.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’un conducteur|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md) (dans la configuration DLL)|  
|Ajout, modification ou suppression d’un conducteur|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Installation d’un conducteur|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|

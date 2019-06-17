---
title: Sqlremovedriver, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 274451cdd2d1c3d811e4105a6d646044537999f1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537366"
---
# <a name="sqlremovedriver-function"></a>SQLRemoveDriver, fonction
**Conformité**  
 Version introduite : ODBC 3.0  
  
 **Résumé**  
 **SQLRemoveDriver** modifie ou supprime des informations sur le pilote à partir de l’entrée de fichier Odbcinst.ini dans les informations système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLRemoveDriver(  
     LPCSTR   lpszDriver,  
     BOOL     fRemoveDSN,  
     LPDWORD  lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszDriver*  
 [Entrée] Le nom du pilote comme inscrit dans la clé du fichier Odbcinst.ini des informations système.  
  
 *fRemoveDSN*  
 [Entrée] Les valeurs valides sont :  
  
 TRUE : Supprimer des sources de données associées au pilote spécifié dans *lpszDriver*. FALSE : Ne supprimez pas les sources de données associées au pilote spécifié dans *lpszDriver*.  
  
 *lpdwUsageCount*  
 [Sortie] Le décompte d’utilisation du pilote après que cette fonction a été appelée.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec. Si aucune entrée n’existe dans les informations système lorsque cette fonction est appelée, la fonction retourne FALSE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLRemoveDriver** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Composant introuvable dans le Registre|Le programme d’installation n’a pas pu supprimer les informations de pilote, car il n’existait pas dans le Registre ou est introuvable dans le Registre.|  
|ODBC_ERROR_INVALID_NAME|Nom de pilote ou de convertisseur non valide|Le *lpszDriver* argument n’est pas valide.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossible d’incrémenter ou décrémenter le décompte d’utilisation de composant|Le programme d’installation a échoué décrémenter le décompte d’utilisation du pilote.|  
|ODBC_ERROR_REQUEST_FAILED|Échoué de la demande|Le *fRemoveDSN* argument a la valeur TRUE ; Toutefois, une ou plusieurs sources de données a pas pu être supprimés. L’appel à **SQLConfigDriver** avec la demande ODBC_REMOVE_DRIVER a échoué.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLRemoveDriver** vient compléter la [SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md) (fonction) et les mises à jour le composant décompte d’utilisation dans les informations système. Cette fonction doit être appelée uniquement à partir d’une application d’installation.  
  
 **SQLRemoveDriver** décrémente la valeur du composant utilisation nombre par 1. Si le nombre d’utilisations de composant passe à 0, les éléments suivants se produisent :  
  
1.  Le **SQLConfigDriver** fonction avec l’option ODBC_REMOVE_DRIVER sera appelée. Si le *fRemoveDSN* option est définie sur TRUE, le **ConfigDSN** appels de fonction **SQLRemoveDSNFromIni** pour supprimer toutes les sources de données associées au pilote spécifié dans *lpszDriver.* Si le *fRemoveDSN* option est définie sur FALSE, les sources de données ne seront pas supprimés.  
  
2.  L’entrée de pilote dans les informations système sera supprimée. L’entrée driver est à l’emplacement suivant informations système, sous le nom du pilote :  
  
     `HKEY_LOCAL_MACHINE`  
  
     `SOFTWARE`  
  
     `ODBC`  
  
     `Odbcinst.ini`  
  
 **SQLRemoveDriver** ne supprime pas réellement de tous les fichiers. Le programme appelant est responsable de la suppression de fichiers et de maintenance le décompte d’utilisation de fichier. Uniquement une fois que le nombre d’utilisations de composant et le décompte d’utilisation de fichier ont atteint zéro est un fichier supprimé physiquement. Certains fichiers dans un composant peuvent être supprimés, et d’autres pas été supprimé, selon que les fichiers sont utilisés par d’autres applications qui ont incrémenté le décompte d’utilisation de fichier.  
  
 **SQLRemoveDriver** est également appelé dans le cadre d’un processus de mise à niveau. Si une application détecte qu’il doit effectuer une mise à niveau et il a précédemment installé le pilote, le pilote doit être supprimé et réinstallé. **SQLRemoveDriver** doit tout d’abord être appelé pour décrémenter le décompte d’utilisation de composant, puis **SQLInstallDriverEx** doit être appelé pour incrémenter le décompte d’utilisation de composant. Le programme d’installation d’application doit remplacer les anciens fichiers par les nouveaux fichiers. Le décompte d’utilisation de fichiers restent les mêmes, et autres applications qui utilisent les anciens fichiers de version utilise désormais la version plus récente.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’un pilote|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md) (dans la DLL d’installation)|  
|Ajout, modification ou suppression d’un pilote|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Installation d’un pilote|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|

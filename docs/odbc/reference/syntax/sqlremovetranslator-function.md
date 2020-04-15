---
title: Fonction SQLRemoveTranslator (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveTranslator
helpviewer_keywords:
- SQLRemoveTranslator function [ODBC]
ms.assetid: c6feda49-0359-4224-8de9-77125cf2397b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 348d2c5da0731ba88ccd4dd6406d3754890f7906
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301786"
---
# <a name="sqlremovetranslator-function"></a>SQLRemoveTranslator, fonction
**Conformité**  
 Version introduite: ODBC 3.0  
  
 **Résumé**  
 **SQLRemoveTranslator** supprime les informations concernant un traducteur de la section Odbcinst.ini des informations du système et décrète le nombre d’utilisation des composants du traducteur par 1.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLRemoveTranslator(  
     LPCSTR    lpszTranslator,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszTranslateur*  
 [Entrée] Le nom du traducteur tel qu’enregistré dans la clé Odbcinst.ini de l’information du système.  
  
 *lpdwUsageCount (en)*  
 [Sortie] Le nombre d’utilisation du traducteur après que cette fonction a été appelée.  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue. Si aucune entrée n’existe dans les informations du système lorsque cette fonction est appelée, la fonction renvoie FALSE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLRemoveTranslator** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Composant non trouvé dans le registre|L’installateur n’a pas pu retirer les renseignements du traducteur parce qu’ils n’existaient pas dans le registre ou qu’ils n’étaient pas trouvés dans le registre.|  
|ODBC_ERROR_INVALID_NAME|Nom de conducteur ou traducteur invalide|*L’argument de lpszTranslator* était invalide.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossible d’incrémenter ou de décroisser le nombre d’utilisation des composants|L’installateur n’a pas réussi à décroisser le nombre d’utilisation du conducteur.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLRemoveTranslator** complète la fonction [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md) et met à jour le nombre d’utilisation des composants dans les informations du système. Cette fonction ne doit être appelée que d’une application de configuration.  
  
 **SQLRemoveTranslator** décrédra le nombre d’utilisation des composants par 1. Si le nombre d’utilisation des composants passe à 0, l’entrée du traducteur dans les informations du système sera supprimée. L’entrée du traducteur se trouve à l’emplacement suivant dans les informations du système, sous le nom du traducteur :  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
 **SQLRemoveTranslator** ne supprime pas réellement les fichiers. Le programme d’appels est responsable de la suppression des fichiers et du maintien du nombre d’utilisation du fichier. Ce n’est qu’après que le nombre d’utilisation des composants et le nombre d’utilisation du fichier ont atteint zéro qu’un fichier a été supprimé physiquement. Certains fichiers d’un composant peuvent être supprimés, et d’autres non supprimés, selon que les fichiers sont utilisés par d’autres applications qui ont incrémenté le nombre d’utilisation du fichier.  
  
 **SQLRemoveTranslator** est également appelé dans le cadre d’un processus de mise à niveau. Si une application détecte qu’elle doit effectuer une mise à niveau et qu’elle a déjà installé le conducteur, le conducteur doit être retiré puis réinstallé. **SQLRemoveTranslator** devrait d’abord être appelé à décérer le nombre d’utilisation des composants, puis **SQLInstallTranslatorEx** devrait être appelé à incrémenter le nombre d’utilisation des composants. Le programme de configuration d’application doit remplacer physiquement les anciens fichiers par les nouveaux fichiers. Le nombre d’utilisations de fichiers restera le même, et d’autres applications qui utilisent les fichiers de version plus anciens utiliseront désormais la version la plus récente.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Installation d’un traducteur|[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|

---
title: Fonction SQLRemoveDriverManager (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDriverManager
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDriverManager
helpviewer_keywords:
- SQLRemoveDriverManager function function [ODBC]
ms.assetid: 3a41511f-6603-4b81-a815-7883874023c4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 27b32c1c4e0f3f4d5359af287ba07d40b033af00
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301810"
---
# <a name="sqlremovedrivermanager-function"></a>SQLRemoveDriverManager, fonction
**Conformité**  
 Version introduite: ODBC 3.0: Déprécié dans Windows XP Service Pack 2, Windows Server 2003 Service Pack 1, et plus tard les systèmes d’exploitation.  
  
 **Résumé**  
 **SQLRemoveDriverManager** modifie ou supprime les informations sur les composants de base de l’ODBC de l’entrée Odbcinst.ini dans les informations du système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLRemoveDriverManager(  
     LPDWORD     pdwUsageCount);  
```  
  
## <a name="arguments"></a>Arguments  
 *pdwUsageCompte*  
 [Sortie] Le nombre d’utilisation du Driver Manager après que cette fonction a été appelée.  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue. Si aucune entrée n’existe dans les informations du système lorsque cette fonction est appelée, la fonction renvoie FALSE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLRemoveDriverManager** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Composant non trouvé dans le registre|L’installateur n’a pas pu retirer les renseignements du gestionnaire de conducteur parce qu’ils n’existaient pas dans le registre ou qu’ils n’étaient pas trouvés dans le registre.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossible d’incrémenter ou de décroisser le nombre d’utilisation des composants|L’installateur n’a pas réussi à décroisser le nombre d’utilisation du gestionnaire de conducteur.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLRemoveDriverManager** complète la fonction **SQLInstallDriverManager,** et met à jour le nombre d’utilisation des composants dans les informations du système. Cette fonction ne doit être appelée que d’une application de configuration.  
  
 **SQLRemoveDriverManager** décroissera le nombre d’utilisation des composants de base par 1. Si le nombre d’utilisation des composants passe à 0, les informations du système d’entrée seront supprimées. L’entrée de composant de base se trouve à l’emplacement suivant dans les informations du système, sous le titre « ODBC Core » :  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
> [!CAUTION]  
>  Une application ne doit pas supprimer physiquement les fichiers Driver Manager lorsque l’utilisation des composants compte et que le nombre d’utilisation du fichier atteint zéro.  
  
 **SQLRemoveDriverManager** ne supprime pas réellement les fichiers. Le programme d’appels est responsable de la suppression des fichiers et du maintien des comptes d’utilisation du fichier. Les dossiers de gestionnaire de conducteur ne doivent toutefois pas être supprimés lorsque le nombre d’utilisation des composants et le nombre d’utilisations du fichier ont atteint zéro, car ces fichiers peuvent être utilisés par d’autres applications qui n’ont pas augmenté le nombre d’utilisation du fichier.  
  
 **SQLRemoveDriverManager** est appelé dans le cadre du processus Uninstall. Les composants de base de l’ODBC (qui comprennent le gestionnaire de chauffeur, la bibliothèque de cursor, l’installateur, la bibliothèque linguistique, l’administrateur, les fichiers de chasse, et ainsi de suite) sont non installés dans leur ensemble. Les fichiers suivants ne sont pas supprimés lorsque **SQLRemoveDriverManager** est appelé dans le cadre du processus Uninstall :  
  
|||  
|-|-|  
|ODBC32DLL|ODBCCP32. DLL DLL|  
|ODBCCR32. DLL DLL|ODBC16GT. DLL DLL|  
|ODBCCU32. DLL DLL|ODBC32GT. DLL DLL|  
|ODBCINT. DLL DLL|DS16GT. DLL DLL|  
|ODBCTRAC. DLL DLL|DS32GT. DLL DLL|  
|MSVCRT40. DLL DLL|ODBCAD32. EXE (EXE)|  
|ODBCCP32. Cpl||  
  
 **SQLRemoveDriverManager** est également appelé dans le cadre d’un processus de mise à niveau. Si une application détecte qu’elle doit effectuer une mise à niveau et qu’elle a déjà installé le conducteur, le conducteur doit être retiré puis réinstallé.  
  
 **SQLRemoveDriverManager** devrait d’abord être appelé à décroisser le nombre d’utilisation des composants. **SQLInstallDriverEx** devrait alors être appelé pour incrémenter le nombre d’utilisation des composants. Le programme de configuration d’application doit remplacer les anciens fichiers de composants de base par les nouveaux fichiers. Le nombre d’utilisations de fichiers restera le même, et d’autres applications qui utilisent les fichiers de composants de base de version ancienne utiliseront désormais les fichiers de version plus récents.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Installation d’un gestionnaire de conducteur|[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|

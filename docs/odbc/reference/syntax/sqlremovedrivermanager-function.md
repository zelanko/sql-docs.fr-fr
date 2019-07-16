---
title: Sqlremovedrivermanager, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5cd31a45ed891a8dc95f4f23981d4b626a6095b6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68024540"
---
# <a name="sqlremovedrivermanager-function"></a>SQLRemoveDriverManager, fonction
**Conformité**  
 Version introduite : ODBC 3.0 : Déconseillées dans Windows XP Service Pack 2, Windows Server 2003 Service Pack 1 et des systèmes d’exploitation ultérieurs.  
  
 **Résumé**  
 **SQLRemoveDriverManager** modifie ou supprime les informations sur les composants principaux ODBC à partir de l’entrée de fichier Odbcinst.ini dans les informations système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLRemoveDriverManager(  
     LPDWORD     pdwUsageCount);  
```  
  
## <a name="arguments"></a>Arguments  
 *pdwUsageCount*  
 [Sortie] Le décompte d’utilisation du Gestionnaire de pilotes une fois que cette fonction a été appelée.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec. Si aucune entrée n’existe dans les informations système lorsque cette fonction est appelée, la fonction retourne FALSE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLRemoveDriverManager** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Composant introuvable dans le Registre|Le programme d’installation n’a pas pu supprimer les informations du Gestionnaire de pilotes, car il n’existait pas dans le Registre ou est introuvable dans le Registre.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossible d’incrémenter ou décrémenter le décompte d’utilisation de composant|Le programme d’installation a échoué décrémenter le décompte d’utilisation du Gestionnaire de pilotes.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLRemoveDriverManager** vient compléter la **SQLInstallDriverManager** (fonction) et les mises à jour le composant décompte d’utilisation dans les informations système. Cette fonction doit être appelée uniquement à partir d’une application d’installation.  
  
 **SQLRemoveDriverManager** décrémente le décompte d’utilisation de composant core par 1. Si le nombre d’utilisations de composant passe à 0, les informations de système d’entrée seront supprimées. L’entrée de composant principal est à l’emplacement suivant dans les informations système, sous le titre « ODBC Core » :  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
> [!CAUTION]  
>  Une application physiquement ne supprimez pas les fichiers de gestionnaire de pilotes lorsque le nombre d’utilisations de composant et le décompte d’utilisation de fichier atteint zéro.  
  
 **SQLRemoveDriverManager** ne supprime pas réellement de tous les fichiers. Le programme appelant est responsable de la suppression de fichiers et maintenir l’utilisation du fichier de compte. Fichiers du Gestionnaire de pilotes ne doit pas, toutefois, être supprimé lorsque le nombre d’utilisations de composant et le décompte d’utilisation de fichier ont atteint zéro, car ces fichiers peuvent être utilisés par d’autres applications qui n’ont pas incrémenté le décompte d’utilisation de fichier.  
  
 **SQLRemoveDriverManager** est appelé dans le cadre du processus de désinstallation. Les composants principaux ODBC (qui incluent le Gestionnaire de pilotes, bibliothèque de curseurs, programme d’installation, langue bibliothèque, administrateur, fichiers thunking et ainsi de suite) sont désinstallés dans sa globalité. Les fichiers suivants ne sont pas supprimés lorsque **SQLRemoveDriverManager** est appelé dans le cadre du processus de désinstallation :  
  
|||  
|-|-|  
|ODBC32DLL|ODBCCP32. DLL|  
|ODBCCR32. DLL|ODBC16GT.DLL|  
|ODBCCU32. DLL|ODBC32GT.DLL|  
|ODBCINT. DLL|DS16GT. DLL|  
|ODBCTRAC. DLL|DS32GT. DLL|  
|MSVCRT40. DLL|ODBCAD32.EXE|  
|ODBCCP32.CPL||  
  
 **SQLRemoveDriverManager** est également appelé dans le cadre d’un processus de mise à niveau. Si une application détecte qu’il doit effectuer une mise à niveau et il a précédemment installé le pilote, le pilote doit être supprimé et réinstallé.  
  
 **SQLRemoveDriverManager** doit tout d’abord être appelé pour décrémenter le décompte d’utilisation de composant. **SQLInstallDriverEx** doit être appelé pour incrémenter le décompte d’utilisation de composant. Le programme d’installation d’application doit remplacer les anciens fichiers de composant core avec les nouveaux fichiers. Le nombre de l’utilisation de fichiers restent les mêmes, et autres applications qui utilisent les anciens fichiers de composant core version utilise désormais les fichiers de version plus récente.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|L’installation d’un gestionnaire de pilotes|[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|

---
title: Sqlremovetranslator, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bf81d013ccf449288791b1875752d5b6067770a1
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53207598"
---
# <a name="sqlremovetranslator-function"></a>SQLRemoveTranslator, fonction
**Conformité**  
 Version introduite : ODBC 3.0  
  
 **Résumé**  
 **SQLRemoveTranslator** supprime les informations relatives à un traducteur à partir de la section du fichier Odbcinst.ini des informations système et décrémente décompte d’utilisation du composant de conversion par 1.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL SQLRemoveTranslator(  
     LPCSTR    lpszTranslator,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszTranslator*  
 [Entrée] Le nom du traducteur comme inscrit dans la clé du fichier Odbcinst.ini des informations système.  
  
 *lpdwUsageCount*  
 [Sortie] Le nombre d’utilisations du traducteur après avoir appelé cette fonction.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec. Si aucune entrée n’existe dans les informations système lorsque cette fonction est appelée, la fonction retourne FALSE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLRemoveTranslator** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Composant introuvable dans le Registre|Le programme d’installation n’a pas pu supprimer les informations de translator, car il n’existait pas dans le Registre ou est introuvable dans le Registre.|  
|ODBC_ERROR_INVALID_NAME|Nom de pilote ou de convertisseur non valide|Le *lpszTranslator* argument n’est pas valide.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossible d’incrémenter ou décrémenter le décompte d’utilisation de composant|Le programme d’installation a échoué décrémenter le décompte d’utilisation du pilote.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLRemoveTranslator** vient compléter la [SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md) (fonction) et les mises à jour le composant décompte d’utilisation dans les informations système. Cette fonction doit être appelée uniquement à partir d’une application d’installation.  
  
 **SQLRemoveTranslator** décrémente le décompte d’utilisation de composant par 1. Si le nombre d’utilisations de composant passe à 0, l’entrée de translator dans les informations système sera supprimée. L’entrée de convertisseur est à l’emplacement suivant dans les informations système, sous le nom du traducteur :  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
 **SQLRemoveTranslator** ne supprime pas réellement de tous les fichiers. Le programme appelant est responsable de la suppression de fichiers et de la gestion le décompte d’utilisation de fichier. Uniquement une fois que le nombre d’utilisations de composant et le décompte d’utilisation de fichier ont atteint zéro est un fichier supprimé physiquement. Certains fichiers dans un composant peuvent être supprimés, et d’autres pas été supprimé, selon que les fichiers sont utilisés par d’autres applications qui ont incrémenté le décompte d’utilisation de fichier.  
  
 **SQLRemoveTranslator** est également appelé dans le cadre d’un processus de mise à niveau. Si une application détecte qu’il doit effectuer une mise à niveau et il a précédemment installé le pilote, le pilote doit être supprimé et réinstallé. **SQLRemoveTranslator** doit tout d’abord être appelé pour décrémenter le décompte d’utilisation de composant, puis **SQLInstallTranslatorEx** doit être appelé pour incrémenter le décompte d’utilisation de composant. Le programme d’installation d’application devez physiquement remplacer les anciens fichiers par les nouveaux fichiers. Le décompte d’utilisation de fichiers restent les mêmes, et autres applications qui utilisent les anciens fichiers de version utilise désormais la version plus récente.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|L’installation d’un traducteur|[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|

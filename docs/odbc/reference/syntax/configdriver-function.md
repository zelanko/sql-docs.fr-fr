---
title: Fonction ConfigDriver (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- ConfigDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigDriver
helpviewer_keywords:
- ConfigDriver [ODBC]
ms.assetid: 9473f48f-bcae-4784-89c1-7839bad4ed13
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6a2da5fd5ce01bd97f13d7c8d805c615c1ac436a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303960"
---
# <a name="configdriver-function"></a>ConfigDriver, fonction
**Conformité**  
 Version introduite: ODBC 2.5  
  
 **Résumé**  
 **ConfigDriver** permet à un programme d’installation d’effectuer des fonctions d’installation et de désinstallation sans exiger du programme qu’il appelle **ConfigDSN**. Cette fonction effectuera des fonctions spécifiques au conducteur telles que la création d’informations système spécifiques au conducteur et l’exécution des conversions DSN pendant l’installation, ainsi que le nettoyage des modifications d’informations du système pendant le désinstallation. Cette fonction est exposée par la configuration du pilote DLL ou une configuration séparée DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL ConfigDriver(  
      HWND    hwndParent,  
      WORD    fRequest,  
      LPCSTR  lpszDriver,  
      LPCSTR  lpszArgs,  
      LPSTR   lpszMsg,  
      WORD    cbMsgMax,  
      WORD *  pcbMsgOut);  
```  
  
## <a name="arguments"></a>Arguments  
 *hwndParent*  
 [Entrée] Poignée de fenêtre de parent. La fonction n’affichera pas de boîtes de dialogue si la poignée est nulle.  
  
 *fRequest*  
 [Entrée] Type de demande. *L’argument de fRequest* doit contenir l’une des valeurs suivantes :  
  
 ODBC_INSTALL_DRIVER: Installer un nouveau pilote.  
  
 ODBC_REMOVE_DRIVER : Retirez un conducteur.  
  
 Cette option peut également être spécifique au conducteur, auquel cas *l’argument de* la première option doit commencer à partir de ODBC_CONFIG_DRIVER_MAX 1. *L’argument de fRequest* pour toute option supplémentaire doit également commencer à partir d’une valeur supérieure à ODBC_CONFIG_DRIVER_MAX 1.  
  
 *lpszDriver (en)*  
 [Entrée] Le nom du conducteur tel qu’enregistré dans la clé Odbcinst.ini de l’information du système.  
  
 *lpszArgs*  
 [Entrée] Une chaîne à durée nulle contenant des arguments en faveur d’une *fRequest*spécifique au conducteur.  
  
 *lpszMsg*  
 [Sortie] Une chaîne non terminée contenant un message de sortie de la configuration du conducteur.  
  
 *cbMsgMax (en)*  
 [Entrée] Longueur de *lpszMsg*.  
  
 *pcbMsgOut*  
 [Sortie] Nombre total d’octets disponibles pour revenir en *lpszMsg*.  
  
 Si le nombre d’octets disponibles pour revenir est supérieur ou égal à *cbMsgMax*, le message de sortie dans *lpszMsg* est tronqué à *cbMsgMax* moins le caractère de non-termination. *L’argument pcbMsgOut* peut être un pointeur nul.  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **ConfigDriver** retourne FALSE, une valeur * \*pfErrorCode* associée est affichée sur le tampon d’erreur de l’installateur par un appel à **SQLPostInstallerError** et peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Poignée de fenêtre invalide|*L’argument de hwndParent* était invalide.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Type invalide de demande|*L’argument de fRequest* n’était pas l’un des suivants :<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> L’option spécifique au conducteur était inférieure ou égale à ODBC_CONFIG_DRIVER_MAX.|  
|ODBC_ERROR_INVALID_NAME|Nom de conducteur ou traducteur invalide|*L’argument de lpszDriver* était invalide. Il n’a pas été trouvé dans le registre.|  
|ODBC_ERROR_REQUEST_FAILED|*Demande* a échoué|Impossible d’effectuer l’opération demandée par l’argument *de fRequest.*|  
|ODBC_ERROR_DRIVER_SPECIFIC|Erreur spécifique au conducteur ou au traducteur|Une erreur spécifique au conducteur pour laquelle il n’y a pas d’erreur d’installateur ODBC définie. *L’argument de SzError* dans un appel à la fonction **SQLPostInstallerError** devrait contenir le message d’erreur spécifique au conducteur.|  
  
## <a name="comments"></a>Commentaires  
  
### <a name="driver-specific-options"></a>Options spécifiques au conducteur  
 Une application peut demander des fonctionnalités spécifiques au conducteur exposées par le conducteur en utilisant l’argument *fRequest.* Le *fRequest* pour la première option sera ODBC_CONFIG_DRIVER_MAX plus 1, et des options supplémentaires seront incrémentées par 1 de cette valeur. Tous les arguments requis par le conducteur pour cette fonction doivent être fournis dans une chaîne non terminée adoptée dans *l’argument lpszArgs.* Les conducteurs qui fournissent de telles fonctionnalités doivent maintenir un tableau d’options spécifiques au conducteur. Les options doivent être entièrement documentées dans la documentation du conducteur. Les rédacteurs d’applications qui utilisent des options spécifiques au conducteur doivent savoir que cela rendra l’application moins interopérable.  
  
### <a name="messages"></a>Messages  
 Une routine de configuration du pilote peut envoyer un message texte à une application comme une chaîne annulée dans le tampon *lpszMsg.* Le message sera tronqué à *cbMsgMax* moins le caractère de non-termination par la fonction **ConfigDriver** s’il est supérieur ou égal aux *caractères cbMsgMax.*

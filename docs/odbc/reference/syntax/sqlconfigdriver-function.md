---
title: Fonction SQLConfigDriver (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLConfigDriver
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConfigDriver
helpviewer_keywords:
- SQLConfigDriver function [ODBC]
ms.assetid: 4f681961-ac9f-4d88-b065-5258ba112642
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0da15cef06e5d8392408108ce88b53f7885eb65e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301244"
---
# <a name="sqlconfigdriver-function"></a>SQLConfigDriver, fonction
**Conformité**  
 Version introduite: ODBC 2.5  
  
 **Résumé**  
 **SQLConfigDriver** charge la configuration appropriée du conducteur DLL et appelle la fonction **ConfigDriver.**  
  
 La fonctionnalité de **SQLConfigDriver** peut également être consultée avec [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLConfigDriver(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszArgs,  
     LPSTR    lpszMsg,  
     WORD     cbMsgMax,  
     WORD *   pcbMsgOut);  
```  
  
## <a name="arguments"></a>Arguments  
 *hwndParent*  
 [Entrée] Poignée de fenêtre de parent. La fonction n’affichera pas de boîtes de dialogue si la poignée est nulle.  
  
 *fRequest*  
 [Entrée] Type de demande. *fRequest* doit contenir l’une des valeurs suivantes :  
  
 ODBC_CONFIG_DRIVER : Modifie le délai de mise en commun des connexions utilisé par le conducteur.  
  
 ODBC_INSTALL_DRIVER: Installe un nouveau pilote.  
  
 ODBC_REMOVE_DRIVER : Supprime un conducteur existant.  
  
 Cette option peut également être spécifique au conducteur, auquel cas la *fRequest* pour la première option doit commencer à partir de ODBC_CONFIG_DRIVER_MAX 1. Le *fRequest* pour toute option supplémentaire doit également commencer à partir d’une valeur supérieure à ODBC_CONFIG_DRIVER_MAX 1.  
  
 *lpszDriver (en)*  
 [Entrée] Le nom du conducteur tel qu’enregistré dans les informations du système.  
  
 *lpszArgs*  
 [Entrée] Une chaîne à durée nulle qui contient des arguments en faveur d’une *fRequest*spécifique au conducteur.  
  
 *lpszMsg*  
 [Sortie] Une chaîne non terminée qui contient un message de sortie de la configuration du pilote.  
  
 *cbMsgMax (en)*  
 [Entrée] Longueur de *lpszMsg.*  
  
 *pcbMsgOut*  
 [Sortie] Nombre total d’octets disponibles pour revenir en *lpszMsg*. Si le nombre d’octets disponibles pour revenir est supérieur ou égal à *cbMsgMax*, le message de sortie dans *lpszMsg* est tronqué à *cbMsgMax* moins le caractère de non-termination. *L’argument pcbMsgOut* peut être un pointeur nul.  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLConfigDriver** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longueur tampon invalide|*L’argument de lpszMsg* était invalide.|  
|ODBC_ERROR_INVALID_HWND|Poignée de fenêtre invalide|*L’argument de hwndParent* était invalide.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Type invalide de demande|*L’argument de fRequest* n’était pas l’un des suivants :<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> *L’argument de fRequest* était une option spécifique au conducteur qui était inférieure ou égale à ODBC_CONFIG_DRIVER_MAX.|  
|ODBC_ERROR_INVALID_NAME|Nom de conducteur ou traducteur invalide|*L’argument de lpszDriver* était invalide. Il n’a pas été trouvé dans le registre.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Paires de mots clés invalides|*L’argument lpszArgs* contenait une erreur de syntaxe.|  
|ODBC_ERROR_REQUEST_FAILED|*Demande* a échoué|L’installateur n’a pas pu effectuer l’opération demandée par l’argument *de la fRequest.* L’appel à **ConfigDriver** a échoué.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Impossible de charger le conducteur ou la bibliothèque d’installation de traducteur|La bibliothèque d’installation du conducteur n’a pas pu être chargée.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLConfigDriver** permet à une application d’appeler la routine **ConfigDriver** d’un conducteur sans avoir à connaître le nom et charger la configuration DLL spécifique au conducteur. Un programme de configuration appelle cette fonction après l’installation du pilote DLL a été installé. Le programme d’appels doit être conscient que cette fonction pourrait ne pas être disponible pour tous les conducteurs. Dans un tel cas, le programme d’appels devrait se poursuivre sans erreur.  
  
## <a name="driver-specific-options"></a>Options spécifiques au conducteur  
 Une application peut demander des fonctionnalités spécifiques au conducteur exposées par le conducteur en utilisant l’argument *fRequest.* Le *fRequest* pour la première option sera ODBC_CONFIG_DRIVER_MAX 1, et les options supplémentaires seront incrémentées par 1 à partir de cette valeur. Tous les arguments requis par le conducteur pour cette fonction doivent être fournis dans une chaîne non terminée adoptée dans *l’argument lpszArgs.* Les conducteurs qui fournissent de telles fonctionnalités doivent maintenir un tableau d’options spécifiques au conducteur. Les options doivent être entièrement documentées dans la documentation du conducteur. Les rédacteurs d’applications qui utilisent des options spécifiques au conducteur doivent savoir que cette utilisation rendra l’application moins interopérable.  
  
## <a name="setting-connection-pooling-timeout"></a>Définir le délai de mise en commun de connexion  
 Les propriétés de temps d’arrêt de mise en commun de connexion peuvent être définies lorsque vous définissez la configuration du pilote. **SQLConfigDriver** est appelé avec un *fRequest* de ODBC_CONFIG_DRIVER et *lpszArgs* réglés sur **CPTimeout**. **CPTimeout** détermine la période pendant laquelle une connexion peut rester dans le pool de connexion sans être utilisée. Lorsque le délai d’expiration expire, la connexion est fermée et retirée de la piscine. Le délai d’attente par défaut est de 60 secondes.  
  
 Lorsque **SQLConfigDriver** est appelé avec *fRequest* réglé pour ODBC_INSTALL_DRIVER ou ODBC_REMOVE_DRIVER, le gestionnaire de conducteur charge la configuration du conducteur approprié DLL et appelle la fonction **ConfigDriver.** Lorsque **SQLConfigDriver** est appelé avec un *fRequest* de ODBC_CONFIG_DRIVER, tout le traitement est effectué dans l’installateur ODBC, de sorte que la configuration du conducteur DLL n’a pas à être chargé.  
  
## <a name="messages"></a>Messages  
 Une routine de configuration du pilote peut envoyer un message texte à une application sous forme de chaînes non terminées dans le tampon *lpszMsg.* Le message sera tronqué à *cbMsgMax* moins le caractère de non-termination par la fonction **ConfigDriver** s’il est supérieur ou égal aux *caractères cbMsgMax.*  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’un conducteur|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)(dans la configuration DLL)|  
|Suppression de la source de données par défaut|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|

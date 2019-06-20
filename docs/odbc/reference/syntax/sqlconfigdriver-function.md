---
title: Sqlconfigdriver, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 20316f2a7932768951633ae24e1b1e180c1dfb49
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537578"
---
# <a name="sqlconfigdriver-function"></a>SQLConfigDriver, fonction
**Conformité**  
 Version introduite : ODBC 2.5  
  
 **Résumé**  
 **SQLConfigDriver** charge la DLL d’installation du pilote approprié et appelle le **ConfigDriver** (fonction).  
  
 La fonctionnalité de **SQLConfigDriver** est également accessible avec [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
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
 [Entrée] Handle de fenêtre parente. La fonction n’affichera pas les boîtes de dialogue si le handle est null.  
  
 *fRequest*  
 [Entrée] Type de requête. *fréquents* doit contenir l’une des valeurs suivantes :  
  
 ODBC_CONFIG_DRIVER : Modifie la délai d’expiration utilisé par le pilote de regroupement de connexions.  
  
 ODBC_INSTALL_DRIVER : Installe un nouveau pilote.  
  
 ODBC_REMOVE_DRIVER : Supprime un pilote existant.  
  
 Cette option peut également être spécifiques au pilote, auquel cas la *fréquents* pour la première option doit commencer à partir de ODBC_CONFIG_DRIVER_MAX + 1. Le *fréquents* pour toute option supplémentaire doit également démarrer à partir d’une valeur supérieure à ODBC_CONFIG_DRIVER_MAX + 1.  
  
 *lpszDriver*  
 [Entrée] Le nom du pilote comme inscrit dans les informations système.  
  
 *lpszArgs*  
 [Entrée] Chaîne se terminant par null qui contient les arguments pour un spécifiques au pilote *fréquents*.  
  
 *lpszMsg*  
 [Sortie] Chaîne se terminant par null qui contient un message de sortie à partir de la configuration du pilote.  
  
 *cbMsgMax*  
 [Entrée] Longueur de *lpszMsg.*  
  
 *pcbMsgOut*  
 [Sortie] Nombre total d’octets à retourner dans *lpszMsg*. Si le nombre d’octets à retourner est supérieur ou égal à *cbMsgMax*, le message de sortie dans *lpszMsg* est tronqué à *cbMsgMax* moins le caractère nul de terminaison caractère. Le *pcbMsgOut* argument peut être un pointeur null.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLConfigDriver** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longueur de la mémoire tampon non valide|Le *lpszMsg* argument n’est pas valide.|  
|ODBC_ERROR_INVALID_HWND|Handle de fenêtre non valide|Le *hwndParent* argument n’est pas valide.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Type de demande non valide|Le *fréquents* argument n’est pas une des opérations suivantes :<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> Le *fréquents* argument était une option spécifique au pilote qui était inférieur ou égal à ODBC_CONFIG_DRIVER_MAX.|  
|ODBC_ERROR_INVALID_NAME|Nom de pilote ou de convertisseur non valide|Le *lpszDriver* argument n’est pas valide. Il est introuvable dans le Registre.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Paires mot clé-valeur non valide|Le *lpszArgs* argument contenait une erreur de syntaxe.|  
|ODBC_ERROR_REQUEST_FAILED|*Demande* a échoué|Le programme d’installation n’a pas pu effectuer l’opération demandée par le *fréquents* argument. L’appel à **ConfigDriver** a échoué.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Impossible de charger la bibliothèque le programme d’installation de pilote ou de convertisseur|La bibliothèque d’installation de pilote n’a pas pu être chargée.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLConfigDriver** permet à une application appeler un chauffeur **ConfigDriver** routine sans avoir à connaître le nom et de charger la DLL d’installation spécifiques au pilote. Un programme d’installation appelle cette fonction après l’installation du pilote que DLL a été installé. Le programme appelant doit être conscient que cette fonction n’est peut-être pas disponible pour tous les pilotes. Dans ce cas, le programme appelant doit continuer sans erreur.  
  
## <a name="driver-specific-options"></a>Options spécifiques au pilote  
 Une application peut demander des fonctionnalités spécifiques au pilote exposées par le pilote à l’aide de la *fréquents* argument. Le *fréquents* pour la première option ODBC_CONFIG_DRIVER_MAX + 1, et pour des options supplémentaires seront incrémentées de 1 à partir de cette valeur. Tous les arguments requis par le pilote pour cette fonction doit être fournie dans une chaîne se terminant par null passé dans le *lpszArgs* argument. Les pilotes en fournissant une telle fonctionnalité doivent gérer une table des options spécifiques au pilote. Les options doivent être entièrement documentées dans la documentation du pilote. Les créateurs d’applications qui utilisent les options spécifiques au pilote doivent être conscients que cette utilisation rendre l’application moins interopérable.  
  
## <a name="setting-connection-pooling-timeout"></a>Paramètre délai de connexion multiple  
 Propriétés de délai d’expiration de regroupement de connexions peuvent être définie lorsque vous définissez la configuration du pilote. **SQLConfigDriver** est appelée avec un *fréquents* de ODBC_CONFIG_DRIVER et *lpszArgs* définie sur **CPTimeout**. **CPTimeout** détermine la durée pendant laquelle une connexion peut rester dans le pool de connexions sans être utilisé. Lorsque le délai expire, la connexion est fermée et supprimée du pool. Le délai d’expiration par défaut est de 60 secondes.  
  
 Lorsque **SQLConfigDriver** est appelée avec *fréquents* défini sur ODBC_INSTALL_DRIVER ou ODBC_REMOVE_DRIVER, le Gestionnaire de pilotes charge la DLL d’installation du pilote approprié et appelle le  **ConfigDriver** (fonction). Lorsque **SQLConfigDriver** est appelée avec un *fréquents* de ODBC_CONFIG_DRIVER, tout le traitement est effectué dans le programme d’installation ODBC, afin que la DLL d’installation du pilote ne devra pas être chargé.  
  
## <a name="messages"></a>Messages  
 Une routine de configuration de pilote peut envoyer un message texte à une application en tant que chaînes se terminant par null le *lpszMsg* mémoire tampon. Le message est tronqué à *cbMsgMax* moins le caractère de fin de la valeur null par le **ConfigDriver** fonctionner s’il est supérieur ou égal à *cbMsgMax* caractères.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’un pilote|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)(dans la DLL d’installation)|  
|Suppression de la source de données par défaut|[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|

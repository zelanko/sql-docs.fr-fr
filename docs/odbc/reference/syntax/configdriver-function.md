---
title: ConfigDriver, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d69db144a460bb2f662c8ba906bf0302cdf98388
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821657"
---
# <a name="configdriver-function"></a>ConfigDriver, fonction
**Conformité**  
 Version introduite : ODBC 2.5  
  
 **Résumé**  
 **ConfigDriver** permet à un programme d’installation effectuer l’installation et désinstaller des fonctions sans nécessiter le programme à appeler **ConfigDSN**. Cette fonction effectue les fonctions spécifiques au pilote telles que la création des informations spécifiques au pilote système et effectuer des conversions de source de données pendant l’installation, ainsi que pour nettoyer les modifications du système d’informations pendant la désinstallation. Cette fonction est exposée par la DLL d’installation du pilote ou une DLL d’installation distinct.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
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
 [Entrée] Handle de fenêtre parente. La fonction n’affichera pas les boîtes de dialogue si le handle est null.  
  
 *fréquents*  
 [Entrée] Type de requête. Le *fréquents* argument doit contenir l’une des valeurs suivantes :  
  
 ODBC_INSTALL_DRIVER : Installer un nouveau pilote.  
  
 ODBC_REMOVE_DRIVER : Supprimer un pilote.  
  
 Cette option peut également être spécifiques au pilote, auquel cas la *fréquents* argument pour la première option doit démarrer à partir de ODBC_CONFIG_DRIVER_MAX + 1. Le *fréquents* argument des options supplémentaires doive également démarrer à partir d’une valeur supérieure à ODBC_CONFIG_DRIVER_MAX + 1.  
  
 *lpszDriver*  
 [Entrée] Le nom du pilote comme inscrit dans la clé du fichier Odbcinst.ini des informations système.  
  
 *lpszArgs*  
 [Entrée] Une chaîne se terminant par null qui contient les arguments pour un spécifiques au pilote *fréquents*.  
  
 *lpszMsg*  
 [Sortie] Chaîne se terminant par null qui contient un message de sortie à partir de la configuration du pilote.  
  
 *cbMsgMax*  
 [Entrée] Longueur de *lpszMsg*.  
  
 *pcbMsgOut*  
 [Sortie] Nombre total d’octets à retourner dans *lpszMsg*.  
  
 Si le nombre d’octets à retourner est supérieur ou égal à *cbMsgMax*, le message de sortie dans *lpszMsg* est tronqué à *cbMsgMax* moins le caractère nul de terminaison caractère. Le *pcbMsgOut* argument peut être un pointeur null.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **ConfigDriver** retourne FALSE, associé à un  *\*pfErrorCode* valeur est publiée dans le tampon d’erreur de programme d’installation par un appel à **SQLPostInstallerError** et peut être obtenu en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Handle de fenêtre non valide|Le *hwndParent* argument n’est pas valide.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Type de demande non valide|Le *fréquents* argument n’est pas une des opérations suivantes :<br /><br /> ODBC_INSTALL_DRIVER ODBC_REMOVE_DRIVER<br /><br /> L’option spécifiques au pilote était inférieur ou égal à ODBC_CONFIG_DRIVER_MAX.|  
|ODBC_ERROR_INVALID_NAME|Nom de pilote ou de convertisseur non valide|Le *lpszDriver* argument n’est pas valide. Il est introuvable dans le Registre.|  
|ODBC_ERROR_REQUEST_FAILED|*Demande* a échoué|Ne peut pas effectuer l’opération demandée par le *fréquents* argument.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Erreur spécifique du pilote ou du traducteur|Une erreur spécifique au pilote pour lesquels il n’existe aucune erreur de programme d’installation ODBC défini. Le *SzError* argument dans un appel à la **SQLPostInstallerError** (fonction) doit contenir le message d’erreur spécifique au pilote.|  
  
## <a name="comments"></a>Commentaires  
  
### <a name="driver-specific-options"></a>Options spécifiques au pilote  
 Une application peut demander des fonctionnalités spécifiques au pilote exposées par le pilote à l’aide de la *fréquents* argument. Le *fréquents* pour la première option ODBC_CONFIG_DRIVER_MAX plus 1, et pour des options supplémentaires seront incrémentées de 1 à partir de cette valeur. Tous les arguments requis par le pilote pour cette fonction doit être fournie dans une chaîne se terminant par null passé dans le *lpszArgs* argument. Les pilotes en fournissant une telle fonctionnalité doivent gérer une table des options spécifiques au pilote. Les options doivent être entièrement documentées dans la documentation du pilote. Les créateurs d’applications qui utilisent les options spécifiques au pilote doivent être conscients que cela permettra l’application moins interopérable.  
  
### <a name="messages"></a>Messages  
 Une routine de configuration de pilote peut envoyer un message texte à une application sous forme de chaîne se terminant par null dans le *lpszMsg* mémoire tampon. Le message est tronqué à *cbMsgMax* moins le caractère de fin de la valeur null par le **ConfigDriver** fonctionner s’il est supérieur ou égal à *cbMsgMax* caractères.

---
title: Fonction SQLConfigDataSource (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLConfigDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- SQLConfigDataSource function [ODBC]
ms.assetid: f8d6e342-c010-434e-b1cd-f5371fb50a14
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90a51193a8f4edbb013527c4dde0625b75131583
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299629"
---
# <a name="sqlconfigdatasource-function"></a>Fonction SQLConfigDataSource
**Conformité**  
 Version introduite: ODBC 1.0  
  
 **Résumé**  
 **SQLConfigDataSource** ajoute, modifie ou supprime des sources de données.  
  
 La fonctionnalité de **SQLConfigDataSource** peut également être consultée avec [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLConfigDataSource(  
     HWND     hwndParent,  
     WORD     fRequest,  
     LPCSTR   lpszDriver,  
     LPCSTR   lpszAttributes);  
```  
  
## <a name="arguments"></a>Arguments  
 *hwndParent*  
 [Entrée] Poignée de fenêtre de parent. La fonction n’affichera pas de boîtes de dialogue si la poignée est nulle.  
  
 *fRequest*  
 [Entrée] Type de demande. *L’argument de fRequest* doit contenir l’une des valeurs suivantes :  
  
 ODBC_ADD_DSN : Ajoutez une nouvelle source de données utilisateur.  
  
 ODBC_CONFIG_DSN : Configurer (modifier) une source de données utilisateur existante.  
  
 ODBC_REMOVE_DSN : Supprimez une source de données utilisateur existante.  
  
 ODBC_ADD_SYS_DSN : Ajoutez une nouvelle source de données système.  
  
 ODBC_CONFIG_SYS_DSN : Modifier une source de données système existante.  
  
 ODBC_REMOVE_SYS_DSN : Supprimez une source de données système existante.  
  
 ODBC_REMOVE_DEFAULT_DSN : Supprimez la section de spécifications de source de données par défaut des informations du système. (Il supprime également la section de spécifications du conducteur par défaut de l’entrée Odbcinst.ini dans les informations du système. Ce *fRequest* remplit la même fonction que la fonction dépréciée **SQLRemoveDefaultDataSource.)** Lorsque cette option est spécifiée, tous les autres paramètres de l’appel à **SQLConfigDataSource** doivent être nulLs; s’ils ne sont pas NULL, ils seront ignorés.  
  
 *lpszDriver (en)*  
 [Entrée] Description du pilote (généralement le nom du DBMS associé) présentée aux utilisateurs au lieu du nom du conducteur physique.  
  
 *lpszAttributes*  
 [Entrée] Une liste doublement nulle des attributs sous forme de paires de mots clés. Pour plus d’informations, voir [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md).  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue. Si aucune entrée n’existe dans les informations du système lorsque cette fonction est appelée, la fonction renvoie FALSE.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLConfigDataSource** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_INVALID_HWND|Poignée de fenêtre invalide|*L’argument de hwndParent* était invalide ou NULL.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Type invalide de demande|*L’argument de fRequest* n’était pas l’un des suivants :<br /><br /> ODBC_ADD_DSN ODBC_CONFIG_DSN ODBC_REMOVE_DSN ODBC_ADD_SYS_DSN ODBC_CONFIG_SYS_DSN ODBC_REMOVE_SYS_DSN ODBC_REMOVE_DEFAULT_DSN|  
|ODBC_ERROR_INVALID_NAME|Nom de conducteur ou traducteur invalide|*L’argument de lpszDriver* était invalide. Il n’a pas été trouvé dans le registre.|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Paires de mots clés invalides|*L’argument lpszAttributes* contenait une erreur de syntaxe.|  
|ODBC_ERROR_REQUEST_FAILED|*Demande* a échoué|L’installateur n’a pas pu effectuer l’opération demandée par l’argument *de la fRequest.* L’appel à **ConfigDSN** a échoué.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Impossible de charger le conducteur ou la bibliothèque d’installation de traducteur|La bibliothèque d’installation du conducteur n’a pas pu être chargée.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLConfigDataSource** utilise la valeur de *lpszDriver* pour lire le chemin complet de la configuration DLL pour le conducteur à partir des informations du système. Il charge le DLL et appelle **ConfigDSN** avec les mêmes arguments qui lui ont été transmis.  
  
 **SQLConfigDataSource** retourne FALSE s’il n’est pas en mesure de trouver ou de charger la configuration DLL ou si l’utilisateur annule la boîte de dialogue. Dans le cas contraire, il retourne le statut qu’il a reçu de **ConfigDSN**.  
  
 **SQLConfigDataSource** cartographie le système DSN *fRequest*s à l’utilisateur DSN *fRequest*s (ODBC_ADD_SYS_DSN à ODBC_ADD_DSN, ODBC_CONFIG_SYS_DSN à ODBC_CONFIG_DSN, et ODBC_REMOVE_SYS_DSN à ODBC_REMOVE_DSN). Pour distinguer les DSN de l’utilisateur et du système, **SQLConfigDataSource** définit le mode de configuration de l’installateur en fonction du tableau suivant. Avant de revenir, **SQLConfigDataSource** réinitialise le mode de configuration sur BOTHDSN. **ConfigDSN** (mis en œuvre par les conducteurs) devrait appeler **SQLWriteDSNToIni** et **SQLWritePrivateProfileString** pour prendre en charge un système DSN. Pour plus d’informations, voir [ConfigDSN Function](../../../odbc/reference/syntax/configdsn-function.md).  
  
|*fRequest*|Mode configuration|  
|----------------|------------------------|  
|ODBC_ADD_DSN|USERDSN_ONLY|  
|ODBC_CONFIG_DSN|USERDSN_ONLY|  
|ODBC_REMOVE_DSN|USERDSN_ONLY|  
|ODBC_ADD_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_CONFIG_SYS_DSN|SYSTEMDSN_ONLY|  
|ODBC_REMOVE_SYS_DSN|SYSTEMDSN_ONLY|  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’une source de données|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (dans la configuration DLL)|  
|Suppression d’un nom de source de données des informations du système|[SQLRemoveDSNDeIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|  
|Ajout d’un nom de source de données aux informations du système|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|

---
title: Fonction SQLInstallDriverManager (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallDriverManager
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallDriverManager
helpviewer_keywords:
- SQLInstallDriverManager function [ODBC]
ms.assetid: aebc439b-fffd-4d98-907a-0163f79aee8d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0788de0493439a360c0446733b31606a02e12422
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302110"
---
# <a name="sqlinstalldrivermanager-function"></a>SQLInstallDriverManager, fonction
**Conformité**  
 Version introduite: ODBC 1.0: Déprécié dans Windows XP Service Pack 2, Windows Server 2003 Service Pack 1, et plus tard les systèmes d’exploitation  
  
 **Résumé**  
 **SQLInstallDriverManager** retourne le chemin du répertoire cible pour l’installation des composants de base de l’ODBC. Le programme d’appels doit en fait copier les dossiers du gestionnaire de conducteur à l’annuaire cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLInstallDriverManager(  
     LPSTR    lpszPath,  
     WORD     cbPathMax,  
     WORD *   pcbPathOut);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszPath*  
 [Sortie] Chemin du répertoire cible de l’installation.  
  
 *cbPathMax (en)*  
 [Entrée] Longueur de *lpszPath*. Cela doit être au moins _MAX_PATH octets.  
  
 *pcbPathOut (en anglais)*  
 [Sortie] Nombre total d’octets (à l’exclusion du octet de cessation d’emploi nul) retournés dans *lpszPath*. Si le nombre d’octets disponibles pour revenir est supérieur ou égal à *cbPathMax*, le chemin dans *lpszPath* est tronqué à *cbPathMax* moins le caractère de non-termination. *L’argument pcbPathOut* peut être un pointeur nul.  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLInstallDriverManager** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longueur tampon invalide|*L’argument de lpszPath* n’était pas assez grand pour contenir la trajectoire de sortie. Le tampon contient le chemin tronqué.<br /><br /> *L’argument cbPathMax* était inférieur à _MAX_PATH.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossible d’incrémenter ou de décroisser le nombre d’utilisation des composants|L’installateur n’a pas incrémenté le nombre d’utilisation des composants de base de l’ODBC.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLInstallDriverManager** est appelé à retourner le chemin pour les composants de base ODBC et incrémenter le nombre d’utilisation des composants dans les informations du système. Si une version du Driver Manager existe déjà mais que le nombre d’utilisation des composants pour le conducteur n’existe pas, la nouvelle valeur de comptage d’utilisation des composants est fixée à 2.  
  
 Le programme d’installation d’applications est responsable de copier physiquement les fichiers de composants de base et de maintenir le nombre d’utilisation des fichiers. Si un fichier de composant de base n’a pas encore été installé, le programme de configuration d’application doit copier le fichier et créer le nombre d’utilisation du fichier. Si le fichier a déjà été installé, le programme de configuration ne fait qu’incrémenter le nombre d’utilisation du fichier.  
  
 Si une ancienne version du Driver Manager a déjà été installée par le programme d’installation de l’application, les composants de base doivent être désinstallés, puis réinstallés, de sorte que le nombre d’utilisation des composants de base est valide. **SQLRemoveDriverManager** devrait d’abord être appelé à décroisser le nombre d’utilisation des composants. **SQLInstallDriverManager** devrait alors être appelé pour incrémenter le nombre d’utilisation des composants. Le programme de configuration d’application doit remplacer les anciens fichiers de composants de base par les nouveaux fichiers. Le nombre d’utilisations de fichiers restera le même, et d’autres applications qui ont utilisé les fichiers de composants de base de la version ancienne utiliseront désormais les fichiers de version plus récents.  
  
 Dans une nouvelle installation des composants de base ODBC, les pilotes et les traducteurs, le programme de configuration d’application devrait appeler les fonctions suivantes dans l’ordre: **SQLInstallDriverManager**, **SQLInstallDriverEx**, **SQLConfigDriver** (avec un *fRequest* de ODBC_INSTALL_DRIVER), puis **SQLInstallTranslatorEx**. Dans un désinstallé des composants de base, les pilotes et les traducteurs, le programme de configuration d’application devrait appeler les fonctions suivantes dans l’ordre: **SQLRemoveTranslator**, **SQLRemoveDriver**, puis **SQLRemoveDriverManager**. Ces fonctions doivent être appelées dans cette séquence. Dans une mise à niveau de tous les composants, toutes les fonctions de désinstallation doivent être appelées dans l’ordre, puis toutes les fonctions d’installation doivent être appelées dans l’ordre.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’un conducteur|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Installation d’un conducteur|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|  
|Installation d’un traducteur|[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|  
|Retrait d’un conducteur|[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|  
|Suppression du gestionnaire de conducteur|[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|  
|Suppression d’un traducteur|[SQLRemoveTranslateur](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|

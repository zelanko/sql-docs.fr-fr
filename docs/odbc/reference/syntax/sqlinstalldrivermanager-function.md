---
title: Sqlinstalldrivermanager, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 47069f1003b9b3f9bddb1e8601b3b4284372ae7e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63132693"
---
# <a name="sqlinstalldrivermanager-function"></a>SQLInstallDriverManager, fonction
**Conformité**  
 Version introduite : ODBC 1.0 : Déconseillées dans Windows XP Service Pack 2, Windows Server 2003 Service Pack 1 et versions ultérieures  
  
 **Résumé**  
 **SQLInstallDriverManager** retourne le chemin d’accès du répertoire cible pour l’installation des composants principaux ODBC. Le programme appelant doit copier les fichiers du Gestionnaire de pilotes dans le répertoire cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL SQLInstallDriverManager(  
     LPSTR    lpszPath,  
     WORD     cbPathMax,  
     WORD *   pcbPathOut);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszPath*  
 [Sortie] Chemin d’accès du répertoire cible de l’installation.  
  
 *cbPathMax*  
 [Entrée] Longueur de *lpszPath*. Cela doit être au moins les octets _MAX_PATH.  
  
 *pcbPathOut*  
 [Sortie] Nombre total d’octets (à l’exception de l’octet de caractère nul de terminaison) retournée dans *lpszPath*. Si le nombre d’octets à retourner est supérieur ou égal à *cbPathMax*, le chemin d’accès dans *lpszPath* est tronqué à *cbPathMax* moins le caractère nul de terminaison caractère. Le *pcbPathOut* argument peut être un pointeur null.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLInstallDriverManager** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longueur de la mémoire tampon non valide|Le *lpszPath* argument n’était pas assez grand pour contenir le chemin de sortie. La mémoire tampon contient le chemin d’accès tronquée.<br /><br /> Le *cbPathMax* argument était inférieure à _MAX_PATH.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossible d’incrémenter ou décrémenter le décompte d’utilisation de composant|Le programme d’installation a échoué incrémenter le décompte d’utilisation ODBC core composant.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLInstallDriverManager** est appelée pour retourner le chemin d’accès pour comptent les composants principaux ODBC et l’incrément de l’utilisation du composant dans les informations système. Si une version du Gestionnaire de pilotes existe déjà, mais le nombre d’utilisations de composant pour le pilote n’existe pas, la nouvelle valeur de nombre de l’utilisation de composant est définie à 2.  
  
 Le programme d’installation d’application est responsable de la copier physiquement les fichiers de composant de base et maintenir l’utilisation du fichier de compte. Si un fichier de composant de base n’a pas été précédemment installé, le programme d’installation d’application doit copier le fichier et créer le décompte d’utilisation de fichier. Si le fichier a déjà été installé, le programme d’installation incrémente simplement le décompte d’utilisation de fichier.  
  
 Si une version antérieure du Gestionnaire de pilotes a été précédemment installée par le programme d’installation d’application, les composants de base doivent être désinstallées et réinstallées, afin que le nombre d’utilisations de composant core n’est valide. **SQLRemoveDriverManager** doit tout d’abord être appelé pour décrémenter le décompte d’utilisation de composant. **SQLInstallDriverManager** doit être appelé pour incrémenter le décompte d’utilisation de composant. Le programme d’installation d’application doit remplacer les anciens fichiers de composant core avec les nouveaux fichiers. Le nombre de l’utilisation de fichiers restent les mêmes, et autres applications qui a utilisé les anciens fichiers de composant core version utilise désormais les fichiers de version plus récente.  
  
 Dans une nouvelle installation des composants principaux ODBC, pilotes et les traducteurs, le programme d’installation d’application doit appeler les fonctions suivantes dans la séquence : **SQLInstallDriverManager**, **SQLInstallDriverEx**, **SQLConfigDriver** (avec un *fréquents* de ODBC_INSTALL_DRIVER), puis  **SQLInstallTranslatorEx**. Dans une désinstallation des composants principaux, des pilotes et des traducteurs, le programme d’installation d’application doit appeler les fonctions suivantes dans la séquence : **SQLRemoveTranslator**, **SQLRemoveDriver**, puis **SQLRemoveDriverManager**. Ces fonctions doivent être appelées dans cette séquence. Dans une mise à niveau de tous les composants, toutes les fonctions de désinstallation doivent être appelées dans la séquence et puis toutes les fonctions d’installation doivent être appelées dans la séquence.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’un pilote|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|  
|Installation d’un pilote|[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|  
|L’installation d’un traducteur|[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|  
|Suppression d’un pilote|[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|  
|Suppression du Gestionnaire de pilotes|[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|  
|Suppression d’un traducteur|[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|

---
title: Fonction SQLInstallDriverEx (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallDriverEx
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallDriverEx
helpviewer_keywords:
- SQLInstallDriverEx function [ODBC]
ms.assetid: 1dd74544-f4e9-46e1-9b5f-c11d84fdab4c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 054e8b6b9eae26bd5f973f3d46d7ef37363a8e79
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302121"
---
# <a name="sqlinstalldriverex-function"></a>SQLInstallDriverEx, fonction
**Conformité**  
 Version introduite: ODBC 3.0  
  
 **Résumé**  
 **SQLInstallDriverEx** ajoute des informations sur le conducteur à l’entrée Odbcinst.ini dans l’information du système et incrédule l’utilisation du *conducteurCount* par 1. Toutefois, si une version du pilote existe déjà mais que la valeur *UseCount* pour le conducteur n’existe pas, la nouvelle valeur *UseCount* est fixée à 2.  
  
 Cette fonction ne copie pas réellement de fichiers. Il incombe au programme d’appel de copier correctement les dossiers du conducteur à l’annuaire cible.  
  
 La fonctionnalité de **SQLInstallDriverEx** est également accessible avec [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLInstallDriverEx(  
     LPCSTR    lpszDriver,  
     LPCSTR    lpszPathIn,  
     LPSTR     lpszPathOut,  
     WORD      cbPathOutMax,  
     WORD *    pcbPathOut,  
     WORD      fRequest,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszDriver (en)*  
 [Entrée] La description du conducteur (généralement le nom du DBMS associé) présentée aux utilisateurs au lieu du nom du conducteur physique. *L’argument lpszDriver* doit contenir une liste doublement nulle des paires de valeur de mot-clé décrivant le conducteur. Pour plus d’informations sur les paires de mots-clés, voir [Subkeys de spécification du conducteur](../../../odbc/reference/install/driver-specification-subkeys.md). Pour plus d’informations sur la chaîne doublement nulle, voir [ConfigDSN Function](../../../odbc/reference/syntax/configdsn-function.md).  
  
 *lpszPathIn*  
 [Entrée] Voie complète de l’annuaire cible de l’installation, ou un pointeur nul. Si *lpszPathIn* est un pointeur nul, les pilotes seront installés dans l’annuaire du système.  
  
 *lpszPathOut (en)*  
 [Sortie] Chemin du répertoire cible où le conducteur doit être installé. Si le conducteur n’a pas été installé auparavant, *lpszPathOut* devrait être le même que *lpszPathIn*. Si le conducteur a déjà été installé, *lpszPathOut* est le chemin de l’installation précédente.  
  
 *cbPathOutMax (en)*  
 [Entrée] Longueur de *lpszPathOut*.  
  
 *pcbPathOut (en anglais)*  
 [Sortie] Nombre total d’octets (à l’exclusion du caractère de résiliation nulle) disponibles pour revenir en *lpszPathOut*. Si le nombre d’octets disponibles pour revenir est supérieur ou égal à *cbPathOutMax*, le chemin de sortie dans *lpszPathOut* est tronqué à *cbPathOutMax* moins le caractère de non-termination. *L’argument pcbPathOut* peut être un pointeur nul.  
  
 *fRequest*  
 [Entrée] Type de demande. *L’argument de fRequest* doit contenir l’une des valeurs suivantes :  
  
 ODBC_INSTALL_INQUIRY: Renseignez-vous sur l’endroit où un conducteur peut être installé.  
  
 ODBC_INSTALL_COMPLETE : Complétez la demande d’installation.  
  
 *lpdwUsageCount (en)*  
 [Sortie] Le nombre d’utilisation du conducteur après que cette fonction a été appelée.  
  
 Les applications ne doivent pas définir le nombre d’utilisations. ODBC maintiendra ce décompte.  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLInstallDriverEx** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longueur tampon invalide|*L’argument lpszPathOut* n’était pas assez grand pour contenir la trajectoire de sortie. Le tampon contient le chemin tronqué.<br /><br /> *L’argument cbPathOutMax* était 0, et *fRequest* a été ODBC_INSTALL_COMPLETE.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Type invalide de demande|*L’argument de fRequest* n’était pas l’un des suivants :<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Paires de mots clés invalides|*L’argument lpszDriver* contenait une erreur de syntaxe.|  
|ODBC_ERROR_INVALID_PATH|Chemin d’installation invalide|*L’argument lpszPathIn* contenait un chemin invalide.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Impossible de charger le conducteur ou la bibliothèque d’installation de traducteur|La bibliothèque d’installation du conducteur n’a pas pu être chargée.|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Séquence de paramètres invalides|*L’argument de lpszDriver* ne contenait pas de liste de paires de mots clés.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossible d’incrémenter ou de décroisser le nombre d’utilisation des composants|L’installateur n’a pas incrémenté le compte d’utilisation du conducteur.|  
  
## <a name="comments"></a>Commentaires  
 *L’argument lpszDriver* est une liste d’attributs sous forme de paires de mots clés. Chaque paire est terminée avec un byte nul, et la liste entière est terminée avec un byte nul. (C’est-à-dire que deux octets nuls marquent la fin de la liste.) Le format de cette liste est le suivant :  
  
 _driver-desc_ **\\**0Driver**=**_driver-DLL-filename_**\\****=** 0[Setup_setup-DLL-filename_<b>\\</b>0]  
  
 _[conducteur-attr-mot-clé1_**=**_valeur1_<b>\\</b>0] _[conducteur-attr-keyword2_**=**_value2_<b>\\</b>0]... <b>\\</b>0  
  
 où le mot clé d’attribut du *conducteur* est le 000. Les mots clés doivent apparaître dans l’ordre spécifié. Supposons, par exemple, qu’un pilote pour les fichiers texte formatés dispose de DLLs de pilote et de configuration distincts et qu’il puisse utiliser des fichiers avec les extensions .txt et .csv. *L’argument lpszDriver* pour ce pilote pourrait être le suivant:  
  
```  
Text\0Driver=TEXT.DLL\0Setup=TXTSETUP.DLL\0FileUsage=1\0  
FileExtns=*.txt,*.csv\0\0  
```  
  
 Supposons qu’un pilote pour SQL Server n’a pas une configuration distincte DLL et n’a pas de mots clés d’attribut pilote. *L’argument lpszDriver* pour ce pilote pourrait être le suivant:  
  
```  
SQL Server\0Driver=SQLSRVR.DLL\0\0  
```  
  
 Après **que SQLInstallDriverEx** a récupéré des informations sur le conducteur de *l’argument lpszDriver,* il ajoute la description du conducteur à la section [ODBC Drivers] de l’entrée Odbcinst.ini dans les informations du système. Il crée ensuite une section intitulée avec la description du conducteur et ajoute les chemins complets du pilote DLL et la configuration DLL. Enfin, il retourne le chemin de l’annuaire cible de l’installation, mais ne copie pas les fichiers du conducteur à elle. Le programme d’appels doit en fait copier les fichiers du conducteur au répertoire cible.  
  
 **SQLInstallDriverEx** incréments le nombre d’utilisation des composants pour le conducteur installé par 1. Si une version du pilote existe déjà mais que le nombre d’utilisation des composants pour le conducteur n’existe pas, la nouvelle valeur de comptage d’utilisation des composants est fixée à 2.  
  
 Le programme d’installation d’applications est responsable de copier physiquement le fichier conducteur et de maintenir le nombre d’utilisation du fichier. Si le fichier pilote n’a pas encore été installé, le programme de configuration d’application doit copier le fichier dans le chemin *lpszPathIn* et créer le nombre d’utilisation du fichier. Si le fichier a déjà été installé, le programme de configuration incrémente simplement le nombre d’utilisation du fichier et retourne le chemin de l’installation précédente dans *l’argument lpszPathOut.*  
  
> [!NOTE]  
>  Pour plus d’informations sur le nombre d’utilisation des composants et le nombre d’utilisation des fichiers, voir [Compter l’utilisation](../../../odbc/reference/install/usage-counting.md).  
  
 Si une ancienne version du fichier conducteur a déjà été installée par l’application, le conducteur doit être désinstallé puis réinstallé, de sorte que le nombre d’utilisation des composants du conducteur est valide. **SQLConfigDriver** (avec un *fRequest* de ODBC_REMOVE_DRIVER) devrait d’abord être appelé, puis **SQLRemoveDriver** devrait être appelé à décroissance le nombre d’utilisation des composants. **SQLInstallDriverEx** devrait alors être appelé pour réinstaller le conducteur, incrémentant le nombre d’utilisation des composants. Le programme de configuration d’application doit remplacer l’ancien fichier par le nouveau fichier. Le nombre d’utilisation du fichier restera le même, et toute autre application qui a utilisé l’ancien fichier de version utilisera maintenant la version la plus récente.  
  
> [!NOTE]  
>  Si le conducteur a déjà été installé et **SQLInstallDriverEx** est appelé à installer le conducteur dans un répertoire différent, la fonction retournera VRAI, mais *lpszPathOut* comprendra le répertoire où le conducteur a déjà été installé. Il n’inclura pas le répertoire inscrit dans *l’argument lpszDriver.*  
  
 La longueur du chemin dans *lpszPathOut* dans **SQLInstallDriverEx** permet un processus d’installation en deux phases, de sorte qu’une application peut déterminer ce que *cbPathOutMax* devrait être en appelant **SQLInstallDriverEx** avec un *fRequest* de mode ODBC_INSTALL_INQUIRY. Cela rendra le nombre total d’octets disponibles dans le tampon *pcbPathOut.* **SQLInstallDriverEx** peut alors être appelé avec un *fRequest* de ODBC_INSTALL_COMPLETE et *l’argument cbPathOutMax* réglé à la valeur dans le tampon *pcbPathOut,* plus le caractère de non-termination.  
  
 Si vous choisissez de ne pas utiliser le modèle en deux phases pour **SQLInstallDriverEx**, vous devez définir *cbPathOutMax*, qui définit la taille du stockage pour le chemin de l’annuaire cible, à la valeur _MAX_PATH, tel que défini dans Stdlib.h, pour empêcher la troncation.  
  
 Lorsque *fRequest* est ODBC_INSTALL_COMPLETE, **SQLInstallDriverEx** ne permet pas *lpszPathOut* d’être NULL (ou *cbPathOutMax* à 0). Si *fRequest* est ODBC_INSTALL_COMPLETE, FALSE est retourné lorsque le nombre d’octets disponibles pour revenir est supérieur ou égal à *cbPathOutMax*, avec le résultat que la troncation se produit.  
  
 Après **SQLInstallDriverEx** a été appelé et le programme d’installation d’application a copié le fichier du conducteur (si nécessaire), la configuration du conducteur DLL doit appeler **SQLConfigDriver** pour définir la configuration pour le conducteur.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Installation du Gestionnaire de pilotes|[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|

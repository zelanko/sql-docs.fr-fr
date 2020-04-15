---
title: Fonction SQLInstallTranslatorEx (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallTranslatorEx
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallTranslatorEx
helpviewer_keywords:
- SQLInstallTranslatorEx function [ODBC]
ms.assetid: a0630602-53c1-4db0-98ce-70d160aedf8d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5cf52c26bf9e4a26f13a27a0e763fbaa30bd18ec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302090"
---
# <a name="sqlinstalltranslatorex-function"></a>SQLInstallTranslatorEx, fonction
**Conformité**  
 Version introduite: ODBC 3.0  
  
 **Résumé**  
 **SQLInstallTranslatorEx** ajoute des informations sur un traducteur à la section Odbcinst.ini des informations du système (HKEY_LOCAL_MACHINE-SOFTWARE-ODBC-ODBCINST. Clé de registre des traducteurs INI-ODBC).  
  
 La fonctionnalité de **SQLInstallTranslatorEx** peut également être consultée avec [ODBCCONF. EXE](../../../odbc/odbcconf-exe.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLInstallTranslatorEx(  
     LPCSTR    lpszTranslator,  
     LPCSTR    lpszPathIn,  
     LPSTR     lpszPathOut,  
     WORD      cbPathOutMax,  
     WORD *    pcbPathOut,  
     WORD      fRequest,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszTranslateur*  
 [Entrée] Cela doit contenir une liste doublement nulle des paires de mots clés décrivant le traducteur. Pour plus d’informations sur la syntaxe de paire de mots-clés, voir [Subkeys de spécification de traducteur](../../../odbc/reference/install/translator-specification-subkeys.md).  
  
 Les mots-clés **De traducteur** et **de configuration** doivent être inclus dans la chaîne *lpszTranslator.* La traduction DLL est répertoriée avec le mot-clé **Traducteur,** et la configuration du traducteur DLL est répertoriée avec le mot clé **Setup.** Chaque paire est terminée avec un byte NULL, et la liste entière est terminée avec un byte NULL. (C’est-à-dire que deux octets NULL marquent la fin de la liste.) Le format de *lpszTranslator* est le suivant:  
  
 '0Translator'*traducteur-DLL-fichiername*'0[Setup'-DLL-filename '0] '0]*setup-DLL-filename*  
  
 *lpszPathIn*  
 [Entrée] Chemin complet de l’endroit où le traducteur doit être installé ou un pointeur nul. Si *lpszPath* est un pointeur nul, les traducteurs seront installés dans le répertoire du système.  
  
 *lpszPathOut (en)*  
 [Sortie] Le chemin du répertoire cible où le traducteur doit être installé. Si le traducteur n’a jamais été installé, *lpszPathOut* est le même que *lpszPathIn*. S’il existe une installation préalable du traducteur, *lpszPathOut* est le chemin de l’installation précédente.  
  
 *cbPathOutMax (en)*  
 [Entrée] Longueur de *lpszPathOut.*  
  
 *pcbPathOut (en anglais)*  
 [Sortie] Nombre total d’octets disponibles pour revenir en *lpszPathOut*. Si le nombre d’octets disponibles pour revenir est supérieur ou égal à *cbPathOutMax*, le chemin de sortie dans *lpszPathOut* est tronqué à *pcbPathOutMax* moins le caractère de non-termination. *L’argument pcbPathOut* peut être un pointeur nul.  
  
 *fRequest*  
 [Entrée] Type de demande. *fRequest* doit contenir l’une des valeurs suivantes :  
  
 ODBC_INSTALL_INQUIRY : Renseignez-vous sur l’endroit où un traducteur peut être installé.  
  
 ODBC_INSTALL_COMPLETE : Complétez la demande d’installation.  
  
 *lpdwUsageCount (en)*  
 [Sortie] Le nombre d’utilisation du traducteur après que cette fonction a été appelée.  
  
 Les applications ne doivent pas définir le nombre d’utilisations. ODBC maintiendra ce décompte.  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLInstallTranslatorEx** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longueur tampon invalide|*L’argument lpszPathOut* n’était pas assez grand pour contenir la trajectoire de sortie. Le tampon contient le chemin tronqué.<br /><br /> *L’argument cbPathOutMax* était 0, et *l’argument fRequest* était ODBC_INSTALL_COMPLETE.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Type invalide de demande|*L’argument de fRequest* n’était pas l’un des suivants :<br /><br /> ODBC_INSTALL_INQUIRY ODBC_INSTALL_COMPLETE|  
|ODBC_ERROR_INVALID_KEYWORD_VALUE|Paires de mots clés invalides|*L’argument lpszTranslator* contenait une erreur de syntaxe.|  
|ODBC_ERROR_INVALID_PATH|Chemin d’installation invalide|*L’argument lpszPathIn* contenait un chemin invalide.|  
|ODBC_ERROR_INVALID_PARAM_SEQUENCE|Séquence de paramètres invalides|*L’argument de lpszTranslator* ne contenait pas de liste de paires de mots clés.|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|Impossible d’incrémenter ou de décroisser le nombre d’utilisation des composants du registre|L’installateur n’a pas incrémenté le nombre d’utilisation du traducteur.|  
  
## <a name="comments"></a>Commentaires  
 **SQLInstallTranslatorEx** fournit un mécanisme pour installer uniquement le traducteur. Cette fonction ne copie pas réellement de fichiers. Le programme d’appels est responsable de la copie des fichiers de traducteur.  
  
 **SQLInstallTranslatorEx** incréments le nombre d’utilisation des composants pour le traducteur installé par 1. Si une version du traducteur existe déjà mais que le nombre d’utilisation des composants pour le traducteur n’existe pas, la nouvelle valeur de comptage d’utilisation des composants est fixée à 2.  
  
 Le programme d’installation d’applications est responsable de la copie physique du fichier de traducteur et du maintien du nombre d’utilisation du fichier. Si le fichier de traducteur n’a pas encore été installé, le programme de configuration de l’application doit copier le fichier ou les fichiers et créer le fichier ou le nombre d’utilisation des fichiers. Si le fichier a déjà été installé, le programme de configuration incrémente simplement le nombre d’utilisation du fichier.  
  
 Si une version plus ancienne du traducteur a déjà été installée par l’application, le traducteur doit être désinstallé puis réinstallé, de sorte que le nombre d’utilisation des composants du traducteur est valide. **SQLRemoveTranslator** devrait être appelé à décérer le nombre d’utilisation des composants, puis **SQLInstallTranslatorEx** devrait être appelé à incrémenter le nombre d’utilisation des composants. Le programme de configuration de l’application doit remplacer l’ancien fichier ou les fichiers par le nouveau fichier. Le nombre d’utilisation du fichier restera le même, et d’autres applications qui ont utilisé l’ancien fichier de version utiliseront désormais la version la plus récente.  
  
 La longueur du chemin dans *lpszPathOut* dans **SQLInstallTranslatorEx** permet un processus d’installation en deux phases, de sorte qu’une application peut déterminer ce que *cbPathOutMax* devrait être en appelant **SQLInstallTranslatorEx** avec un *fRequest* de ODBC_INSTALL_INQUIRY mode. Cela rendra le nombre total d’octets disponibles dans le tampon *pcbPathOut.* **SQLInstallTranslatorEx** peut alors être appelé avec un *fRequest* de ODBC_INSTALL_COMPLETE et *l’argument cbPathOutMax* réglé à la valeur dans le tampon *pcbPathOut,* plus le caractère de désilisation nulle.  
  
 Si vous choisissez de ne pas utiliser le modèle en deux phases pour **SQLInstallTranslatorEx**, vous devez définir *cbPathOutMax*, qui définit la taille du stockage pour le chemin de l’annuaire cible, à la valeur _MAX_PATH, tel que défini dans Stdlib.h, pour empêcher la troncation.  
  
 Lorsque *fRequest* est ODBC_INSTALL_COMPLETE, **SQLInstallTranslatorEx** ne permet pas *lpszPathOut* d’être NULL (ou *cbPathOutMax* à 0). Si *fRequest* est ODBC_INSTALL_COMPLETE, FALSE est retourné lorsque le nombre d’octets disponibles pour revenir est supérieur ou égal à *cbPathOutMax*, avec le résultat que la troncation se produit.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Retour d’une option de traduction par défaut|[ConfigTranslateur](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Sélection des traducteurs|[SQLGetTranslator (SQLGetTranslator)](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Suppression des traducteurs|[SQLRemoveTranslateur](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|

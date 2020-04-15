---
title: Fonction SQLGetTranslator (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetTranslator
helpviewer_keywords:
- SQLGetTranslator function [ODBC]
ms.assetid: 33879db3-5ef9-4585-9be5-69376157e017
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bcd5aeebab8539b8b94db56ff30892f4a7dbbac1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303270"
---
# <a name="sqlgettranslator-function"></a>SQLGetTranslator, fonction
**Conformité**  
 Version introduite: ODBC 2.0  
  
 **Résumé**  
 **SQLGetTranslator** affiche une boîte de dialogue à partir de laquelle un utilisateur peut sélectionner un traducteur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLGetTranslator(  
     HWND      hwndParent,  
     LPSTR     lpszName,  
     WORD      cbNameMax,  
     WORD *    pcbNameOut,  
     LPSTR     lpszPath,  
     WORD      cbPathMax,  
     WORD *    pcbPathOut,  
     DWORD *   pvOption);  
```  
  
## <a name="arguments"></a>Arguments  
 *hwndParent*  
 [Entrée] Poignée de fenêtre de parent.  
  
 *lpszName (en)*  
 [Entrée/sortie] Nom du traducteur à partir des informations du système.  
  
 *cbNameMax (en)*  
 [Entrée] Longueur maximale du tampon *lpszName.*  
  
 *pcbNameOut (en anglais)*  
 [Entrée/sortie] Nombre total d’octets (à l’exclusion du octet de cessation d’emploi nul) passés ou retournés en *lpszName*. Si le nombre d’octets disponibles pour revenir est supérieur ou égal à *cbNameMax*, le nom du traducteur dans *lpszName* est tronqué à *cbNameMax* moins le caractère de non-termination. *L’argument pcbNameOut* peut être un pointeur nul.  
  
 *lpszPath*  
 [Sortie] Chemin complet de la traduction DLL.  
  
 *cbPathMax (en)*  
 [Entrée] Longueur maximale du tampon *lpszPath.*  
  
 *pcbPathOut (en anglais)*  
 [Sortie] Nombre total d’octets (à l’exclusion du octet de cessation d’emploi nul) retournés dans *lpszPath*. Si le nombre d’octets disponibles pour revenir est supérieur ou égal à *cbPathMax*, le chemin de traduction DLL dans *lpszPath* est tronqué à *cbPathMax* moins le caractère de désilisation nulle. *L’argument pcbPathOut* peut être un pointeur nul.  
  
 *pvOption*  
 [Sortie] option de traduction 32 bits.  
  
## <a name="returns"></a>Retours  
 La fonction renvoie TRUE si elle est réussie, FALSE si elle échoue ou si l’utilisateur annule la boîte de dialogue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetTranslator** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longueur tampon invalide|*L’argument cbNameMax* ou *cbPathMax* était inférieur ou égal à 0.|  
|ODBC_ERROR_INVALID_HWND|Poignée de fenêtre invalide|*L’argument de hwndParent* était invalide ou NULL.|  
|ODBC_ERROR_INVALID_NAME|Nom de conducteur ou traducteur invalide|*L’argument de lpszName était invalide.* Il n’a pas été trouvé dans le registre.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Impossible de charger le conducteur ou la bibliothèque d’installation de traducteur|La bibliothèque de traducteurs n’a pas pu être chargée.|  
|ODBC_ERROR_INVALID_OPTION|Option de transaction invalide|*L’argument de l’pvOption* contenait une valeur invalide.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 Si *hwndParent* est nul ou si *lpszName*, *lpszPath*, ou *pvOption* est un pointeur nul, **SQLGetTranslator** retourne FALSE. Dans le cas contraire, il affiche la liste des traducteurs installés dans la boîte de dialogue suivante.  
  
 ![Boîte de dialogue Sélectionner le convertisseur](../../../odbc/reference/syntax/media/ch23j.gif "CH23J")  
  
 Si *lpszName* contient un nom de traducteur valide, il est sélectionné. Sinon, \<aucun traducteur> n’est sélectionné.  
  
 Si l’utilisateur \<choisit No Translator>, le contenu de *lpszName*, *lpszPath*, et *pvOption* ne sont pas touchés. **SQLGetTranslator** définit *pcbNameOut* et *pcbPathOut* à 0 et retourne TRUE.  
  
 Si l’utilisateur choisit un traducteur, **SQLGetTranslator** appelle **ConfigTranslator** dans la configuration DLL du traducteur. Si **ConfigTranslator** retourne FALSE, **SQLGetTranslator** retourne à sa boîte de dialogue. Si **ConfigTranslator** retourne TRUE, **SQLGetTranslator** retourne TRUE, ainsi que l’option de nom, de chemin et de traduction du traducteur sélectionné.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Configurer un traducteur|[ConfigTranslateur](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Obtenir un attribut de traduction|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Définir un attribut de traduction|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|

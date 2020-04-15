---
title: FONCTION SQLWritePrivateProfileString (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLWritePrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWritePrivateProfileString
helpviewer_keywords:
- SQLWritePrivateProfileString [ODBC]
ms.assetid: 526f36a4-92ed-4874-9725-82d27c0b86f9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b0de5ad074fb2b760420686feddff58b26887112
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286882"
---
# <a name="sqlwriteprivateprofilestring-function"></a>SQLWritePrivateProfileString, fonction
**Conformité**  
 Version introduite: ODBC 2.0  
  
 **Résumé**  
 **SQLWritePrivateProfileString** écrit un nom de valeur et des données au sous-clé Odbc.ini des informations du système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLWritePrivateProfileString(  
     LPCSTR     lpszSection,  
     LPCSTR     lpszEntry,  
     LPCSTR     lpszString,  
     LPCSTR     lpszFilename);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszSection*  
 [Entrée] Indique une corde non terminée contenant le nom de la section à laquelle la chaîne sera copiée. Si l’article n’existe pas, il est créé. Le nom de l’article est indépendant des cas; la ficelle peut être n’importe quelle combinaison de majuscules et de lettres minuscules.  
  
 *lpszEntry (en)*  
 [Entrée] Indique une corde non terminée contenant le nom de la clé à associer à une chaîne. Si la clé n’existe pas dans la section spécifiée, elle est créée. Si cet argument est NULL, toute la section, y compris toutes les entrées dans la section, est supprimée.  
  
 *lpszString (lpszString)*  
 [Entrée] Indique une corde non résiliée à écrire au dossier. Si cet argument est NULL, la clé pointée par *l’argument lpszEntry* est supprimée.  
  
 *lpszFilename*  
 [Sortie] Indique une chaîne non terminée qui nomme le fichier d’initialisation.  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLWritePrivateProfileString** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_REQUEST_FAILED|Échec de la demande|Les renseignements sur le système demandé n’ont pas pu être rédigés.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLWritePrivateProfileString** est fourni comme un moyen simple pour les pilotes de port et d’installation du conducteur DLLs de Microsoft® Windows® à Microsoft Windows NT®/Windows 2000. Les appels à **WritePrivateProfileString** qui écrivent une chaîne de profil au fichier Odbc.ini doivent être remplacés par des appels à **SQLWritePrivateProfileString**. **SQLWritePrivateProfileString** appelle des fonctions dans l’API de 32 ® pour ajouter le nom et les données de valeur spécifiés au sous-clé Odbc.ini des informations du système.  
  
 Un mode de configuration indique où l’entrée Odbc.ini énumérant les valeurs DSN est dans les informations du système. Si le DSN est un DSN utilisateur (la variable d’état est USERDSN_ONLY), la fonction écrit à l’entrée Odbc.ini dans HKEY_CURRENT_USER. Si le DSN est un système DSN (SYSTEMDSN_ONLY), la fonction écrit à l’entrée Odbc.ini dans HKEY_LOCAL_MACHINE. Si la variable d’état est BOTHDSN, HKEY_CURRENT_USER est essayée, et si elle échoue, HKEY_LOCAL_MACHINE est utilisé.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Obtenir une valeur de l’information du système|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|

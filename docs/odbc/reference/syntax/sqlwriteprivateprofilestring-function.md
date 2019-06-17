---
title: Sqlwriteprivateprofilestring, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff853976cf0d900cb24391ff6bf13838782ea876
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536772"
---
# <a name="sqlwriteprivateprofilestring-function"></a>SQLWritePrivateProfileString, fonction
**Conformité**  
 Version introduite : ODBC 2.0  
  
 **Résumé**  
 **SQLWritePrivateProfileString** écrit un nom de la valeur et les données dans la sous-clé Odbc.ini des informations système.  
  
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
 [Entrée] Pointe vers une chaîne se terminant par null qui contient le nom de la section où la chaîne doit être copiée. Si la section n’existe pas, il est créé. Le nom de la section est indépendante de la casse ; la chaîne peut être toute combinaison de lettres majuscules et les minuscules.  
  
 *lpszEntry*  
 [Entrée] Pointe vers une chaîne se terminant par null qui contient le nom de la clé à associer à une chaîne. Si la clé n’existe pas dans la section spécifiée, il est créé. Si cet argument est NULL, la section entière, y compris toutes les entrées dans la section, est supprimée.  
  
 *lpszString*  
 [Entrée] Pointe vers une chaîne se terminant par null à écrire dans le fichier. Si cet argument est NULL, la clé vers laquelle pointe le *lpszEntry* argument est supprimé.  
  
 *lpszFilename*  
 [Sortie] Pointe vers une chaîne se terminant par null qui nomme le fichier d’initialisation.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLWritePrivateProfileString** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_REQUEST_FAILED|Échoué de la demande|Impossible d’écrire les informations système demandé.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLWritePrivateProfileString** est fourni comme un moyen simple de pilotes de port et le programme d’installation de pilote DLL à partir de Microsoft® Windows® pour Microsoft Windows/Windows 2000. Les appels à **WritePrivateProfileString** qui écrivent une chaîne de profil dans le fichier Odbc.ini doit être remplacée par des appels à **SQLWritePrivateProfileString**. **SQLWritePrivateProfileString** appelle des fonctions dans l’API Win32® pour ajouter le nom de la valeur spécifiée et les données à la sous-clé Odbc.ini des informations système.  
  
 Un mode de configuration indique où l’entrée de fichier Odbc.ini répertoriant les valeurs de la source de données est dans les informations système. Si la source de données est une source de données utilisateur (la variable d’état est USERDSN_ONLY), la fonction écrit à l’entrée de fichier Odbc.ini dans HKEY_CURRENT_USER. Si la source de données est une source de données système (SYSTEMDSN_ONLY), la fonction écrit à l’entrée de fichier Odbc.ini dans HKEY_LOCAL_MACHINE. Si la variable d’état est BOTHDSN, HKEY_CURRENT_USER est tentée, et si elle échoue, HKEY_LOCAL_MACHINE est utilisée.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Obtention d’une valeur à partir des informations système|[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|

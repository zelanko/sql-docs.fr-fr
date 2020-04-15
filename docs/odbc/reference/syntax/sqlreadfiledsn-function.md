---
title: Fonction SQLReadFileDSN (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLReadFileDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLReadFileDSN
helpviewer_keywords:
- SQLReadFileDSN function [ODBC]
ms.assetid: ead464aa-cdc3-47dd-a0c0-997711205d31
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3abda956ee7682c9ac49270e8bf69fb039641790
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303950"
---
# <a name="sqlreadfiledsn-function"></a>SQLReadFileDSN, fonction
**Conformité**  
 Version introduite: ODBC 3.0  
  
 **Résumé**  
 **SQLReadFileDSN** lit les informations d’un fichier DSN.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLReadFileDSN(  
     LPCSTR   lpszFileName,  
     LPCSTR   lpszAppName,  
     LPCSTR   lpszKeyName,  
     LPSTR    lpszString,  
     WORD     cbString,  
     WORD *   pcbString);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszFileName*  
 [Entrée] Pointeur vers le tampon de données contenant le nom du fichier .dsn. Une extension .dsn est annexée à tous les noms de fichiers qui n’ont pas déjà une extension .dsn. La valeur de * \*lpszFileName* doit être une chaîne non terminée.  
  
 *lpszAppName*  
 [Entrée] Pointeur vers le tampon de données contenant le nom de l’application. Il s’agit de "ODBC" pour la section ODBC. La valeur de * \*lpszAppName* doit être une chaîne non terminée.  
  
 *lpszKeyName (en)*  
 [Entrée] Pointeur vers le tampon de données contenant le nom de la clé à lire. Voir "Commentaires" pour les mots-clés réservés. La valeur de * \*lpszAppName* doit être une chaîne non terminée.  
  
 *lpszString (lpszString)*  
 [Sortie] Pointeur vers le tampon de données contenant la chaîne associée à la clé à lire.  
  
 Si * \*lpszFileName* est un nom de fichier .dsn valide, mais *l’argument lpszAppName* est un pointeur nul et *l’argument lpszKeyName* est un pointeur nul, puis * \*lpszString* contient une liste d’applications valides. Si * \*lpszFileName* est un nom de fichier .dsn valide et * \*lpszAppName* est un nom de demande valide, mais *l’argument lpszKeyName* est un pointeur nul, puis * \*lpszString* contient une liste de mots clés réservés valides dans la section appropriée du fichier DSN, délimité par des semi-colons. Si * \*lpszFileName* est un nom de fichier .dsn valide, mais * \*lpszAppName* est un pointeur nul et *l’argument lpszKeyName* est un pointeur nul, puis * \*lpszString* contient une liste des sections dans le fichier DSN, délimité par des semicolons.  
  
 *cbString (en)*  
 [Entrée] Longueur du * \*tampon lpszString.*  
  
 *pcbString (en anglais)*  
 [Sortie] Nombre total d’octets disponibles pour revenir en * \*lpszString*. Si le nombre d’octets disponibles pour revenir est supérieur ou égal à *cbString*, la chaîne de sortie en * \*lpszString* est tronquée à *cbString* moins le caractère de non-termination. *L’argument pcbString* peut être un pointeur nul.  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLReadFileDSN** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longueur tampon invalide|*L’argument de lpszString* était NULL.<br /><br /> *L’argument cbString* était inférieur ou égal à 0.|  
|ODBC_ERROR_INVALID_PATH|Chemin d’installation invalide|La voie du nom du fichier spécifiée dans *l’argument lpszFileName était invalide.*|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Type invalide de demande|*L’argument lpszAppName* était NULL, tandis que *l’argument lpszKeyName* était valide.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
|ODBC_ERROR_OUTPUT_STRING_TRUNCATED|Chaîne de sortie tronquée|La chaîne retournée en * \*lpszString* a été tronquée parce que la valeur dans *cbString* était inférieure ou égale à la valeur dans * \*pcbString*.|  
|ODBC_ERROR_REQUEST_FAILED|Échec de la demande|Le mot clé n’existait pas dans le fichier DSN.|  
  
## <a name="comments"></a>Commentaires  
 ODBC réserve le nom de section [ODBC] dans lequel stocker les informations de connexion. Les mots-clés réservés pour cette section sont les mêmes que ceux réservés à une chaîne de connexion dans **SQLDriverConnect**. (Pour plus d’informations, consultez la description de la fonction [SQLDriverConnect.)](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Les applications peuvent utiliser ces mots clés réservés pour lire les informations dans un fichier DSN. Si une application veut connaître la chaîne de connexion sans DSN associée à un DSN de fichier, elle peut appeler **SQLReadFileDSN** pour l’un des mots clés réservés de chaîne de connexion dans la section [ODBC]. La chaîne de connexion complète passée dans une connexion sans DSN est une combinaison de tous les mots clés (réservés et spécifiques au conducteur) dans la section [ODBC].  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Rédaction d’informations à un fichier DSN|[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|

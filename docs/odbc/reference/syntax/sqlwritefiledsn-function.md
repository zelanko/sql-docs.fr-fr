---
title: Fonction SQLWriteFileDSN (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLWriteFileDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLWriteFileDSN
helpviewer_keywords:
- SQLWriteFileDSN [ODBC]
ms.assetid: 9e18f56f-1061-416b-83d4-ffeec42ab5a9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e781f1be79e0079f33b3d0800c665f5f5e9fda4d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286889"
---
# <a name="sqlwritefiledsn-function"></a>SQLWriteFileDSN, fonction
**Conformité**  
 Version introduite: ODBC 3.0  
  
 **Résumé**  
 **SQLWriteFileDSN** écrit des informations à un fichier DSN.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLWriteFileDSN(  
     LPCSTR     lpszFileName,  
     LPCSTR     lpszAppName,  
     LPCSTR     lpszKeyName,  
     LPCSTR     lpszString);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszFileName*  
 [Entrée] Pointeur au nom du fichier DSN. Une extension DSN est annexée à tous les noms de fichiers qui n’ont pas déjà d’extension DSN.  
  
 *lpszAppName*  
 [Entrée] Pointeur sur le nom de l’application. Il s’agit de "ODBC" pour la section ODBC.  
  
 *lpszKeyName (en)*  
 [Entrée] Pointeur sur le nom de la clé à lire. Voir "Commentaires" pour les mots-clés réservés.  
  
 *lpszString (lpszString)*  
 [Sortie] Pointé vers la chaîne associée à la clé à écrire. La longueur maximale de la chaîne soulignée par cet argument est de 32 767 octets.  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLWriteFileDSN** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_INVALID_PATH|Chemin d’installation invalide|La voie du nom du fichier spécifiée dans *l’argument lpszFileName était invalide.*|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Type invalide de demande|*L’argument lpszAppName*, *lpszKeyName*, ou *lpszString* argument était NULL.|  
  
## <a name="comments"></a>Commentaires  
 ODBC réserve le nom de section [ODBC] dans lequel stocker les informations de connexion. Les mots-clés réservés pour cette section sont les mêmes que ceux réservés à une chaîne de connexion dans **SQLDriverConnect**. (Pour plus d’informations, consultez la description de la fonction [SQLDriverConnect.)](../../../odbc/reference/syntax/sqldriverconnect-function.md)  
  
 Les applications peuvent utiliser ces mots clés réservés pour écrire des informations directement sur un DSN de fichier. Si une application veut créer ou modifier la chaîne de connexion sans DSN associée à un DSN de fichier, elle peut appeler **SQLWriteFileDSN** pour l’un des mots clés réservés de chaîne de connexion dans la section [ODBC].  
  
 Si *l’argument lpszString* est un pointeur nul, le mot clé pointé par *l’argument lpszKeyName* sera supprimé du fichier .dsn. Si les arguments *lpszString* et *lpszKeyName* sont tous deux des pointeurs nuls, la section pointée par *l’argument lpszAppName* sera supprimée du fichier .dsn.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lecture des informations tirées des DSN du fichier|[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|

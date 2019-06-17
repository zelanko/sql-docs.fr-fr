---
title: SQLReadFileDSN Function | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f32e23be700f17fee88cc6354f8652bb1333a12c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537349"
---
# <a name="sqlreadfiledsn-function"></a>SQLReadFileDSN, fonction
**Conformité**  
 Version introduite : ODBC 3.0  
  
 **Résumé**  
 **SQLReadFileDSN** lit les informations dans un fichier DSN.  
  
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
 [Entrée] Pointeur vers la mémoire tampon de données contenant le nom du fichier .dsn. Une extension .dsn est ajoutée à tous les noms de fichier qui n’est pas déjà une extension .dsn. La valeur dans  *\*lpszFileName* doit être une chaîne se terminant par null.  
  
 *lpszAppName*  
 [Entrée] Pointeur vers la mémoire tampon de données contenant le nom de l’application. Il s’agit « ODBC » pour la section ODBC. La valeur dans  *\*lpszAppName* doit être une chaîne se terminant par null.  
  
 *lpszKeyName*  
 [Entrée] Pointeur vers la mémoire tampon de données contenant le nom de la clé à lire. Pour les mots clés réservés, consultez « Commentaires ». La valeur dans  *\*lpszAppName* doit être une chaîne se terminant par null.  
  
 *lpszString*  
 [Sortie] Pointeur vers la mémoire tampon de données contenant la chaîne associée à la clé à lire.  
  
 Si  *\*lpszFileName* est un nom de fichier .dsn valide mais le *lpszAppName* argument est un pointeur null et le *lpszKeyName* argument est un pointeur null, puis  *\*lpszString* contient une liste d’applications valides. Si  *\*lpszFileName* est un nom de fichier .dsn valide et  *\*lpszAppName* est un nom d’application valide, mais la *lpszKeyName* argument est une valeur null pointeur, puis  *\*lpszString* contient une liste de mots clés réservés valides dans la section appropriée du fichier DSN, séparée par des points-virgules. Si  *\*lpszFileName* est un nom de fichier .dsn valide mais  *\*lpszAppName* est un pointeur null et le *lpszKeyName* argument est un pointeur null, puis  *\*lpszString* contient une liste des sections dans le fichier de source de données, séparées par des points-virgules.  
  
 *cbString*  
 [Entrée] Longueur de la  *\*lpszString* mémoire tampon.  
  
 *pcbString*  
 [Sortie] Nombre total d’octets à retourner dans  *\*lpszString*. Si le nombre d’octets à retourner est supérieur ou égal à *cbString*, la chaîne de sortie dans  *\*lpszString* est tronqué à *cbString* moins le caractère de fin de null. Le *pcbString* argument peut être un pointeur null.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLReadFileDSN** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longueur de la mémoire tampon non valide|Le *lpszString* argument était NULL.<br /><br /> Le *cbString* argument était inférieur ou égal à 0.|  
|ODBC_ERROR_INVALID_PATH|Chemin d’installation non valide|Le chemin d’accès du nom de fichier spécifié dans le *lpszFileName* argument n’est pas valide.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Type de demande non valide|Le *lpszAppName* argument a la valeur NULL, alors que le *lpszKeyName* argument était valide.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
|ODBC_ERROR_OUTPUT_STRING_TRUNCATED|Chaîne de sortie tronquée|La chaîne retournée dans  *\*lpszString* a été tronqué, car la valeur de *cbString* était inférieur ou égal à la valeur de  *\*pcbString*.|  
|ODBC_ERROR_REQUEST_FAILED|Échoué de la demande|Le mot clé n’existait pas dans le fichier DSN.|  
  
## <a name="comments"></a>Commentaires  
 ODBC réserve le nom de la section [ODBC] dans lequel stocker les informations de connexion. Les mots clés réservés pour cette section sont les mêmes que celles réservées pour une chaîne de connexion dans **SQLDriverConnect**. (Pour plus d’informations, consultez le [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) description de fonction.)  
  
 Applications peuvent utiliser ces mots clés réservés pour lire les informations contenues dans un fichier DSN. Si une application souhaite savoir la chaîne de connexion sans DSN associée à une source de données de fichier, elle peut appeler **SQLReadFileDSN** pour un des mots-clés de chaîne de connexion réservé dans la section [ODBC]. La chaîne de connexion complète passée dans une connexion sans DSN est une combinaison de tous les mots clés (et non réservés spécifiques au pilote) dans la section [ODBC].  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Écriture d’informations dans un fichier DSN|[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|

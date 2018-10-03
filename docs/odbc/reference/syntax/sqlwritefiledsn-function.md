---
title: SQLWriteFileDSN, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b8c490da7ecfe0230eaad5f98da1c66293f99eb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758957"
---
# <a name="sqlwritefiledsn-function"></a>SQLWriteFileDSN, fonction
**Conformité**  
 Version introduite : ODBC 3.0  
  
 **Résumé**  
 **SQLWriteFileDSN** écrit les informations dans un fichier DSN.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL SQLWriteFileDSN(  
     LPCSTR     lpszFileName,  
     LPCSTR     lpszAppName,  
     LPCSTR     lpszKeyName,  
     LPCSTR     lpszString);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszFileName*  
 [Entrée] Pointeur vers le nom de la source de données de fichier. Une extension de source de données est ajoutée à tous les noms de fichier qui n’est pas déjà une extension de source de données.  
  
 *lpszAppName*  
 [Entrée] Pointeur vers le nom de l’application. Il s’agit « ODBC » pour la section ODBC.  
  
 *lpszKeyName*  
 [Entrée] Pointeur vers le nom de la clé à lire. Pour les mots clés réservés, consultez « Commentaires ».  
  
 *lpszString*  
 [Sortie] Vers lequel pointe la chaîne associée à la clé à écrire. La longueur maximale de la chaîne désignée par cet argument est de 32 767 octets.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLWriteFileDSN** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_INVALID_PATH|Chemin d’installation non valide|Le chemin d’accès du nom de fichier spécifié dans le *lpszFileName* argument n’est pas valide.|  
|ODBC_ERROR_INVALID_REQUEST_TYPE|Type de demande non valide|Le *lpszAppName*, *lpszKeyName*, ou *lpszString* argument était NULL.|  
  
## <a name="comments"></a>Commentaires  
 ODBC réserve le nom de la section [ODBC] dans lequel stocker les informations de connexion. Les mots clés réservés pour cette section sont les mêmes que celles réservées pour une chaîne de connexion dans **SQLDriverConnect**. (Pour plus d’informations, consultez le [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) description de fonction.)  
  
 Applications peuvent utiliser ces mots clés réservés pour écrire des informations directement dans un fichier DSN. Si une application veut créer ou modifier la chaîne de connexion sans DSN associée à une source de données de fichier, elle peut appeler **SQLWriteFileDSN** pour un des mots-clés de chaîne de connexion réservé dans la section [ODBC].  
  
 Si le *lpszString* argument est un pointeur null, le mot clé vers laquelle pointé le *lpszKeyName* argument est supprimé à partir du fichier .dsn. Si le *lpszString* et *lpszKeyName* arguments sont les deux pointeurs null, la section vers laquelle pointée le *lpszAppName* argument est supprimé à partir du fichier .dsn.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Lecture des informations à partir de sources de données fichier|[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|

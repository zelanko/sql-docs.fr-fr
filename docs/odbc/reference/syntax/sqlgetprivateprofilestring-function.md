---
title: FONCTION SQLGetPrivateProfileString (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetPrivateProfileString
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetPrivateProfileString
helpviewer_keywords:
- SQLGetPrivateProfileString function [ODBC]
ms.assetid: b72ca065-4d67-48df-baac-e18379a8320a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c12fc8d08535960cbb239c14e017b2ad5faa6c0e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303291"
---
# <a name="sqlgetprivateprofilestring-function"></a>SQLGetPrivateProfileString, fonction
**Conformité**  
 Version introduite: ODBC 2.0  
  
 **Résumé**  
 **SQLGetPrivateProfileString** obtient une liste de noms de valeurs ou de données correspondant à une valeur de l’information du système.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
int SQLGetPrivateProfileString(  
     LPCSTR   lpszSection,  
     LPCSTR   lpszEntry,  
     LPCSTR   lpszDefault,  
     LPCSTR   RetBuffer,  
     INT      cbRetBuffer,  
     LPCSTR   lpszFilename);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszSection*  
 [Entrée] Indique une chaîne non terminée qui spécifie la section contenant le nom clé. Si cet argument est NULL, la fonction copie tous les noms de section dans le fichier au tampon fourni.  
  
 *lpszEntry (en)*  
 [Entrée] Points à la chaîne non terminée contenant le nom clé dont la chaîne associée doit être récupérée. Si cet argument est NULL, tous les noms clés de la section spécifiée par *l’argument de lpszSection* sont copiés sur le tampon spécifié par l’argument de *RetBuffer.*  
  
 *lpszDefault*  
 [Entrée] Indique une chaîne non résiliée qui précise la valeur par défaut de la clé donnée si la clé ne peut pas être trouvée dans le fichier de initialisation. Cet argument ne peut pas avoir la valeur null.  
  
 *RetBuffer (RetBuffer)*  
 [Sortie] Points vers le tampon qui reçoit la chaîne récupérée.  
  
 *cbRetBuffer*  
 [Entrée] Spécifie la taille, dans les caractères, de la mémoire tampon pointée par l’argument de *RetBuffer.*  
  
 *lpszFilename*  
 [Entrée] Indique une chaîne non terminée qui nomme le fichier d’initialisation. Si cet argument ne contient pas un chemin complet vers le fichier, l’annuaire par défaut est recherché.  
  
## <a name="returns"></a>Retours  
 **SQLGetPrivateProfileString** retourne une valeur integer qui indique le nombre de caractères lus.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsqu’un appel à **SQLGetPrivateProfileString** échoue, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLGetPrivateProfileString** est fourni comme un moyen simple pour les pilotes de port et d’installation du conducteur DLLs de Microsoft® Windows® à Microsoft Windows NT®/Windows 2000. Les appels vers **GetPrivateProfileString** qui récupèrent une chaîne de profil du fichier Odbc.ini doivent être remplacés par des appels à **SQLGetPrivateProfileString**. **SQLGetPrivateProfileString** appelle des fonctions dans l’API de ® WinLGetPrivate Pour récupérer les noms demandés de valeurs ou de données correspondant à une valeur de la sous-clé Odbc.ini des informations du système.  
  
 Le mode de configuration (tel qu’il est défini par **SQLSetConfigMode**) indique où les valeurs DSN de liste odbc.ini sont dans l’information du système. Si le DSN est un DSN utilisateur (le mode de configuration est USERDSN_ONLY), la fonction se lit à partir de l’entrée Odbc.ini dans HKEY_CURRENT_USER. Si le DSN est un DSN système (SYSTEMDSN_ONLY), la fonction se lit à partir de l’entrée Odbc.ini dans HKEY_LOCAL_MACHINE. Si le mode de configuration est BOTHDSN, HKEY_CURRENT_USER est essayé, et s’il échoue, HKEY_LOCAL_MACHINE est utilisé.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Rédaction d’une valeur pour l’information du système|[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|

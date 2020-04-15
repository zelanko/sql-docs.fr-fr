---
title: Fonction SQLPostInstallerError (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPostInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPostInstallerError
helpviewer_keywords:
- SQLPostInstallerError function [ODBC]
ms.assetid: 4c60d827-b2d2-4f27-b220-daa9e1fcdd8d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cdceff5c4e175ba9f135c6e5e4405933b1a86b7c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306890"
---
# <a name="sqlpostinstallererror-function"></a>SQLPostInstallerError, fonction
**Conformité**  
 Version introduite: ODBC 3.0  
  
 **Résumé**  
 **SQLPostInstallerError** fournit un mécanisme pour un conducteur ou une bibliothèque d’installation de traducteur pour signaler les erreurs pour le **ConfigDriver**, **ConfigDSN**, et **les fonctions ConfigTranslator** à la file d’attente d’erreur d’installateur. Les applications n’utilisent pas cette API; ils utilisent **SQLInstallerError** pour récupérer l’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>Arguments  
 *code fError*  
 [Entrée] Code d’erreur d’installateur.  
  
 *szErrorMsg*  
 [Entrée] Texte de message d’erreur.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS ou SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnostics  
 **SQLPostInstallerError** ne poste pas de valeurs d’erreur pour lui-même. Si l’erreur a été postée avec succès sur la file d’attente d’erreur de l’installateur (récupérable à l’aide **de SQLInstallerError),** SQL_SUCCESS est retournée. SQL_ERROR sera retourné si la valeur de *l’argument dwErrorCode* n’est pas l’un des codes d’erreur spécifiés.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’un conducteur|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)|  
|Ajout, modification ou suppression de sources de données|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Définir une option de traduction|[ConfigTranslateur](../../../odbc/reference/syntax/configtranslator-function.md)|

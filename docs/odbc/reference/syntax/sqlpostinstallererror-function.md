---
title: SQLPostInstallerError fonction) | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306890"
---
# <a name="sqlpostinstallererror-function"></a>SQLPostInstallerError, fonction
**Conformité**  
 Version introduite : ODBC 3,0  
  
 **Résumé**  
 **SQLPostInstallerError** fournit un mécanisme permettant à une bibliothèque de configuration de pilote ou de traducteur de signaler les erreurs des fonctions **ConfigDriver**, **ConfigDSN**et **ConfigTranslator** à la file d’attente des erreurs du programme d’installation. Les applications n’utilisent pas cette API ; ils utilisent **SQLInstallerError** pour récupérer l’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>Arguments  
 *fErrorCode*  
 Entrée Code d’erreur du programme d’installation.  
  
 *szErrorMsg*  
 Entrée Texte du message d’erreur.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS ou SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnostics  
 **SQLPostInstallerError** ne publie pas de valeurs d’erreur pour lui-même. Si l’erreur a été publiée avec succès dans la file d’attente des erreurs du programme d’installation (récupérables à l’aide de **SQLInstallerError**), SQL_SUCCESS est retourné. SQL_ERROR est retourné si la valeur de l’argument *dwErrorCode* n’est pas l’un des codes d’erreur du programme d’installation spécifiés.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’un pilote|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)|  
|Ajout, modification ou suppression de sources de données|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Définition d’une option de traduction|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|

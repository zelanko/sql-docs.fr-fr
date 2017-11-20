---
title: Fonction de SQLPostInstallerError | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f7d3a6bec7c12e271c073d5665c0a4e9b227ceef
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlpostinstallererror-function"></a>SQLPostInstallerError (fonction)
**Mise en conformité**  
 Version introduite : ODBC 3.0  
  
 **Résumé**  
 **SQLPostInstallerError** fournit un mécanisme pour une bibliothèque du programme d’installation de pilote ou de convertisseur pour signaler les erreurs pour le **ConfigDriver**, **ConfigDSN**, et **ConfigTranslator** fonctions à la file d’attente des erreurs de programme d’installation. Applications n’utilisent pas cette API ; ils utilisent **SQLInstallerError** pour récupérer l’erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>Arguments  
 *fErrorCode*  
 [Entrée] Code d’erreur de programme d’installation.  
  
 *szErrorMsg*  
 [Entrée] Texte de message d’erreur.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS ou SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnostics  
 **SQLPostInstallerError** ne publie pas de valeurs d’erreur pour lui-même. Si l’erreur a été correctement envoyée à la file d’attente des erreurs de programme d’installation (récupérables à l’aide de **SQLInstallerError**), valeur SQL_SUCCESS est retournée. SQL_ERROR est retournée si la valeur de la *dwErrorCode* argument n’est pas un des codes d’erreur de programme d’installation spécifié.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’un pilote|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)|  
|Ajout, modification ou suppression de sources de données|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|Définition d’une option de traduction|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|


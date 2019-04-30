---
title: Sqlgetconfigmode, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConfigMode
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConfigMode
helpviewer_keywords:
- SQLGetConfigMode function [ODBC]
ms.assetid: b96ab3b8-08d5-4fea-9ffe-e03043efbf2d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 54c8dbed5599952778ca7651acbdb55a21b8f876
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63259288"
---
# <a name="sqlgetconfigmode-function"></a>SQLGetConfigMode, fonction
**Conformité**  
 Version introduite : ODBC 3.0  
  
 **Résumé**  
 **SQLGetConfigMode** récupère le mode de configuration qui indique où l’entrée de fichier Odbc.ini répertoriant les valeurs de la source de données est dans les informations système.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>Arguments  
 *pwConfigMode*  
 [Sortie] Pointeur vers la mémoire tampon contenant le mode de configuration. (Voir « Commentaires ».) La valeur dans  *\*pwConfigMode* peut être :  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetConfigMode** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 Cette fonction est utilisée pour déterminer où se trouve l’entrée du fichier Odbc.ini répertoriant les valeurs de la source de données dans les informations système. Si  *\*pwConfigMode* est ODBC_USER_DSN, la source de données est une source de données utilisateur et la fonction lit à partir de l’entrée de fichier Odbc.ini dans HKEY_CURRENT_USER. Si elle est ODBC_SYSTEM_DSN, la source de données est une source de données système et la fonction lit à partir de l’entrée de fichier Odbc.ini dans HKEY_LOCAL_MACHINE. Si elle est ODBC_BOTH_DSN, HKEY_CURRENT_USER est tentée, et si elle échoue, HKEY_LOCAL_MACHINE est utilisée.  
  
 Par défaut, **SQLGetConfigMode** retourne ODBC_BOTH_DSN. Création d’un DSN utilisateur ou une source de données système par un appel à **SQLConfigDataSource**, la fonction définit le mode de configuration ODBC_USER_DSN ou ODBC_SYSTEM_DSN pour distinguer les sources de données système et utilisateur lors de la modification d’une source de données. Avant de retourner, **SQLConfigDataSource** ODBC_BOTH_DSN rétablit le mode de configuration.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Définition du mode de configuration|[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|

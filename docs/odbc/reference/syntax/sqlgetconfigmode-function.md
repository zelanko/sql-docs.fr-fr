---
title: Fonction de SQLGetConfigMode | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d52a471de1590df140f766a417820126ac191f77
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetconfigmode-function"></a>SQLGetConfigMode (fonction)
**Mise en conformité**  
 Version introduite : ODBC 3.0  
  
 **Résumé**  
 **SQLGetConfigMode** récupère le mode de configuration qui indique l’entrée du fichier Odbc.ini répertoriant les valeurs de la source de données dans les informations système.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL SQLGetConfigMode(  
     UWORD *   pwConfigMode);  
```  
  
## <a name="arguments"></a>Arguments  
 *pwConfigMode*  
 [Sortie] Pointeur vers la mémoire tampon contenant le mode de configuration. (Voir « Commentaires ».) La valeur de * \*pwConfigMode* peut être :  
  
 ODBC_USER_DSN  
  
 ODBC_SYSTEM_DSN  
  
 ODBC_BOTH_DSN  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne TRUE si l’opération a réussi, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetConfigMode** renvoie la valeur FALSE, associé à un * \*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*pfErrorCode* les valeurs qui peuvent être retournées par **SQLInstallerError** et explique chacune d’elles dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Erreur| Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 Cette fonction est utilisée pour déterminer l’emplacement de l’entrée du fichier Odbc.ini répertoriant les valeurs de la source de données dans les informations système. Si * \*pwConfigMode* est ODBC_USER_DSN, la source de données est une source de données utilisateur et la fonction lit à partir de l’entrée de fichier Odbc.ini dans HKEY_CURRENT_USER. S’il s’agit de ODBC_SYSTEM_DSN, la source de données est une source de données système et la fonction lit à partir de l’entrée de fichier Odbc.ini dans HKEY_LOCAL_MACHINE. S’il s’agit de ODBC_BOTH_DSN, HKEY_CURRENT_USER est tentée, et en cas d’échec, HKEY_LOCAL_MACHINE est utilisé.  
  
 Par défaut, **SQLGetConfigMode** retourne ODBC_BOTH_DSN. Lorsqu’un DSN utilisateur ou une source de données système est créé par un appel à **SQLConfigDataSource**, la fonction définit le mode de configuration ODBC_USER_DSN ou ODBC_SYSTEM_DSN pour distinguer les sources de données système et utilisateur lors de la modification d’une source de données. Avant de retourner, **SQLConfigDataSource** ODBC_BOTH_DSN rétablit le mode de configuration.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Définition du mode de configuration|[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|

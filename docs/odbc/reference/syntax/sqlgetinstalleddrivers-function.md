---
title: Fonction SQLGetGetstalledDrivers (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetInstalledDrivers
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetInstalledDrivers
helpviewer_keywords:
- SQLGetInstalledDrivers function [ODBC]
ms.assetid: a1983a2e-0edf-422e-bd1b-ec5db40a34bc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 24793473bf4f25253ac11673df852d10cfb2c558
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303326"
---
# <a name="sqlgetinstalleddrivers-function"></a>SQLGetInstalledDrivers, fonction
**Conformité**  
 Version introduite: ODBC 1.0  
  
 **Résumé**  
 **SQLGetInstalledDrivers** lit la section [ODBC Drivers] de l’information du système et renvoie une liste de descriptions des pilotes installés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLGetInstalledDrivers(  
     LPSTR   lpszBuf,  
     WORD    cbBufMax,  
     WORD *  pcbBufOut);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszBuf (lpszBuf)*  
 [Sortie] Liste des descriptions des pilotes installés. Pour plus d’informations sur la structure de la liste, voir « Commentaires ».  
  
 *cbBufMax (en)*  
 [Entrée] Longueur de *lpszBuf*.  
  
 *pcbBufOut*  
 [Sortie] Nombre total d’octets (à l’exclusion du octet de cessation d’emploi nul) retournés en *lpszBuf*. Si le nombre d’octets disponibles pour revenir est supérieur ou égal à *cbBufMax*, la liste des descriptions de pilote dans *lpszBuf* est tronquée à *cbBufMax* moins le caractère de non-termination. *L’argument pcbBufOut* peut être un pointeur nul.  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetInstalledDrivers** retourne FALSE, une valeur * \*pfErrorCode* associée peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur d’installateur général|Une erreur s’est produite pour laquelle il n’y a pas eu d’erreur spécifique d’installateur.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longueur tampon invalide|*L’argument de lpszBuf* était NULL ou invalide, ou l’argument *cbBufMax* était inférieur ou égal à 0.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Composant non trouvé dans le registre|L’installateur n’a pas trouvé la section [des conducteurs de l’ODBC] dans le registre.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|L’installateur ne pouvait pas effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 Chaque description du conducteur est terminée avec un byte nul, et la liste complète est terminée avec un byte nul. (C’est-à-dire que deux octets nuls marquent la fin de la liste.) Si le tampon alloué n’est pas assez grand pour contenir la liste entière, la liste est tronquée sans erreur. Une erreur est retournée si un pointeur nul est passé en tant que *lpszBuf*.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Retour des descriptions et attributs des conducteurs|[SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|

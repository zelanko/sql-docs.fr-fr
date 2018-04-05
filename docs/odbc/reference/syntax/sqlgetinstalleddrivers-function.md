---
title: Fonction de SQLGetInstalledDrivers | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 64b8479b23f76c8af74be77b4f44e3bca6f8a6f6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetinstalleddrivers-function"></a>SQLGetInstalledDrivers (fonction)
**Mise en conformité**  
 Version introduite : ODBC 1.0  
  
 **Résumé**  
 **SQLGetInstalledDrivers** lit la section [ODBC Drivers] les informations système et retourne une liste des descriptions des pilotes installés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL SQLGetInstalledDrivers(  
     LPSTR   lpszBuf,  
     WORD    cbBufMax,  
     WORD *  pcbBufOut);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszBuf*  
 [Sortie] Liste des descriptions des pilotes installés. Pour plus d’informations sur la structure de la liste, consultez « Commentaires ».  
  
 *cbBufMax*  
 [Entrée] Longueur de *lpszBuf*.  
  
 *pcbBufOut*  
 [Sortie] Nombre total d’octets (à l’exception de l’octet de fin de null) retournée dans *lpszBuf*. Si le nombre d’octets à retourner est supérieur ou égal à *cbBufMax*, la liste des descriptions de pilote dans *lpszBuf* est tronqué à *cbBufMax* moins le caractère de fin de la valeur null. Le *pcbBufOut* argument peut être un pointeur null.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne TRUE si l’opération a réussi, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetInstalledDrivers** renvoie la valeur FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournées par **SQLInstallerError** et explique chacune d’elles dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générales|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longueur de la mémoire tampon non valide|Le *lpszBuf* argument était NULL ou non valide, ou le *cbBufMax* argument était inférieur ou égal à 0.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Composant introuvable dans le Registre|Le programme d’installation n’a pas trouvé la section [ODBC Drivers] dans le Registre.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 Description de chaque pilote se termine par un octet null, et la liste entière se termine par un octet null. (Autrement dit, deux octets null marquent la fin de la liste.) Si la mémoire tampon allouée n’est pas suffisamment grande pour contenir l’intégralité de la liste, la liste est tronquée sans erreur. Une erreur est retournée si un pointeur null est passé comme *lpszBuf*.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Renvoi de descriptions de pilote et attributs|[SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|

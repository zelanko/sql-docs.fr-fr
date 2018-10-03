---
title: Sqlgetinstalleddrivers, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 093da37d061153013682772c3284e0afe88b7866
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47618937"
---
# <a name="sqlgetinstalleddrivers-function"></a>SQLGetInstalledDrivers, fonction
**Conformité**  
 Version introduite : ODBC 1.0  
  
 **Résumé**  
 **SQLGetInstalledDrivers** lit la section [ODBC Drivers] des informations système et retourne une liste de descriptions des pilotes installés.  
  
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
 [Sortie] Nombre total d’octets (à l’exception de l’octet de caractère nul de terminaison) retournée dans *lpszBuf*. Si le nombre d’octets à retourner est supérieur ou égal à *cbBufMax*, la liste des descriptions de pilote dans *lpszBuf* est tronqué à *cbBufMax* moins le caractère du caractère nul de terminaison. Le *pcbBufOut* argument peut être un pointeur null.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetInstalledDrivers** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longueur de la mémoire tampon non valide|Le *lpszBuf* argument était NULL ou non valides, ou le *cbBufMax* argument était inférieur ou égal à 0.|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|Composant introuvable dans le Registre|Le programme d’installation n’a pas pu trouver la section [ODBC Drivers] dans le Registre.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 Description de chaque pilote se termine par un octet null, et la liste entière se termine par un octet null. (Autrement dit, deux octets null marquent la fin de la liste.) Si la mémoire tampon allouée n’est pas suffisamment grande pour contenir l’intégralité de la liste, la liste est tronquée sans erreur. Une erreur est retournée si un pointeur null est passé en tant que *lpszBuf*.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Renvoi de descriptions de pilote et attributs|[SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|

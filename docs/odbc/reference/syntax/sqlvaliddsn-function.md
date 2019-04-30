---
title: SQLValidDSN Function | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLValidDSN
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLValidDSN
helpviewer_keywords:
- SQLValidDSN [ODBC]
ms.assetid: 930d1d89-337a-4429-85a2-84ee10555ac9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fb490b475c5795125d11915729693eb630934eb8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63233487"
---
# <a name="sqlvaliddsn-function"></a>SQLValidDSN, fonction
**Conformité**  
 Version introduite : ODBC 2.0  
  
 **Résumé**  
 **SQLValidDSN** la longueur et la validité du nom de source de données sont vérifiées avant que le nom est ajouté aux informations système.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
BOOL SQLValidDSN(  
     LPCSTR    lpszDSN);  
```  
  
## <a name="arguments"></a>Arguments  
 *lpszDSN*  
 [Entrée] Source de données à vérifier.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne TRUE si le nom de source de données est valide. Elle retourne FALSE si le nom de source de données n’est pas valide ou l’appel de fonction a échoué.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLValidDSN** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Un  *\*pfErrorCode* est retourné uniquement si l’appel de fonction échoue, pas si la valeur FALSE est retournée, car le nom de source de données n’est pas valide. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 **SQLValidDSN** est appelée par un chauffeur [ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) pour vérifier la longueur du nom de source de données et la validité des caractères individuels dans le nom de source de données. Il vérifie si la longueur du nom est supérieure à SQL_MAX_DSN_LENGTH, tel que défini dans Sqlext.h. (La longueur du nom de source de données est également vérifiée par [SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md).) **SQLValidDSN** vérifie si un des caractères non valides suivants sont inclus dans le nom de source de données :  
  
 [ ] { } ( ) , ; ? * = ! \@ \  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Ajout, modification ou suppression d’une source de données|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md) (dans la DLL d’installation)|  
|Ajout, modification ou suppression d’une source de données|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|  
|Écriture d’un nom de source de données dans les informations système|[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|

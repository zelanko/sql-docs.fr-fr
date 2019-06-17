---
title: ConfigTranslator, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- ConfigTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- ConfigTranslator
helpviewer_keywords:
- ConfigTranslator [ODBC]
ms.assetid: 7c22f07e-36de-425b-aa67-e32a84afae92
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0b56a5ebd0ad00e2c3abb87b72d2de8735245f99
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537977"
---
# <a name="configtranslator-function"></a>ConfigTranslator, fonction
**Conformité**  
 Version introduite : ODBC 2.0  
  
 **Résumé**  
 **ConfigTranslator** renvoie une option de traduction par défaut pour un traducteur. Il peut être dans le traducteur de DLL ou d’une DLL d’installation distinct.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL ConfigTranslator(  
     HWND     hwndParent,  
     DWORD *  pvOption);  
```  
  
## <a name="arguments"></a>Arguments  
 *hwndParent*  
 [Entrée] Handle de fenêtre parente. La fonction n’affichera pas les boîtes de dialogue si le handle est null.  
  
 *pvOption*  
 [Sortie] Une option de traduction de 32 bits.  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne la valeur TRUE si elle réussit, FALSE en cas d’échec.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **ConfigTranslator** retourne FALSE, associé à un  *\*pfErrorCode* valeur est publiée dans le tampon d’erreur de programme d’installation par un appel à **SQLPostInstallerError**et peut être obtenu en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Handle de fenêtre non valide|Le *hwndParent* argument était non valide ou NULL.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Erreur spécifique du pilote ou du traducteur|Une erreur spécifique au pilote pour lesquels il n’existe aucune erreur de programme d’installation ODBC défini. Le *SzError* argument dans un appel à la **SQLPostInstallerError** (fonction) doit contenir le message d’erreur spécifique au pilote.|  
|ODBC_ERROR_INVALID_OPTION|Option de conversion non valide|Le *pvOption* argument contenue une valeur non valide.|  
  
## <a name="comments"></a>Commentaires  
 Si le convertisseur prend en charge uniquement une option de traduction unique, **ConfigTranslator** retourne la valeur TRUE et définit *pvOption* à l’option 32 bits. Sinon, il détermine l’option de traduction par défaut à utiliser. **ConfigTranslator** peut afficher une boîte de dialogue avec laquelle un utilisateur sélectionne une option de traduction par défaut.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Obtention d’une option de traduction|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|En sélectionnant un traducteur|[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Définition d’une option de traduction|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|

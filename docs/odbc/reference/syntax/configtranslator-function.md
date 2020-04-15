---
title: Fonction ConfigTranslator (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fb2f26f87854d74a217885010014633963472787
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306030"
---
# <a name="configtranslator-function"></a>ConfigTranslator, fonction
**Conformité**  
 Version introduite: ODBC 2.0  
  
 **Résumé**  
 **ConfigTranslator** retourne une option de traduction par défaut pour un traducteur. Il peut être dans le traducteur DLL ou une configuration séparée DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL ConfigTranslator(  
     HWND     hwndParent,  
     DWORD *  pvOption);  
```  
  
## <a name="arguments"></a>Arguments  
 *hwndParent*  
 [Entrée] Poignée de fenêtre de parent. La fonction n’affichera pas de boîtes de dialogue si la poignée est nulle.  
  
 *pvOption*  
 [Sortie] Une option de traduction 32 bits.  
  
## <a name="returns"></a>Retours  
 La fonction retourne VRAI si elle est réussie, FALSE si elle échoue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **ConfigTranslator** retourne FALSE, une valeur * \*pfErrorCode* associée est affichée sur le tampon d’erreur de l’installateur par un appel à **SQLPostInstallerError** et peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les * \*valeurs pfErrorCode* qui peuvent être retournées par **SQLInstallerError** et explique chacune dans le cadre de cette fonction.  
  
|*\*pfErrorCode (en)*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_INVALID_HWND|Poignée de fenêtre invalide|*L’argument de hwndParent* était invalide ou NULL.|  
|ODBC_ERROR_DRIVER_SPECIFIC|Erreur spécifique au conducteur ou au traducteur|Une erreur spécifique au conducteur pour laquelle il n’y a pas d’erreur d’installateur ODBC définie. *L’argument de SzError* dans un appel à la fonction **SQLPostInstallerError** devrait contenir le message d’erreur spécifique au conducteur.|  
|ODBC_ERROR_INVALID_OPTION|Option de traduction invalide|*L’argument de l’pvOption* contenait une valeur invalide.|  
  
## <a name="comments"></a>Commentaires  
 Si le traducteur ne prend en charge qu’une seule option de traduction, **ConfigTranslator** renvoie TRUE et définit *pvOption* à l’option 32 bits. Dans le cas contraire, il détermine l’option de traduction par défaut à utiliser. **ConfigTranslator** peut afficher une boîte de dialogue avec laquelle un utilisateur sélectionne une option de traduction par défaut.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Obtenir une option de traduction|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Sélection d’un traducteur|[SQLGetTranslator (SQLGetTranslator)](../../../odbc/reference/syntax/sqlgettranslator-function.md)|  
|Définir une option de traduction|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|

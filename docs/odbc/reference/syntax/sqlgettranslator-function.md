---
title: Sqlgettranslator, fonction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetTranslator
helpviewer_keywords:
- SQLGetTranslator function [ODBC]
ms.assetid: 33879db3-5ef9-4585-9be5-69376157e017
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 948fc36da520777812c02e6e5d52a423eb9cc288
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65536549"
---
# <a name="sqlgettranslator-function"></a>SQLGetTranslator, fonction
**Conformité**  
 Version introduite : ODBC 2.0  
  
 **Résumé**  
 **SQLGetTranslator** affiche une boîte de dialogue à partir de laquelle un utilisateur peut sélectionner un traducteur.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
BOOL SQLGetTranslator(  
     HWND      hwndParent,  
     LPSTR     lpszName,  
     WORD      cbNameMax,  
     WORD *    pcbNameOut,  
     LPSTR     lpszPath,  
     WORD      cbPathMax,  
     WORD *    pcbPathOut,  
     DWORD *   pvOption);  
```  
  
## <a name="arguments"></a>Arguments  
 *hwndParent*  
 [Entrée] Handle de fenêtre parente.  
  
 *lpszName*  
 [Entrée/sortie] Nom de la traduction à partir des informations système.  
  
 *cbNameMax*  
 [Entrée] Longueur maximale de la *le caractère* mémoire tampon.  
  
 *pcbNameOut*  
 [Entrée/sortie] Nombre total d’octets (à l’exception de l’octet de caractère nul de terminaison) passées ou retournées dans *le caractère*. Si le nombre d’octets à retourner est supérieur ou égal à *cbNameMax*, le nom du traducteur dans *le caractère* est tronqué à *cbNameMax* moins le caractère du caractère nul de terminaison. Le *pcbNameOut* argument peut être un pointeur null.  
  
 *lpszPath*  
 [Sortie] Chemin d’accès complet de la DLL de traduction.  
  
 *cbPathMax*  
 [Entrée] Longueur maximale de la *lpszPath* mémoire tampon.  
  
 *pcbPathOut*  
 [Sortie] Nombre total d’octets (à l’exception de l’octet de caractère nul de terminaison) retournée dans *lpszPath*. Si le nombre d’octets à retourner est supérieur ou égal à *cbPathMax*, le chemin d’accès DLL de traduction dans *lpszPath* est tronqué à *cbPathMax* moins le caractère du caractère nul de terminaison. Le *pcbPathOut* argument peut être un pointeur null.  
  
 *pvOption*  
 Option de traduction de 32 bits de [sortie].  
  
## <a name="returns"></a>Valeur renvoyée  
 La fonction retourne TRUE si elle est réussie, FALSE en cas d’échec ou si l’utilisateur annule la boîte de dialogue.  
  
## <a name="diagnostics"></a>Diagnostics  
 Lorsque **SQLGetTranslator** retourne FALSE, associé à un  *\*pfErrorCode* valeur peut être obtenue en appelant **SQLInstallerError**. Le tableau suivant répertorie les  *\*pfErrorCode* les valeurs qui peuvent être retournés par **SQLInstallerError** et explique chacune dans le contexte de cette fonction.  
  
|*\*pfErrorCode*|Error|Description|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|Erreur du programme d’installation générale|Une erreur s’est produite pour lequel aucune erreur d’installation spécifique s’est produite.|  
|ODBC_ERROR_INVALID_BUFF_LEN|Longueur de la mémoire tampon non valide|Le *cbNameMax* ou *cbPathMax* argument était inférieur ou égal à 0.|  
|ODBC_ERROR_INVALID_HWND|Handle de fenêtre non valide|Le *hwndParent* argument était non valide ou NULL.|  
|ODBC_ERROR_INVALID_NAME|Nom de pilote ou de convertisseur non valide|Le *le caractère* argument n’est pas valide. Il est introuvable dans le Registre.|  
|ODBC_ERROR_LOAD_LIBRARY_FAILED|Impossible de charger la bibliothèque le programme d’installation de pilote ou de convertisseur|La bibliothèque de traducteur n’a pas pu être chargée.|  
|ODBC_ERROR_INVALID_OPTION|Option de transaction non valide|Le *pvOption* argument contenue une valeur non valide.|  
|ODBC_ERROR_OUT_OF_MEM|Mémoire insuffisante|Le programme d’installation n’a pas pu effectuer la fonction en raison d’un manque de mémoire.|  
  
## <a name="comments"></a>Commentaires  
 Si *hwndParent* a la valeur null ou si *le caractère*, *lpszPath*, ou *pvOption* est un pointeur null, **SQLGetTranslator** retourne FALSE. Sinon, elle affiche la liste des convertisseurs installés dans la boîte de dialogue suivante.  
  
 ![Boîte de dialogue Sélectionnez Translator](../../../odbc/reference/syntax/media/ch23j.gif "CH23J")  
  
 Si *le caractère* contient un nom valide translator, il est sélectionné. Sinon, \<pas de convertisseur > est sélectionné.  
  
 Si l’utilisateur choisit \<pas de convertisseur >, le contenu de *le caractère*, *lpszPath*, et *pvOption* ne sont pas touchées. **SQLGetTranslator** définit *pcbNameOut* et *pcbPathOut* à 0 et retourne la valeur TRUE.  
  
 Si l’utilisateur choisit un traducteur, **SQLGetTranslator** appels **ConfigTranslator** dans la DLL d’installation du traducteur. Si **ConfigTranslator** retourne FALSE, **SQLGetTranslator** retourne à sa boîte de dialogue. Si **ConfigTranslator** retourne la valeur TRUE, **SQLGetTranslator** renvoie TRUE, ainsi que l’option de nom, chemin d’accès et une traduction translator sélectionné.  
  
## <a name="related-functions"></a>Fonctions connexes  
  
|Pour obtenir des informations sur|Consultez|  
|---------------------------|---------|  
|Configuration d’un traducteur|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|  
|Obtention d’un attribut de traduction|[SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|Définition d’un attribut de traduction|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|

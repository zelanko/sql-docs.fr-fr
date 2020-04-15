---
title: Fonction SQLInstallerError (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLInstallerError
helpviewer_keywords:
- SQLInstallerError [ODBC]
ms.assetid: e6474b79-4d55-458f-81ce-abfafe357f83
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e749237cf87c5054b8273f38531d9336d316e040
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302100"
---
# <a name="sqlinstallererror-function"></a>SQLInstallerError, fonction
**Conformité**  
 Version introduite: ODBC 3.0  
  
 **Résumé**  
 **SQLInstallerError renvoie** des informations d’erreur ou d’état pour les fonctions d’installateur ODBC.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
  
RETCODE SQLInstallerError(  
     WORD      iError,  
     DWORD *   pfErrorCode,  
     LPSTR     lpszErrorMsg,  
     WORD      cbErrorMsgMax,  
     WORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>Arguments  
 *iError (en)*  
 [Entrée] Numéro d’enregistrement d’erreur. Les numéros valides sont de 1 à 8.  
  
 *pfErrorCode (en)*  
 [Sortie] Code d’erreur d’installateur. (Pour plus d’informations, voir "Commentaires.")  
  
 *lpszErrorMsg*  
 [Sortie] Pointeur au stockage pour le texte de message d’erreur.  
  
 *cbErrorMsgMax*  
 [Entrée] Longueur maximale du tampon *szErrorMsg.* Cela doit être inférieur ou égal à SQL_MAX_MESSAGE_LENGTH moins le caractère de résiliation nulle.  
  
 *cbErrorMsgMax*  
 [Entrée] Longueur maximale du tampon *szErrorMsg.* Cela doit être inférieur ou égal à SQL_MAX_MESSAGE_LENGTH moins le caractère de résiliation nulle.  
  
 *pcbErrorMsg*  
 [Sortie] Pointeur sur le nombre total d’octets (à l’exclusion du caractère de résiliation nulle) disponible pour revenir en *lpszErrorMsg*. Si le nombre d’octets disponibles pour revenir est supérieur ou égal à *cbErrorMsgMax*, le texte de message *d’erreur dans lpszErrorMsg* est tronqué à *cbErrorMsgMax* moins les octets caractère de non-termination. *L’argument pcbErrorMsg* peut être un pointeur nul.  
  
## <a name="returns"></a>Retours  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA ou SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnostics  
 **SQLInstallerError** ne poste pas de valeurs d’erreur pour lui-même. **SQLInstallerError** retourne SQL_NO_DATA lorsqu’il n’est pas en mesure de récupérer des informations d’erreur (auquel cas *pfErrorCode* n’est pas défini). Si **SQLInstallerError** ne peut pas accéder aux valeurs d’erreur pour une raison qui reviendrait normalement SQL_ERROR, **SQLInstallerError** retourne SQL_ERROR mais ne affiche aucune valeur d’erreur. Si vous ne connaissez pas la longueur de la chaîne d’avertissement (*lpszErrorMsg*), vous pouvez définir *lpszErrorMsg* à NULL et appeler **SQLInstallerError**. **SQLInstallerError** retournera ensuite la longueur de la chaîne d’avertissement en *cbErrorMsgMax*. Si le tampon pour le message d’erreur est trop court, **SQLInstallerError** retourne SQL_SUCCESS_WITH_INFO et renvoie la valeur *pfErrorCode* correcte pour **SQLInstallerError**.  
  
 Pour déterminer si une troncation s’est produite dans le message d’erreur, une application peut comparer la valeur de *l’argument cbErrorMsgMax* à la longueur réelle du texte du message écrit à *l’argument pcbErrorMsg.* Si la troncation se produit, la longueur tampon correcte doit être allouée pour *lpszErrorMsg* et **SQLInstallerError** devrait être appelé à nouveau avec l’enregistrement *iError* correspondant.  
  
## <a name="comments"></a>Commentaires  
 Une application appelle **SQLInstallerError** lorsqu’un appel précédent à la fonction d’installateur ODBC renvoie FALSE. ODBC installateur et pilote ou traducteur fonctions de configuration post zéro ou plus erreurs que lorsque la fonction échoue (retours FALSE); par conséquent, une application appelle **SQLInstallerError** seulement après une fonction d’installateur ODBC échoue.  
  
 La file d’attente d’erreur d’installateur D’ODBC est rincée chaque fois qu’une nouvelle fonction d’installateur est appelée. Par conséquent, une application ne peut pas s’attendre à récupérer des erreurs pour des fonctions autres que du dernier appel de fonction installateur.  
  
 Pour récupérer plusieurs erreurs pour un appel de fonction, une application appelle **SQLInstallerError** plusieurs fois.  
  
 Lorsqu’il n’y a pas d’information supplémentaire, **SQLInstallerError** retourne SQL_NO_DATA, l’argument *pfErrorCode* n’est pas défini, *l’argument pcbErrorMsg* est égal à 0, et *l’argument lpszErrorMsg* contient un seul caractère de non-termination (à moins que *l’argument cbErrorMsgMax* est égal à 0).

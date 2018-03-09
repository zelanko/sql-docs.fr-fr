---
title: Fonction de SQLInstallerError | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLInstallerError
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLInstallerError
helpviewer_keywords: SQLInstallerError [ODBC]
ms.assetid: e6474b79-4d55-458f-81ce-abfafe357f83
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c3cdc3ae1e4efe4292077851a4f457bae4af17bd
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlinstallererror-function"></a>SQLInstallerError (fonction)
**Mise en conformité**  
 Version introduite : ODBC 3.0  
  
 **Résumé**  
 **SQLInstallerError** retourne des informations d’erreur ou d’état pour les fonctions du programme d’installation ODBC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE SQLInstallerError(  
     WORD      iError,  
     DWORD *   pfErrorCode,  
     LPSTR     lpszErrorMsg,  
     WORD      cbErrorMsgMax,  
     WORD *    pcbErrorMsg);  
```  
  
## <a name="arguments"></a>Arguments  
 *IErreur*  
 [Entrée] Erreur numéro d’enregistrement. Les nombres valides sont compris entre 1 et 8.  
  
 *pfErrorCode*  
 [Sortie] Code d’erreur de programme d’installation. (Pour plus d’informations, consultez « Commentaires ».)  
  
 *lpszErrorMsg*  
 [Sortie] Pointeur vers le stockage pour le texte du message.  
  
 *cbErrorMsgMax*  
 [Entrée] Longueur maximale de la *szErrorMsg* mémoire tampon. Il doit être inférieur ou égal à SQL_MAX_MESSAGE_LENGTH moins le caractère de fin de la valeur null.  
  
 *cbErrorMsgMax*  
 [Entrée] Longueur maximale de la *szErrorMsg* mémoire tampon. Il doit être inférieur ou égal à SQL_MAX_MESSAGE_LENGTH moins le caractère de fin de la valeur null.  
  
 *pcbErrorMsg*  
 [Sortie] Pointeur vers le nombre total d’octets (sans le caractère de fin de la valeur null) disponibles à renvoyer dans *lpszErrorMsg*. Si le nombre d’octets à retourner est supérieur ou égal à *cbErrorMsgMax*, le texte du message dans *lpszErrorMsg* est tronqué à *cbErrorMsgMax* moins les octets de caractère de fin de la valeur null. Le *pcbErrorMsg* argument peut être un pointeur null.  
  
## <a name="returns"></a>Valeur renvoyée  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA ou SQL_ERROR.  
  
## <a name="diagnostics"></a>Diagnostics  
 **SQLInstallerError** ne publie pas de valeurs d’erreur pour lui-même. **SQLInstallerError** retourne SQL_NO_DATA lorsqu’il est impossible de récupérer les informations d’erreur (dans ce cas *pfErrorCode* n’est pas définie). Si **SQLInstallerError** ne peut pas accéder aux valeurs d’erreur pour une raison quelconque qui doit normalement retourner SQL_ERROR, **SQLInstallerError** retourne SQL_ERROR, mais ne valide pas les valeurs d’erreur. Si vous ne connaissez pas la longueur de la chaîne d’avertissement (*lpszErrorMsg*), vous pouvez définir *lpszErrorMsg* à NULL et appelez **SQLInstallerError**. **SQLInstallerError** sera puis retourner la longueur de la chaîne d’avertissement dans *cbErrorMsgMax*. Si la mémoire tampon pour le message d’erreur est trop courte, **SQLInstallerError** retourne SQL_SUCCESS_WITH_INFO et retourne le bon *pfErrorCode* valeur **SQLInstallerError**.  
  
 Pour déterminer si une troncation s’est produite dans le message d’erreur, une application peut comparer la valeur de la *cbErrorMsgMax* argument à la longueur réelle du texte du message écrit dans le *pcbErrorMsg* argument. En cas de troncation, la longueur du tampon correct doit être allouée pour *lpszErrorMsg* et **SQLInstallerError** doit encore être appelée avec correspondant *IErreur* enregistrement.  
  
## <a name="comments"></a>Commentaires  
 Une application appelle **SQLInstallerError** lorsqu’un appel précédent à la fonction du programme d’installation ODBC retourne FALSE. Fonctions de programme d’installation de programme d’installation et de pilote ou de convertisseur ODBC valider zéro ou plusieurs erreurs uniquement lorsque la fonction échoue (renvoie FALSE) ; Par conséquent, une application appelle **SQLInstallerError** uniquement après l’échec d’une fonction de programme d’installation ODBC.  
  
 La file d’attente des erreurs de programme d’installation ODBC est vidé à chaque fois qu'un nouveau programme d’installation est appelée. Par conséquent, une application ne peut pas attendre récupérer les erreurs pour les fonctions autres que du dernier appel de fonction du programme d’installation.  
  
 Pour récupérer plusieurs erreurs pour un appel de fonction, une application appelle **SQLInstallerError** plusieurs fois.  
  
 Lorsqu’il n’existe aucune information supplémentaire, **SQLInstallerError** retourne SQL_NO_DATA, le *pfErrorCode* argument n’est pas défini, le *pcbErrorMsg* argument est égal à 0 et le *lpszErrorMsg* argument contient un seul caractère de fin de null (sauf si le *cbErrorMsgMax* argument est égal à 0).

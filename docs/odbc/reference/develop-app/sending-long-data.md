---
title: Envoi de données longues (en anglais) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- long data [ODBC]
- sending long data [ODBC]
ms.assetid: ea989084-a8e6-4737-892e-9ec99dd49caf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aeeeb716aa2f9a72338f3aeb586dffce86f84069
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304180"
---
# <a name="sending-long-data"></a>Envoi de données de type Long
Les DBMS définissent les *données longues* comme n’importe quel personnage ou données binaires sur une certaine taille, telles que 254 caractères. Il pourrait ne pas être possible de stocker un élément entier de données longues dans la mémoire, comme lorsque l’élément représente un long document texte ou un bitmap. Étant donné que ces données ne peuvent pas être stockées dans un seul tampon, la source de données les envoie au conducteur dans des pièces avec **SQLPutData** lorsque la déclaration est exécutée. Les paramètres pour lesquels les données sont envoyées au moment de l’exécution sont connus sous le nom *de paramètres de données à l’exécution*.  
  
> [!NOTE]  
>  Une application peut effectivement envoyer n’importe quel type de données au moment de l’exécution avec **SQLPutData**, bien que seuls les données de caractère et binaires peuvent être envoyées en pièces. Toutefois, si les données sont assez petites pour tenir dans un seul tampon, il n’y a généralement aucune raison d’utiliser **SQLPutData**. Il est beaucoup plus facile de lier le tampon et de laisser le conducteur récupérer les données à partir du tampon.  
  
 Pour envoyer des données au moment de l’exécution, l’application effectue les actions suivantes :  
  
1.  Adopte une valeur 32 bits qui identifie le paramètre dans l’argument *ParamètreValuePtr* dans **SQLBindParameter** plutôt que de passer l’adresse d’un tampon. Cette valeur n’est pas analysée par le conducteur. Il sera retourné à l’application plus tard, de sorte qu’il devrait signifier quelque chose à l’application. Par exemple, il peut s’agir du nombre de paramètres ou de la poignée d’un fichier contenant des données.  
  
2.  Passe l’adresse d’un tampon de longueur/indicateur dans *l’argument StrLen_or_IndPtr* de **SQLBindParameter**.  
  
3.  Stocke SQL_DATA_AT_EXEC ou le résultat de la SQL_LEN_DATA_AT_EXEC(*longueur)* macro dans la longueur / tampon indicateur. Ces deux valeurs indiquent au conducteur que les données du paramètre seront envoyées avec **SQLPutData**. SQL_LEN_DATA_AT_EXEC) est*length*utilisé lors de l’envoi de longues données à une source de données qui doit savoir combien d’octets de données longues seront envoyés afin qu’il puisse préallocer l’espace. Pour déterminer si une source de données nécessite cette valeur, l’application appelle **SQLGetInfo** avec l’option SQL_NEED_LONG_DATA_LEN. Tous les conducteurs doivent soutenir cette macro; si la source de données ne nécessite pas la longueur des byte, le conducteur peut l’ignorer.  
  
4.  Appels **SQLExecute** ou **SQLExecDirect**. Le conducteur découvre qu’un tampon longueur/indicateur contient la valeur SQL_DATA_AT_EXEC ou le résultat de la macro*SQL_LEN_DATA_AT_EXEC)* et les rendements SQL_NEED_DATA comme valeur de retour de la fonction.  
  
5.  Appelle **SQLParamData** en réponse à la valeur de rendement SQL_NEED_DATA. Si de longues données doivent être envoyées, **SQLParamData** revient SQL_NEED_DATA. Dans le tampon pointé par l’argument *ValuePtrPtr,* le conducteur retourne la valeur qui identifie le paramètre de données à l’exécution. S’il existe plus d’un paramètre de données à l’exécution, l’application doit utiliser cette valeur pour déterminer le paramètre pour lequel envoyer des données; le conducteur n’est pas tenu de demander des données pour les paramètres de données à l’exécution dans un ordre particulier.  
  
6.  Appelle **SQLPutData** pour envoyer les données de paramètres au conducteur. Si les données de paramètres ne s’inscrivent pas dans un seul tampon, comme c’est souvent le cas avec les données longues, l’application appelle **SQLPutData** à plusieurs reprises pour envoyer les données en pièces; c’est au conducteur et à la source de données de réassembler les données. Si l’application transmet les données de chaîne non résiliées, le conducteur ou la source de données doit supprimer le caractère de résiliation nulle dans le cadre du processus de remontage.  
  
7.  Appelle **SQLParamData** à nouveau pour indiquer qu’il a envoyé toutes les données pour le paramètre. S’il existe des paramètres de données à l’exécution pour lesquels les données n’ont pas été envoyées, le conducteur renvoie SQL_NEED_DATA et la valeur qui identifie le paramètre suivant; la demande revient à l’étape 6. Si des données ont été envoyées pour tous les paramètres de données à l’exécution, la déclaration est exécutée. **SQLParamData** retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO et peut retourner toute valeur de retour ou de diagnostic que **SQLExecute** ou **SQLExecDirect** peut retourner.  
  
 Après le retour **de SQLExecute** ou **SQLExecDirect** SQL_NEED_DATA et avant que les données n’ont été complètement envoyées pour le dernier paramètre de données à l’exécution, la déclaration est dans un état de données de besoin. Bien qu’une déclaration soit dans un état de données de besoin, l’application ne peut appeler que **SQLPutData**, **SQLParamData**, **SQLCancel**, **SQLGetDiagField**, ou **SQLGetDiagRec**; toutes les autres fonctions renvoient SQLSTATE HY010 (erreur de séquence de fonction). Appeler **SQLCancel** annule l’exécution de la déclaration et la renvoie à son état précédent. Pour plus d’informations, voir [Annexe B: ODBC State Transition Tables](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Par exemple, envoyez des données au moment de l’exécution, consultez la description de la fonction [SQLPutData.](../../../odbc/reference/syntax/sqlputdata-function.md)

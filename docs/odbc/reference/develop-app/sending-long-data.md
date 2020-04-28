---
title: Envoi de données de type long | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304180"
---
# <a name="sending-long-data"></a>Envoi de données de type Long
Les SGBD définissent des *données longues* sous forme de données binaires ou de caractères sur une certaine taille, par exemple 254 caractères. Il se peut qu’il ne soit pas possible de stocker l’intégralité d’un élément de données de type long en mémoire, par exemple lorsque l’élément représente un long document ou une image bitmap. Étant donné que ces données ne peuvent pas être stockées dans une seule mémoire tampon, la source de données les envoie au pilote en parties avec **SQLPutData** lorsque l’instruction est exécutée. Les paramètres pour lesquels les données sont envoyées au moment de l’exécution sont appelés *paramètres de données en*cours d’exécution.  
  
> [!NOTE]  
>  Une application peut en fait envoyer n’importe quel type de données au moment de l’exécution avec **SQLPutData**, bien que seules les données de caractères et binaires puissent être envoyées en partie. Toutefois, si les données sont suffisamment petites pour tenir dans une seule mémoire tampon, il n’y a généralement aucune raison d’utiliser **SQLPutData**. Il est beaucoup plus facile de lier la mémoire tampon et de laisser le pilote récupérer les données de la mémoire tampon.  
  
 Pour envoyer des données au moment de l’exécution, l’application effectue les actions suivantes :  
  
1.  Passe une valeur 32 bits qui identifie le paramètre dans l’argument *ParameterValuePtr* dans **SQLBindParameter** au lieu de passer l’adresse d’une mémoire tampon. Cette valeur n’est pas analysée par le pilote. Il sera renvoyé à l’application par la suite. il doit donc s’agir d’un point de vue de l’application. Par exemple, il peut s’agir du numéro du paramètre ou du handle d’un fichier contenant des données.  
  
2.  Passe l’adresse d’une mémoire tampon de longueur/d’indicateur dans l’argument *StrLen_or_IndPtr* de **SQLBindParameter**.  
  
3.  Stocke SQL_DATA_AT_EXEC ou le résultat de la macro SQL_LEN_DATA_AT_EXEC (*longueur*) dans le tampon longueur/indicateur. Ces deux valeurs indiquent au pilote que les données du paramètre sont envoyées avec **SQLPutData**. SQL_LEN_DATA_AT_EXEC (*longueur*) est utilisé lors de l’envoi de données de type long à une source de données qui doit connaître le nombre d’octets de données longues à envoyer afin qu’il puisse préallouer de l’espace. Pour déterminer si une source de données requiert cette valeur, l’application appelle **SQLGetInfo** avec l’option SQL_NEED_LONG_DATA_LEN. Tous les pilotes doivent prendre en charge cette macro. Si la source de données ne nécessite pas la longueur d’octet, le pilote peut l’ignorer.  
  
4.  Appelle **SQLExecute** ou **SQLExecDirect**. Le pilote découvre qu’une mémoire tampon de longueur/d’indicateur contient la valeur SQL_DATA_AT_EXEC ou le résultat de la macro SQL_LEN_DATA_AT_EXEC (*longueur*) et retourne SQL_NEED_DATA comme valeur de retour de la fonction.  
  
5.  Appelle **SQLParamData** en réponse à la valeur de retour de SQL_NEED_DATA. Si des données de type long doivent être envoyées, **SQLParamData** retourne SQL_NEED_DATA. Dans la mémoire tampon vers laquelle pointe l’argument *ValuePtrPtr* , le pilote retourne la valeur qui identifie le paramètre de données en cours d’exécution. S’il existe plusieurs paramètres de données en cours d’exécution, l’application doit utiliser cette valeur pour déterminer le paramètre pour lequel envoyer des données ; le pilote n’est pas requis pour demander des données pour les paramètres de données en cours d’exécution dans un ordre particulier.  
  
6.  Appelle **SQLPutData** pour envoyer les données de paramètre au pilote. Si les données de paramètre ne tiennent pas dans une seule mémoire tampon, comme c’est souvent le cas avec les données de type long, l’application appelle **SQLPutData** à plusieurs reprises pour envoyer les données par parties. Il revient au pilote et à la source de données de réassembler les données. Si l’application transmet des données de chaîne se terminant par un caractère null, le pilote ou la source de données doit supprimer le caractère de fin null dans le cadre du processus de réassemblage.  
  
7.  Appelle à nouveau **SQLParamData** pour indiquer qu’il a envoyé toutes les données pour le paramètre. S’il existe des paramètres de données en cours d’exécution pour lesquels des données n’ont pas été envoyées, le pilote retourne SQL_NEED_DATA et la valeur qui identifie le paramètre suivant ; l’application retourne à l’étape 6. Si des données ont été envoyées pour tous les paramètres de données en cours d’exécution, l’instruction est exécutée. **SQLParamData** retourne SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO et peut retourner une valeur de retour ou un diagnostic que **SQLExecute** ou **SQLExecDirect** peut retourner.  
  
 Après l’exécution de **SQLExecute** ou **SQLExecDirect** SQL_NEED_DATA et avant l’envoi complet des données pour le dernier paramètre de données en cours d’exécution, l’instruction est dans un état de données requis. Alors qu’une instruction est dans un état de données requis, l’application peut uniquement appeler **SQLPutData**, **SQLParamData**, **SQLCancel**, **SQLGetDiagField**ou **SQLGetDiagRec**; toutes les autres fonctions retournent SQLSTATE HY010 (erreur de séquence de fonction). L’appel de **SQLCancel** annule l’exécution de l’instruction et la retourne à son état précédent. Pour plus d’informations, consultez [annexe B : tables de transition d’État ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Pour obtenir un exemple d’envoi de données au moment de l’exécution, consultez la description de la fonction [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md) .

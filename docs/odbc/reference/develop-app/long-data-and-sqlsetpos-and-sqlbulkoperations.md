---
title: Long Data et SQLSetPos et SQLBulkOperations (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- long data [ODBC]
- SQLSetPos function [ODBC], long data and SQLBulkOperations
- data updates [ODBC], long data
- updating data [ODBC], long data
- SQLBulkOperations function [ODBC], long data
ms.assetid: e2fdf842-5e4c-46ca-bb21-4625c3324f28
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4bc6c5d2da2f796a7c312971635fc36bc2fae8af
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287863"
---
# <a name="long-data-and-sqlsetpos-and-sqlbulkoperations"></a>Données de type Long, et SQLSetPos et SQLBulkOperations
Comme c’est le cas pour les paramètres des relevés SQL, de longues données peuvent être envoyées lors de la mise à jour des lignes avec **SQLBulkOperations** ou **SQLSetPos** ou lors de l’insertion de lignes avec **SQLBulkOperations**. Les données sont envoyées en pièces, avec plusieurs appels à **SQLPutData**. Les colonnes pour lesquelles les données sont envoyées au moment de l’exécution sont connues sous le nom *de colonnes de données à l’exécution*.  
  
> [!NOTE]  
>  Une application peut en fait envoyer n’importe quel type de données au moment de l’exécution avec **SQLPutData**, bien que seuls les données de caractère et binaires peuvent être envoyées en pièces. Toutefois, si les données sont assez petites pour tenir dans un seul tampon, il n’y a généralement aucune raison d’utiliser **SQLPutData**. Il est beaucoup plus facile de lier le tampon et de laisser le conducteur récupérer les données à partir du tampon.  
  
 Étant donné que les colonnes de données longues ne sont généralement pas liées, l’application doit lier la colonne avant d’appeler **SQLBulkOperations** ou **SQLSetPos** et non l’avoir délimitée après avoir appelé **SQLBulkOperations** ou **SQLSetPos**. La colonne doit être liée parce que **SQLBulkOperations** ou **SQLSetPos** ne fonctionne que sur les colonnes liées et doivent être non liés de sorte que **SQLGetData** peut être utilisé pour récupérer les données de la colonne.  
  
 Pour envoyer des données au moment de l’exécution, l’application fait ce qui suit :  
  
1.  Place une valeur 32 bits dans le tampon rowset au lieu d’une valeur de données. Cette valeur sera retournée à l’application plus tard, de sorte que l’application devrait la définir à une valeur significative, comme le nombre de la colonne ou la poignée d’un fichier contenant des données.  
  
2.  Définit la valeur du tampon longueur/indicateur au résultat du*SQL_LEN_DATA_AT_EXEC)* macro. Cette valeur indique au conducteur que les données du paramètre seront envoyées avec **SQLPutData**. La valeur *de longueur* est utilisée lors de l’envoi de données longues à une source de données qui doit savoir combien d’octets de données longues seront envoyés afin qu’ils puissent préallocer l’espace. Pour déterminer si une source de données nécessite cette valeur, l’application appelle **SQLGetInfo** avec l’option SQL_NEED_LONG_DATA_LEN. Tous les conducteurs doivent soutenir cette macro; si la source de données ne nécessite pas la longueur des byte, le conducteur peut l’ignorer.  
  
3.  Appels **SQLBulkOperations** ou **SQLSetPos**. Le conducteur découvre qu’un tampon longueur/indicateur contient le résultat de la macro*SQL_LEN_DATA_AT_EXEC)* et les retours SQL_NEED_DATA comme valeur de retour de la fonction.  
  
4.  Appelle **SQLParamData** en réponse à la valeur de rendement SQL_NEED_DATA. Si de longues données doivent être envoyées, **SQLParamData** revient SQL_NEED_DATA. Dans le tampon pointé par l’argument *ValuePtrPtr,* le conducteur retourne la valeur unique que l’application a placée dans le tampon encastré. S’il existe plus d’une colonne de données à l’exécution, l’application utilise cette valeur pour déterminer la colonne pour laquelle envoyer des données; le conducteur n’est pas tenu de demander des données pour les colonnes de données à l’exécution dans un ordre particulier.  
  
5.  Appelle **SQLPutData** pour envoyer les données de la colonne au conducteur. Si les données de la colonne ne rentrent pas dans un seul tampon, comme c’est souvent le cas avec les données longues, l’application appelle **SQLPutData** à plusieurs reprises pour envoyer les données en pièces; c’est au conducteur et à la source de données de réassembler les données. Si l’application transmet les données de chaîne non résiliées, le conducteur ou la source de données doit supprimer le caractère de résiliation nulle dans le cadre du processus de remontage.  
  
6.  Appelle **SQLParamData** à nouveau pour indiquer qu’il a envoyé toutes les données pour la colonne. S’il existe des colonnes de données à l’exécution pour lesquelles les données n’ont pas été envoyées, le conducteur renvoie SQL_NEED_DATA et la valeur unique pour la prochaine colonne de données à exécution; la demande revient à l’étape 5. Si des données ont été envoyées pour toutes les colonnes de données d’exécution, les données de la ligne sont envoyées à la source de données. **SQLParamData** retourne alors SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO et peut retourner n’importe quel **SQLSTATE que SQLBulkOperations** ou **SQLSetPos** peuvent revenir.  
  
 Après **le retour de SQLBulkOperations** ou **SQLSetPos** SQL_NEED_DATA et avant que les données n’ont été complètement envoyées pour la dernière colonne de données à l’exécution, la déclaration est dans un état de données de besoin. Dans cet état, l’application ne peut appeler que **SQLPutData**, **SQLParamData**, **SQLCancel**, **SQLGetDiagField**, ou **SQLGetDiagRec**; toutes les autres fonctions renvoient SQLSTATE HY010 (erreur de séquence de fonction). Appeler **SQLCancel** annule l’exécution de la déclaration et la renvoie à son état précédent. Pour plus d’informations, voir [Annexe B: ODBC State Transition Tables](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).

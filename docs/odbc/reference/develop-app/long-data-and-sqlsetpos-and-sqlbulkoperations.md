---
title: Données de type long et SQLSetPos et SQLBulkOperations | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 578c85331a65c15cb25b5d9b75b7156ab509e910
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036409"
---
# <a name="long-data-and-sqlsetpos-and-sqlbulkoperations"></a>Données de type Long, et SQLSetPos et SQLBulkOperations
Comme c’est le cas avec les paramètres dans les instructions SQL, les données longues peuvent être envoyées lors de la mise à jour de lignes avec **SQLBulkOperations** ou **SQLSetPos** ou lors de l’insertion de lignes avec **SQLBulkOperations**. Les données sont envoyées par parties, avec plusieurs appels à **SQLPutData**. Les colonnes pour lesquelles les données sont envoyées au moment de l’exécution sont connues sous le nom de *colonnes de données en*cours d’exécution.  
  
> [!NOTE]  
>  Une application peut envoyer n’importe quel type de données au moment de l’exécution avec **SQLPutData**, bien que seules les données de caractères et binaires puissent être envoyées en partie. Toutefois, si les données sont suffisamment petites pour tenir dans une seule mémoire tampon, il n’y a généralement aucune raison d’utiliser **SQLPutData**. Il est beaucoup plus facile de lier la mémoire tampon et de laisser le pilote récupérer les données de la mémoire tampon.  
  
 Étant donné que les colonnes de données longues ne sont généralement pas liées, l’application doit lier la colonne avant d’appeler **SQLBulkOperations** ou **SQLSetPos** et la dissocier après avoir appelé **SQLBulkOperations** ou **SQLSetPos**. La colonne doit être liée, car **SQLBulkOperations** ou **SQLSetPos** fonctionnent uniquement sur des colonnes liées et doivent être détachées afin que **SQLGetData** puisse être utilisé pour extraire des données de la colonne.  
  
 Pour envoyer des données au moment de l’exécution, l’application effectue les opérations suivantes :  
  
1.  Place une valeur 32 bits dans la mémoire tampon de l’ensemble de lignes au lieu d’une valeur de données. Cette valeur sera retournée ultérieurement à l’application, de sorte que l’application doit lui affecter une valeur significative, telle que le numéro de la colonne ou le handle d’un fichier contenant des données.  
  
2.  Définit la valeur de la mémoire tampon de longueur/indicateur sur le résultat de la macro SQL_LEN_DATA_AT_EXEC (*longueur*). Cette valeur indique au pilote que les données du paramètre sont envoyées avec **SQLPutData**. La valeur de *longueur* est utilisée lors de l’envoi de données de type long à une source de données qui doit connaître le nombre d’octets de données de type long qui seront envoyés afin de pouvoir préallouer de l’espace. Pour déterminer si une source de données requiert cette valeur, l’application appelle **SQLGetInfo** avec l’option SQL_NEED_LONG_DATA_LEN. Tous les pilotes doivent prendre en charge cette macro. Si la source de données ne nécessite pas la longueur d’octet, le pilote peut l’ignorer.  
  
3.  Appelle **SQLBulkOperations** ou **SQLSetPos**. Le pilote découvre qu’une mémoire tampon de longueur/d’indicateur contient le résultat de la macro SQL_LEN_DATA_AT_EXEC (*longueur*) et retourne SQL_NEED_DATA comme valeur de retour de la fonction.  
  
4.  Appelle **SQLParamData** en réponse à la valeur de retour de SQL_NEED_DATA. Si des données de type long doivent être envoyées, **SQLParamData** retourne SQL_NEED_DATA. Dans la mémoire tampon vers laquelle pointe l’argument *ValuePtrPtr* , le pilote retourne la valeur unique que l’application a placée dans la mémoire tampon de l’ensemble de lignes. S’il existe plus d’une colonne de données en cours d’exécution, l’application utilise cette valeur pour déterminer la colonne pour laquelle envoyer des données ; le pilote n’est pas requis pour demander des données pour les colonnes de données en cours d’exécution dans un ordre particulier.  
  
5.  Appelle **SQLPutData** pour envoyer les données de la colonne au pilote. Si les données de la colonne ne tiennent pas dans une seule mémoire tampon, comme c’est souvent le cas avec les données de type long, l’application appelle **SQLPutData** à plusieurs reprises pour envoyer les données par parties. Il revient au pilote et à la source de données de réassembler les données. Si l’application transmet des données de chaîne se terminant par un caractère null, le pilote ou la source de données doit supprimer le caractère de fin null dans le cadre du processus de réassemblage.  
  
6.  Appelle à nouveau **SQLParamData** pour indiquer qu’il a envoyé toutes les données de la colonne. S’il existe des colonnes de données en cours d’exécution pour lesquelles des données n’ont pas été envoyées, le pilote retourne SQL_NEED_DATA et la valeur unique pour la colonne de données en cours d’exécution suivante ; l’application retourne à l’étape 5. Si des données ont été envoyées pour toutes les colonnes de données en cours d’exécution, les données de la ligne sont envoyées à la source de données. **SQLParamData** retourne ensuite SQL_SUCCESS ou SQL_SUCCESS_WITH_INFO et peut retourner n’importe quel SQLSTATE que **SQLBulkOperations** ou **SQLSetPos** peut retourner.  
  
 Une fois que **SQLBulkOperations** ou **SQLSetPos** a retourné SQL_NEED_DATA et avant que les données soient entièrement envoyées pour la dernière colonne de données en cours d’exécution, l’instruction est dans un état de données requis. Dans cet État, l’application peut appeler uniquement **SQLPutData**, **SQLParamData**, **SQLCancel**, **SQLGetDiagField**ou **SQLGetDiagRec**; toutes les autres fonctions retournent SQLSTATE HY010 (erreur de séquence de fonction). L’appel de **SQLCancel** annule l’exécution de l’instruction et la retourne à son état précédent. Pour plus d’informations, consultez [annexe B : tables de transition d’État ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).

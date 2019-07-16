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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68036409"
---
# <a name="long-data-and-sqlsetpos-and-sqlbulkoperations"></a>Données de type Long, et SQLSetPos et SQLBulkOperations
Comme c’est le cas avec des paramètres dans les instructions SQL, les données de type long peuvent être envoyées lors de la mise à jour des lignes avec **SQLBulkOperations** ou **SQLSetPos** ou lors de l’insertion de lignes avec **SQLBulkOperations**. Les données sont envoyées dans des parties, avec plusieurs appels à **SQLPutData**. Les colonnes pour lesquelles les données sont envoyées au moment de l’exécution sont appelées *data-at-execution colonnes*.  
  
> [!NOTE]  
>  Une application peut envoyer n’importe quel type de données au moment de l’exécution avec **SQLPutData**, même si uniquement des caractères et des données binaires peuvent être envoyées dans les parties. Toutefois, si les données sont suffisamment petites pour tenir dans une seule mémoire tampon, il est généralement inutile d’utiliser **SQLPutData**. Il est beaucoup plus facile de lier la mémoire tampon et de laisser le pilote de récupérer les données à partir de la mémoire tampon.  
  
 Étant donné que les colonnes de données de type long ne sont généralement pas liés, l’application doit lier la colonne avant d’appeler **SQLBulkOperations** ou **SQLSetPos** et annuler la liaison après avoir appelé **SQLBulkOperations**  ou **SQLSetPos**. La colonne doit être liée, car **SQLBulkOperations** ou **SQLSetPos** fonctionne uniquement sur les colonnes dépendantes et doit être indépendant afin que **SQLGetData** peut être utilisé pour récupérer des données à partir de la colonne.  
  
 Pour envoyer des données au moment de l’exécution, l’application effectue les opérations suivantes :  
  
1.  Place une valeur 32 bits dans la mémoire tampon d’ensemble de lignes au lieu d’une valeur de données. Cette valeur s’affichera à l’application plus tard, l’application doit l’affecter à une valeur explicite, comme le numéro de la colonne ou le handle d’un fichier contenant des données.  
  
2.  Définit la valeur dans la mémoire tampon de longueur / d’indicateur au résultat de la SQL_LEN_DATA_AT_EXEC (*longueur*) (macro). Cette valeur indique au pilote que les données pour le paramètre seront envoyées avec **SQLPutData**. Le *longueur* valeur est utilisée lors de l’envoi des données de type long à une source de données qui a besoin de connaître le nombre d’octets de données de type long sera envoyé afin que pré-alloue espace. Pour déterminer si une source de données requiert cette valeur, l’application appelle **SQLGetInfo** avec l’option SQL_NEED_LONG_DATA_LEN. Tous les pilotes doivent prendre en charge cette macro ; Si la source de données ne nécessite pas la longueur d’octet, le pilote peut l’ignorer.  
  
3.  Appels **SQLBulkOperations** ou **SQLSetPos**. Le pilote détecte qu’un tampon de longueur/indicateur contient le résultat de la SQL_LEN_DATA_AT_EXEC (*longueur*) (macro) et retourne SQL_NEED_DATA comme valeur de retour de la fonction.  
  
4.  Appels **SQLParamData** en réponse à la SQL_NEED_DATA valeur de retour. Si les données de type long doivent être envoyé, **SQLParamData** retourne SQL_NEED_DATA. Dans la mémoire tampon vers laquelle pointée le *ValuePtrPtr* argument, le pilote retourne la valeur unique que l’application est placée dans la mémoire tampon d’ensemble de lignes. S’il existe plusieurs colonnes de données en cours d’exécution, l’application utilise cette valeur pour déterminer la colonne pour envoyer des données le pilote n’est pas nécessaire pour demander des données pour les colonnes de data-at-execution dans un ordre particulier.  
  
5.  Appels **SQLPutData** pour envoyer les données de colonne pour le pilote. Si les données de colonne ne tient pas dans une seule mémoire tampon, comme c’est souvent le cas avec les données de type long, l’application appelle **SQLPutData** à plusieurs reprises pour envoyer les données en parties ; c’est à la source de données et de pilote pour réassembler les données. Si l’application transmet des données de chaîne se terminant par null, la pilote ou source de données doit supprimer le caractère de fin de la valeur null dans le cadre du processus de réassemblage.  
  
6.  Appels **SQLParamData** à nouveau pour indiquer qu’il a envoyé toutes les données pour la colonne. S’il existe des colonnes de data-at-execution pour lequel les données n’ont pas été envoyées, le pilote retourne SQL_NEED_DATA et la valeur unique pour la colonne de data-at-execution suivante ; l’application retourne à l’étape 5. Si les données ont été envoyées pour toutes les colonnes de données en cours d’exécution, les données de la ligne sont envoyées à la source de données. **SQLParamData** retourne SQL_SUCCESS, SQL_SUCCESS_WITH_INFO et peut retourner n’importe quel SQLSTATE qui **SQLBulkOperations** ou **SQLSetPos** peut retourner.  
  
 Après avoir **SQLBulkOperations** ou **SQLSetPos** retourne SQL_NEED_DATA et avant que les données ont été complètement envoyées pour la dernière colonne de données en cours d’exécution, l’instruction est dans un état besoin des données. Dans cet état, l’application peut appeler uniquement **SQLPutData**, **SQLParamData**, **SQLCancel**, **SQLGetDiagField**, ou **SQLGetDiagRec**; toutes les autres fonctions retournent SQLSTATE HY010 (erreur de séquence de fonction). Appel **SQLCancel** annule l’exécution de l’instruction et le renvoie à son état précédent. Pour plus d’informations, consultez [annexe b : Tableaux des transitions d’état ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).

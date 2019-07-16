---
title: Envoi de données de type Long | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: acb4ff1637c1530527af88affaf437334596016b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094343"
---
# <a name="sending-long-data"></a>Envoi de données de type Long
Définir des SGBD *données de type long* sous forme de n’importe quel caractère ou binaire sur une certaine taille, telles que de 254 caractères. Il se peut qu’il ne soit pas possible de stocker la totalité d’un élément de données de type long dans la mémoire, telles que lorsque l’élément représente un document texte long ou une image bitmap. Étant donné que ces données ne peuvent pas être stockées dans une seule mémoire tampon, la source de données l’envoie au pilote dans des parties avec **SQLPutData** lorsque l’instruction est exécutée. Paramètres pour lesquels les données sont envoyées au moment de l’exécution sont appelés *data-at-execution paramètres*.  
  
> [!NOTE]  
>  Une application peut envoyer n’importe quel type de données au moment de l’exécution avec **SQLPutData**, même si uniquement des caractères et des données binaires peuvent être envoyées dans les parties. Toutefois, si les données sont suffisamment petites pour tenir dans une seule mémoire tampon, il est généralement inutile d’utiliser **SQLPutData**. Il est beaucoup plus facile de lier la mémoire tampon et de laisser le pilote de récupérer les données à partir de la mémoire tampon.  
  
 Pour envoyer des données au moment de l’exécution, l’application effectue les actions suivantes :  
  
1.  Transmet une valeur 32 bits qui identifie le paramètre dans le *ParameterValuePtr* argument dans **SQLBindParameter** au lieu de passer l’adresse d’une mémoire tampon. Cette valeur n’est pas analysée par le pilote. Il s’affichera à l’application plus tard, afin qu’il doit ont une signification pour l’application. Par exemple, il peut être le numéro du paramètre ou le handle d’un fichier contenant des données.  
  
2.  Transfère l’adresse d’une mémoire tampon de longueur / d’indicateur dans le *StrLen_or_IndPtr* argument de **SQLBindParameter**.  
  
3.  Stocke les SQL_DATA_AT_EXEC ou le résultat de la SQL_LEN_DATA_AT_EXEC (*longueur*) (macro) dans la mémoire tampon de longueur / d’indicateur. Les deux de ces valeurs indiquent au pilote que les données pour le paramètre seront envoyées avec **SQLPutData**. SQL_LEN_DATA_AT_EXEC (*longueur*) est utilisé lors de l’envoi des données de type long à une source de données qui a besoin de connaître le nombre d’octets de données de type long sera envoyé afin que pré-alloue espace. Pour déterminer si une source de données requiert cette valeur, l’application appelle **SQLGetInfo** avec l’option SQL_NEED_LONG_DATA_LEN. Tous les pilotes doivent prendre en charge cette macro ; Si la source de données ne nécessite pas la longueur d’octet, le pilote peut l’ignorer.  
  
4.  Appels **SQLExecute** ou **SQLExecDirect**. Le pilote détecte qu’un tampon de longueur/indicateur contient la valeur SQL_DATA_AT_EXEC ou le résultat de la SQL_LEN_DATA_AT_EXEC (*longueur*) (macro) et retourne SQL_NEED_DATA comme valeur de retour de la fonction.  
  
5.  Appels **SQLParamData** en réponse à la SQL_NEED_DATA valeur de retour. Si les données de type long doivent être envoyé, **SQLParamData** retourne SQL_NEED_DATA. Dans la mémoire tampon vers laquelle pointée le *ValuePtrPtr* argument, le pilote retourne la valeur qui identifie le paramètre data-at-execution. S’il existe plusieurs paramètres de data-at-execution, l’application doit utiliser cette valeur pour déterminer quel paramètre pour envoyer des données le pilote n’est pas nécessaire pour demander des données pour les paramètres de data-at-execution dans un ordre particulier.  
  
6.  Appels **SQLPutData** pour envoyer les données de paramètre pour le pilote. Si les données de paramètre ne tient pas dans une seule mémoire tampon, comme c’est souvent le cas avec les données de type long, l’application appelle **SQLPutData** à plusieurs reprises pour envoyer les données en parties ; c’est à la source de données et de pilote pour réassembler les données. Si l’application transmet des données de chaîne se terminant par null, la pilote ou source de données doit supprimer le caractère de fin de la valeur null dans le cadre du processus de réassemblage.  
  
7.  Appels **SQLParamData** à nouveau pour indiquer qu’il a envoyé toutes les données pour le paramètre. S’il y a aucun paramètre data-at-execution pour lequel les données n’ont pas été envoyées, le pilote retourne SQL_NEED_DATA et la valeur qui identifie le paramètre suivant ; l’application retourne à l’étape 6. Si les données ont été envoyées pour tous les paramètres de data-at-execution, l’instruction est exécutée. **SQLParamData** retourne SQL_SUCCESS, SQL_SUCCESS_WITH_INFO et peut retourne une valeur de retour ou diagnostic qui **SQLExecute** ou **SQLExecDirect** peut retourner.  
  
 Après avoir **SQLExecute** ou **SQLExecDirect** retourne SQL_NEED_DATA et avant l’envoi de données pour le dernier paramètre data-at-execution a complètement, l’instruction est dans un état besoin des données. Bien qu’une instruction soit dans un état besoin des données, l’application peut appeler uniquement **SQLPutData**, **SQLParamData**, **SQLCancel**, **SQLGetDiagField**, ou **SQLGetDiagRec**; toutes les autres fonctions retournent SQLSTATE HY010 (erreur de séquence de fonction). Appel **SQLCancel** annule l’exécution de l’instruction et le renvoie à son état précédent. Pour plus d’informations, consultez [annexe b : Tableaux des transitions d’état ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Pour obtenir un exemple d’envoi de données au moment de l’exécution, consultez le [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md) description de fonction.

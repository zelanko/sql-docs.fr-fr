---
title: Extraction d’une ligne de données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFetch function [ODBC], fetching a row of data
- cursors [ODBC], fetching rows
- result sets [ODBC], fetching
- fetches [ODBC], row of data
ms.assetid: 16d4a380-0d83-456b-aeee-f10738944e86
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 012e454d03a0eb4ad16095353351d67e50d9586a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63061517"
---
# <a name="fetching-a-row-of-data"></a>Extraction d’une ligne de données
Pour extraire une ligne de données, une application appelle **SQLFetch**. **SQLFetch** peut être appelée avec n’importe quel type de curseur, mais il ne déplace le curseur de l’ensemble de lignes dans une direction avant uniquement. **SQLFetch** avance le curseur à la ligne suivante et retourne les données pour toutes les colonnes qui ont été liés par des appels à **SQLBindCol**. Lorsque le curseur atteint la fin du résultat défini, **SQLFetch** retourne SQL_NO_DATA. Pour obtenir des exemples de l’appel **SQLFetch**, consultez [à l’aide de SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).  
  
 Exactement comment **SQLFetch** est implémentée est spécifique au pilote, mais le grand modèle concerne le pilote récupérer les données pour les colonnes liées à partir de la source de données, convertissez-le selon les types de variables liées, puis placent la données converties dans ces variables. Si le pilote ne peut pas convertir des données quelconques, **SQLFetch** retourne une erreur. L’application peut continuer l’extraction de lignes, mais les données de la ligne actuelle sont perdues. Que se passe-t-il pour les données pour les colonnes indépendantes dépend du pilote, mais la plupart des pilotes récupérer et rejeter ou jamais récupérez-la du tout.  
  
 Le pilote définit également les valeurs de n’importe quel mémoires tampon de longueur / d’indicateur qui ont été liés. Si la valeur de données pour une colonne est NULL, le pilote définit la mémoire tampon de longueur / d’indicateur correspondant avec la valeur SQL_NULL_DATA. Si la valeur de données n’est pas NULL, le pilote définit la mémoire tampon de longueur / d’indicateur à la longueur d’octet des données après la conversion. Si cette longueur ne peut pas être déterminée, comme c’est parfois le cas avec les données de type long qui sont récupérées par plusieurs appels de fonction, le pilote définit la mémoire tampon de longueur / d’indicateur à SQL_NO_TOTAL. Pour les types de données de longueur fixe, telles que des entiers et des structures de date, la longueur d’octet est la taille du type de données.  
  
 Pour les données de longueur variable, telles que des caractères et des données binaires, le pilote vérifie la longueur d’octet des données converties par rapport à la longueur d’octet de la mémoire tampon liée à la colonne ; longueur de la mémoire tampon est spécifiée dans le *BufferLength* argument dans **SQLBindCol**. Si la longueur d’octet des données converties est supérieure à la longueur d’octet de la mémoire tampon, le pilote tronque les données pour tenir dans la mémoire tampon, retourne la longueur non tronquée dans la mémoire tampon de longueur / d’indicateur, retourne SQL_SUCCESS_WITH_INFO et SQLSTATE 01004 (données de place tronqué) dans les tests de diagnostic. La seule exception à cela est que si un signet de longueur variable est tronqué quand retournée par **SQLFetch**, qui retourne SQLSTATE 22001 (données chaîne tronquée à droite).  
  
 Données de longueur fixe ne sont jamais tronquées, car le pilote part du principe que la taille de la mémoire tampon liée est la taille du type de données. Troncation de données a tendance à être rare, car l’application est généralement liée à une mémoire tampon assez grande pour contenir la valeur de la totalité des données ; Il détermine la taille nécessaire à partir des métadonnées. Toutefois, l’application peut lier de manière explicite une mémoire tampon qu’il puisse pour être trop petit. Par exemple, il peut récupérer et afficher les 20 premiers caractères d’une description de la partie ou les 100 premiers caractères d’une colonne de texte long.  
  
 Données de type caractère doivent être terminée par le pilote avant d’être renvoyé à l’application, même si elle a été tronquée. Le caractère null de terminaison n’est pas inclus dans la longueur d’octet retourné mais requiert d’espace dans la mémoire tampon liée. Par exemple, une application utilise des chaînes composées de données de caractères dans le jeu de caractères ASCII, un pilote a 50 caractères de données à retourner, et tampon de l’application est 25 octets de long. Dans la mémoire tampon de l’application, le pilote retourne les premier 24 caractères suivis d’un caractère nul de terminaison. Dans la mémoire tampon de longueur / d’indicateur, elle retourne une longueur d’octet de 50.  
  
 L’application peut limiter le nombre de lignes dans le jeu de résultats en définissant l’attribut d’instruction SQL_ATTR_MAX_ROWS avant que l’exécution de l’instruction qui crée le résultat défini. Par exemple, le mode Aperçu dans une application permet de formater des rapports a besoin que les données nécessaires pour afficher la première page du rapport. En limitant la taille du jeu de résultats, une telle fonctionnalité serait exécutées plus rapidement. Cet attribut d’instruction vise à réduire le trafic réseau et ne peut pas pris en charge par tous les pilotes.

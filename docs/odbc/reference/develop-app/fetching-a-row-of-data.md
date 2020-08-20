---
description: Extraction d’une ligne de données
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 71ced7d7df30f1bb4f784317b76f7b42553951df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499889"
---
# <a name="fetching-a-row-of-data"></a>Extraction d’une ligne de données
Pour extraire une ligne de données, une application appelle **SQLFetch**. **SQLFetch** peut être appelée avec n’importe quel type de curseur, mais ne déplace le curseur de l’ensemble de lignes que dans une direction avant uniquement. **SQLFetch** avance le curseur à la ligne suivante et retourne les données pour toutes les colonnes qui étaient liées avec des appels à **SQLBindCol**. Lorsque le curseur atteint la fin du jeu de résultats, **SQLFetch** retourne SQL_NO_DATA. Pour obtenir des exemples d’appel de **SQLFetch**, consultez [utilisation de SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).  
  
 La façon dont la méthode **SQLFetch** est implémentée est spécifique au pilote, mais le modèle général permet au pilote de récupérer les données pour toutes les colonnes liées de la source de données, de les convertir en fonction des types de variables liées et de placer les données converties dans ces variables. Si le pilote ne peut pas convertir de données, **SQLFetch** retourne une erreur. L’application peut poursuivre l’extraction des lignes, mais les données de la ligne actuelle sont perdues. Ce qui arrive aux données des colonnes indépendantes dépend du pilote, mais la plupart des pilotes les récupèrent et les ignorent ou ne les récupèrent pas du tout.  
  
 Le pilote définit également les valeurs de toutes les mémoires tampons de longueur/d’indicateur qui ont été liées. Si la valeur de données d’une colonne est NULL, le pilote définit la mémoire tampon de longueur/indicateur correspondante sur SQL_NULL_DATA. Si la valeur de données n’est pas NULL, le pilote définit la mémoire tampon de longueur/d’indicateur sur la longueur en octets des données après la conversion. Si cette longueur ne peut pas être déterminée, comme c’est parfois le cas avec de longues données récupérées par plusieurs appels de fonction, le pilote définit la mémoire tampon de longueur/d’indicateur sur SQL_NO_TOTAL. Pour les types de données de longueur fixe, tels que les entiers et les structures de date, la longueur en octets correspond à la taille du type de données.  
  
 Pour les données de longueur variable, telles que les données de type caractère et binaire, le pilote vérifie la longueur en octets des données converties par rapport à la longueur en octets de la mémoire tampon liée à la colonne ; la longueur de la mémoire tampon est spécifiée dans l’argument *BufferLength* dans **SQLBindCol**. Si la longueur d’octet des données converties est supérieure à la longueur d’octet de la mémoire tampon, le pilote tronque les données pour les ajuster à la mémoire tampon, retourne la longueur non tronquée dans le tampon de longueur/d’indicateur, retourne SQL_SUCCESS_WITH_INFO et place SQLSTATE 01004 (données tronquées) dans les Diagnostics. La seule exception est si un signet de longueur variable est tronqué lorsqu’il est retourné par **SQLFetch**, qui retourne SQLState 22001 (chaîne de données tronquée à droite).  
  
 Les données de longueur fixe ne sont jamais tronquées, car le pilote part du principe que la taille de la mémoire tampon liée correspond à la taille du type de données. La troncation des données a tendance à être rare, car l’application lie généralement une mémoire tampon suffisamment grande pour contenir la valeur de données entière. elle détermine la taille nécessaire à partir des métadonnées. Toutefois, l’application peut lier explicitement une mémoire tampon qu’elle sait être trop petite. Par exemple, il peut récupérer et afficher les 20 premiers caractères d’une description de partie ou les premiers 100 caractères d’une colonne de texte long.  
  
 Les données caractères doivent être terminées par un caractère NULL par le pilote avant d’être renvoyées à l’application, même si elles ont été tronquées. Le caractère de fin null n’est pas inclus dans la longueur d’octet retournée, mais nécessite de l’espace dans la mémoire tampon liée. Par exemple, supposons qu’une application utilise des chaînes composées de données caractères dans le jeu de caractères ASCII, qu’un pilote comporte 50 caractères de données à retourner et que la mémoire tampon de l’application ait une longueur de 25 octets. Dans la mémoire tampon de l’application, le pilote retourne les 24 premiers caractères suivis d’un caractère de fin null. Dans la mémoire tampon de longueur/indicateur, elle retourne une longueur d’octet de 50.  
  
 L’application peut limiter le nombre de lignes dans le jeu de résultats en définissant l’attribut d’instruction SQL_ATTR_MAX_ROWS avant d’exécuter l’instruction qui crée le jeu de résultats. Par exemple, le mode aperçu dans une application utilisée pour mettre en forme les rapports ne nécessite que suffisamment de données pour afficher la première page du rapport. En limitant la taille du jeu de résultats, une telle fonctionnalité s’exécute plus rapidement. Cet attribut d’instruction vise à réduire le trafic réseau et peut ne pas être pris en charge par tous les pilotes.

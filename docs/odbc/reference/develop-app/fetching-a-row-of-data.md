---
title: Aller chercher une série de données (fr) Microsoft Docs
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
ms.openlocfilehash: a702f561b756d5305020df9f015d3ea4b444caa6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305670"
---
# <a name="fetching-a-row-of-data"></a>Extraction d’une ligne de données
Pour obtenir une série de données, une application appelle **SQLFetch**. **SQLFetch** peut être appelé avec n’importe quel type de curseur, mais il ne déplace le curseur encastré dans une direction avant seulement. **SQLFetch** avance le curseur à la rangée suivante et renvoie les données pour toutes les colonnes qui ont été liées avec des appels à **SQLBindCol**. Lorsque le curseur atteint la fin de l’ensemble de résultats, **SQLFetch** retourne SQL_NO_DATA. Pour des exemples d’appel **SQLFetch**, voir [Using SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md).  
  
 Exactement comment **SQLFetch** est implémenté est spécifique au conducteur, mais le modèle général est pour le conducteur de récupérer les données pour toutes les colonnes liées de la source de données, les convertir en fonction des types de variables liées, et placer les données converties dans ces variables. Si le conducteur ne peut convertir aucune donnée, **SQLFetch** renvoie une erreur. L’application peut continuer à chercher des lignes, mais les données pour la ligne actuelle sont perdues. Ce qui arrive aux données pour les colonnes non liées dépend du conducteur, mais la plupart des pilotes soit les récupérer et les jeter ou ne jamais les récupérer du tout.  
  
 Le conducteur définit également les valeurs de toutes les limites de longueur/indicateur qui ont été liées. Si la valeur de données d’une colonne est NULL, le pilote définit la longueur/indicateur correspondant pour SQL_NULL_DATA. Si la valeur de données n’est pas NULL, le pilote définit le tampon longueur/indicateur sur la longueur des byte des données après la conversion. Si cette longueur ne peut pas être déterminée, comme c’est parfois le cas avec les données longues qui sont récupérées par plus d’un appel de fonction, le conducteur définit la longueur / tampon indicateur pour SQL_NO_TOTAL. Pour les types de données à durée fixe, tels que les intégriers et les structures de date, la longueur des byte est la taille du type de données.  
  
 Pour les données à durée variable, telles que les données de caractère et binaires, le conducteur vérifie la longueur des byte des données converties par rapport à la longueur d’entrée du tampon lié à la colonne; la longueur du tampon est spécifiée dans l’argument *De BufferLength* dans **SQLBindCol**. Si la longueur des byte des données converties est supérieure à la longueur des byte du tampon, le conducteur tronque les données pour s’adapter au tampon, retourne la longueur fausse dans le tampon longueur/indicateur, retourne SQL_SUCCESS_WITH_INFO et place SQLSTATE 01004 (Data tronquée) dans les diagnostics. La seule exception à cela est si un signet à longueur variable est tronqué lorsqu’il est retourné par **SQLFetch**, qui retourne SQLSTATE 22001 (données de cordes, à droite tronqué).  
  
 Les données à durée fixe ne sont jamais tronquées, car le conducteur suppose que la taille du tampon lié est la taille du type de données. La troncation de données tend à être rare, parce que l’application lie habituellement un tampon assez grand pour contenir la valeur de données entière ; il détermine la taille nécessaire des métadonnées. Toutefois, l’application peut explicitement lier un tampon qu’elle sait être trop petit. Par exemple, il peut récupérer et afficher les 20 premiers caractères d’une description de partie ou les 100 premiers caractères d’une longue colonne de texte.  
  
 Les données de caractère doivent être annulées par le conducteur avant qu’elles ne soient retournées à l’application, même si elles ont été tronquées. Le caractère de terminaison nulle n’est pas inclus dans la longueur d’entrée retournée, mais nécessite de l’espace dans le tampon lié. Supposons, par exemple, qu’une application utilise des chaînes composées de données de caractère dans l’ensemble de caractères ASCII, qu’un pilote dispose de 50 caractères de données à retourner et que le tampon de l’application est de 25 octets. Dans le tampon de l’application, le conducteur renvoie les 24 premiers caractères suivis d’un caractère de résiliation nulle. Dans le tampon longueur/indicateur, il retourne une longueur d’aute de 50.  
  
 L’application peut limiter le nombre de lignes dans le résultat défini en définissant l’attribut de l’SQL_ATTR_MAX_ROWS déclaration avant d’exécuter l’énoncé qui crée l’ensemble de résultats. Par exemple, le mode de prévisualisation d’une application utilisée pour formater les rapports n’a besoin que de suffisamment de données pour afficher la première page du rapport. En limitant la taille de l’ensemble de résultats, une telle fonctionnalité fonctionnerait plus rapidement. Cet attribut de déclaration est destiné à réduire le trafic réseau et pourrait ne pas être pris en charge par tous les conducteurs.

---
description: Arguments de valeur de modèle
title: Arguments de la valeur de modèle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], pattern value
- pattern value arguments [ODBC]
ms.assetid: 1d3f0ea6-87af-4836-807f-955e7df2b5df
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a014c63c7fff6b82bbdd26d9fd5b4391c29d0ce2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465751"
---
# <a name="pattern-value-arguments"></a>Arguments de valeur de modèle
Certains arguments dans les fonctions de catalogue, tels que l’argument *TableName* dans **SQLTables**, acceptent les modèles de recherche. Ces arguments acceptent les modèles de recherche si l’attribut d’instruction SQL_ATTR_METADATA_ID est défini sur SQL_FALSE ; Il s’agit d’arguments d’identificateur qui n’acceptent pas de modèle de recherche si cet attribut a la valeur SQL_TRUE.  
  
 Les caractères du modèle de recherche sont les suivants :  
  
-   Un trait de soulignement (_), qui représente n’importe quel caractère unique.  
  
-   Signe de pourcentage (%), qui représente toute séquence de zéro ou plusieurs caractères.  
  
-   Caractère d’échappement, spécifique au pilote, utilisé pour inclure des traits de soulignement, des signes de pourcentage et le caractère d’échappement comme des littéraux. Si le caractère d’échappement précède un caractère non spécial, le caractère d’échappement n’a aucune signification particulière. Si le caractère d’échappement précède un caractère spécial, il échappe au caractère spécial. Par exemple, « \A » est considéré comme deux caractères, « \\ » et « a », mais « \\ % » est traité comme le caractère unique non spécial « % ».  
  
 Le caractère d’échappement est récupéré avec l’option SQL_SEARCH_PATTERN_ESCAPE dans **SQLGetInfo**. Elle doit précéder tout trait de soulignement, signe de pourcentage ou caractère d’échappement dans un argument qui accepte des modèles de recherche pour inclure ce caractère en tant que littéral. Les exemples sont présentés dans le tableau suivant.  
  
|Modèle de recherche|Description|  
|--------------------|-----------------|  
|Un|Tous les identificateurs contenant la lettre A|  
|ABC_|Les quatre identificateurs de caractères commençant par ABC|  
|ABC \\ _|L’identificateur ABC_, en supposant que le caractère d’échappement est une barre oblique inverse ( \\ )|  
|\\\\%|Tous les identificateurs commençant par une barre oblique inverse ( \\ ), en supposant que le caractère d’échappement est une barre oblique inverse|  
  
 Une attention particulière doit être prise pour échapper les caractères de modèle de recherche dans les arguments qui acceptent des modèles de recherche. Cela est particulièrement vrai pour le trait de soulignement, qui est couramment utilisé dans les identificateurs. Une erreur courante dans les applications consiste à extraire une valeur d’une fonction de catalogue et à passer cette valeur à un argument de modèle de recherche dans une autre fonction de catalogue. Par exemple, supposons qu’une application récupère le nom de la table MY_TABLE du jeu de résultats pour **SQLTables** et la transmet à **SQLColumns** pour récupérer une liste de colonnes dans MY_TABLE. Au lieu d’obtenir les colonnes pour MY_TABLE, l’application obtiendra les colonnes de toutes les tables qui correspondent au modèle de recherche MY_TABLE, comme MY_TABLE, MY1TABLE, MY2TABLE, etc.  
  
> [!NOTE]
>  ODBC 2. les pilotes *x* ne prennent pas en charge les modèles de recherche dans l’argument *nomcatalogue* dans **SQLTables**. Les pilotes ODBC 3 *. x* acceptent les modèles de recherche dans cet argument si l’SQL_ATTR_ ODBC_VERSION attribut d’environnement a la valeur SQL_OV_ODBC3 ; ils n’acceptent pas les modèles de recherche dans cet argument s’ils ont la valeur SQL_OV_ODBC2.  
  
 Le passage d’un pointeur null à un argument de modèle de recherche ne limite pas la recherche de cet argument ; autrement dit, un pointeur null et le modèle de recherche% (tous les caractères) sont équivalents. Toutefois, un modèle de recherche de longueur nulle, c’est-à-dire un pointeur valide vers une chaîne de longueur zéro, correspond uniquement à la chaîne vide ("").

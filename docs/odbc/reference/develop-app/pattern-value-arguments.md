---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 53c091fd0b7a6cfdf390997fb5163fbc9d98e18c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68023339"
---
# <a name="pattern-value-arguments"></a>Arguments de valeur de modèle
Certains arguments dans le catalogue des fonctions, telles que la *TableName* argument dans **SQLTables**, acceptez les modèles de recherche. Ces arguments acceptent des modèles de recherche si l’attribut d’instruction SQL_ATTR_METADATA_ID a la valeur SQL_FALSE ; ils sont des arguments d’identificateur qui n’acceptent pas d’un modèle de recherche si cet attribut a la valeur SQL_TRUE.  
  
 Les caractères de modèle de recherche sont :  
  
-   Un trait de soulignement (_), qui représente n’importe quel caractère unique.  
  
-   Un signe de pourcentage (%), qui représente une séquence de zéro ou plusieurs caractères.  
  
-   Un caractère d’échappement, qui est spécifique au pilote et est utilisé pour inclure des traits de soulignement, signes de pourcentage, et le caractère d’échappement en tant que littéraux. Si le caractère d’échappement précède un caractère non spéciale, le caractère d’échappement n’a aucune signification particulière. Si le caractère d’échappement précède un caractère spécial, il échappe le caractère spécial. Par exemple, « \a » seraient traités comme deux caractères, «\\» et « a », mais «\\% » est considéré comme non spéciale caractère « % ».  
  
 Le caractère d’échappement est récupéré avec l’option SQL_SEARCH_PATTERN_ESCAPE dans **SQLGetInfo**. Il doit précéder n’importe quel caractère de soulignement, un signe de pourcentage ou un caractère d’échappement dans un argument qui accepte les modèles de recherche pour inclure ce caractère comme un littéral. Exemples sont présentés dans le tableau suivant.  
  
|Modèle de recherche|Description|  
|--------------------|-----------------|  
|%A %|Tous les identificateurs contenant la lettre A|  
|ABC_|Tous les identificateurs de quatre caractères en commençant par ABC|  
|ABC\\_|L’identificateur ABC_, en supposant que le caractère d’échappement est une barre oblique inverse (\\)|  
|\\\\%|Tous les identificateurs commençant par une barre oblique inverse (\\), en supposant que le caractère d’échappement est une barre oblique inverse|  
  
 Une attention particulière doit être prise pour échapper les caractères de modèle de recherche dans les arguments qui acceptent des modèles de recherche. Cela est particulièrement vrai pour le caractère de soulignement, qui est couramment utilisé dans les identificateurs. Une erreur courante dans les applications consiste à récupérer une valeur d’une fonction de catalogue et passe cette valeur à un argument de modèle de recherche dans une autre fonction de catalogue. Par exemple, une application récupère le nom de table MY_TABLE à partir du résultat défini pour **SQLTables** et la transmet à **SQLColumns** pour récupérer une liste de colonnes dans MY_TABLE. Au lieu d’obtenir les colonnes pour MY_TABLE, l’application obtiendra les colonnes pour toutes les tables qui correspondent au modèle de recherche MY_TABLE, tels que MY_TABLE, MY1TABLE, MY2TABLE et ainsi de suite.  
  
> [!NOTE]
>  ODBC 2. *x* pilotes ne prennent pas en charge les modèles de recherche dans les *CatalogName* argument dans **SQLTables**. ODBC 3 *.x* pilotes acceptent les modèles de recherche dans cet argument si l’attribut d’environnement le paramètre version_odbc SQL_ATTR_ est défini à SQL_OV_ODBC3 ; ils n’acceptent pas les modèles de recherche dans cet argument si elle est définie sur SQL_OV_ODBC2.  
  
 En passant un pointeur null à un argument de modèle de recherche ne contraint pas la recherche pour cet argument ; Autrement dit, un pointeur null et le pourcentage de modèle de recherche (tous les caractères) sont équivalentes. Toutefois, un modèle de recherche de longueur nulle - autrement dit, un pointeur valide vers une chaîne de longueur zéro - correspond uniquement à la chaîne vide ( » »).

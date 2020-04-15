---
title: Arguments de valeur de modèle (en anglais) Microsoft Docs
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
ms.openlocfilehash: 0b8e7b7de64d8051118089a54cf14eb45dc96f74
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282379"
---
# <a name="pattern-value-arguments"></a>Arguments de valeur de modèle
Certains arguments dans les fonctions du catalogue, tels que *l’argument TableName* dans **SQLTables**, acceptent les modèles de recherche. Ces arguments acceptent les modèles de recherche si l’attribut de l’SQL_ATTR_METADATA_ID déclaration est réglé pour SQL_FALSE; ce sont des arguments d’identification qui n’acceptent pas un modèle de recherche si cet attribut est configuré pour SQL_TRUE.  
  
 Les caractères de modèle de recherche sont :  
  
-   Un soulignement, qui représente n’importe quel personnage.  
  
-   Un signe de pourcentage (%), qui représente n’importe quelle séquence de zéro ou plus de caractères.  
  
-   Un personnage d’évasion, qui est spécifique au conducteur et est utilisé pour inclure des soulignements, des signes pour cent, et le caractère d’évasion comme littérale. Si le personnage d’évasion précède un personnage non spécial, le personnage d’évasion n’a pas de signification particulière. Si le personnage d’évasion précède un personnage spécial, il échappe au caractère spécial. Par exemple, « a » serait traité comme\\deux caractères,\\« et « a », mais « % » serait traité comme le « % » non spécial.  
  
 Le personnage d’évasion est récupéré avec l’option SQL_SEARCH_PATTERN_ESCAPE dans **SQLGetInfo**. Il doit précéder tout caractère de soulignement, de pourcentage, ou d’évasion dans un argument qui accepte les modèles de recherche pour inclure ce caractère comme un littéral. Des exemples sont indiqués dans le tableau suivant.  
  
|Modèle de recherche|Description|  
|--------------------|-----------------|  
|%A%|Tous les identificateurs contenant la lettre A|  
|ABC_|Les quatre identificateurs de caractères commençant par ABC|  
|ABC\\-|L’identificateur ABC_, en supposant que le\\personnage d’évasion est une barre oblique inverse ( )|  
|\\\\%|Tous les identificateurs commençant\\par une barre oblique inverse ( ), en supposant que le personnage d’évasion est un backslash|  
  
 Une attention particulière doit être prise pour échapper aux caractères de modèle de recherche dans les arguments qui acceptent les modèles de recherche. Cela est particulièrement vrai pour le caractère de soulignement, qui est couramment utilisé dans les identificateurs. Une erreur commune dans les applications est de récupérer une valeur à partir d’une fonction de catalogue et de passer cette valeur à un argument de modèle de recherche dans une autre fonction de catalogue. Supposons, par exemple, qu’une application récupère le nom de table MY_TABLE du résultat défini pour **SQLTables** et passe ceci à **SQLColumns** pour récupérer une liste de colonnes dans MY_TABLE. Au lieu d’obtenir les colonnes pour MY_TABLE, l’application obtiendra les colonnes pour toutes les tables qui correspondent au modèle de recherche MY_TABLE, tels que MY_TABLE, MY1TABLE, MY2TABLE, et ainsi de suite.  
  
> [!NOTE]
>  ODBC 2. *x* les conducteurs ne prennent pas en charge les modèles de recherche dans l’argument *CatalogName* dans **SQLTables**. Les conducteurs de 3 *,x* ODBC acceptent les modèles de recherche dans cet argument si l’attribut SQL_ATTR_ ODBC_VERSION environnement est réglé pour SQL_OV_ODBC3; ils n’acceptent pas les modèles de recherche dans cet argument s’il est réglé pour SQL_OV_ODBC2.  
  
 Le fait de passer un pointeur nul à un argument de modèle de recherche ne limite pas la recherche de cet argument; c’est-à-dire qu’un pointeur nul et le modèle de recherche % (tous les caractères) sont équivalents. Cependant, un modèle de recherche de longueur zéro - c’est-à-dire un pointeur valide à une chaîne de longueur zéro - ne correspond qu’à la chaîne vide ("").

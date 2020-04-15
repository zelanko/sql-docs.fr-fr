---
title: Décalages de liaison de paramètres Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- offsets of parameters [ODBC]
- binding offsets of parameters [ODBC]
ms.assetid: 309339e9-9ccd-4a58-8aa4-b6dc88f4eb7c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: de67b230883f3cf8a582e73ce82e8c4bd7d21ad0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282488"
---
# <a name="parameter-binding-offsets"></a>Décalages des liaisons de paramètres
Une application peut spécifier qu’un décalage est ajouté aux adresses tampons de paramètres consolidés et aux adresses tampons de longueur/indicateur correspondantes lorsque **SQLExecDirect** ou **SQLExecute** est appelé. Le résultat de ces ajouts détermine les adresses utilisées dans ces opérations.  
  
 Les compensations de liaison permettent à une application de modifier les fixations sans appeler **SQLBindParameter** pour les paramètres précédemment liés. Un appel à **SQLBindParameter** pour rebind un paramètre modifie l’adresse tampon et le pointeur longueur/indicateur. Le rebinding avec un décalage, d’autre part, ajoute simplement une compensation à l’adresse tampon de paramètre lié existant et l’adresse tampon de longueur/indicateur. Lorsque des compensations sont utilisées, les fixations sont un « modèle » de la façon dont les tampons d’application sont disposés et l’application peut déplacer ce « modèle » vers différents domaines de mémoire en changeant la compensation. Un nouveau décalage peut être spécifié à tout moment et est toujours ajouté aux valeurs initialement liées.  
  
 Pour spécifier un décalage de liaison, la demande définit l’attribut SQL_ATTR_PARAM_BIND_OFFSET_PTR énoncé à l’adresse d’un tampon SQLINTEGER. Avant que l’application appelle une fonction qui utilise les liaisons, il place un décalage dans les octets dans ce tampon, tant que ni l’adresse tampon paramètre ni l’adresse tampon longueur /indicateur est 0, et le paramètre lié est dans l’énoncé SQL. La somme de l’adresse et la compensation doivent être une adresse valide. (Cela signifie que l’un ou l’autre ou à la fois le décalage et l’adresse à laquelle le décalage est ajouté peuvent être invalides, tant que leur somme est une adresse valide.)  
  
> [!NOTE]  
>  Les compensations contraignantes ne sont pas prises en charge par ODBC 2. *x* conducteurs.

---
title: Décalages de liaison de paramètre | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d0dbddc71b0d647246d10dad16ad72d533df16de
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68023344"
---
# <a name="parameter-binding-offsets"></a>Décalages des liaisons de paramètres
Une application peut spécifier qu’un décalage est ajouté à adresses de tampons de paramètre et l’indicateur de longueur/correspondante liées aux adresses de mémoire tampon quand **SQLExecDirect** ou **SQLExecute** est appelée. Le résultat de ces ajouts détermine les adresses utilisées dans ces opérations.  
  
 Les décalages de liaison permettent à une application modifier les liaisons sans appeler **SQLBindParameter** pour les paramètres liés précédemment. Un appel à **SQLBindParameter** pour relier un paramètre change l’adresse de la mémoire tampon et le pointeur de longueur / d’indicateur. Rétablissement de la liaison avec un décalage, en revanche, ajoute simplement la valeur un décalage à l’adresse de mémoire tampon de paramètre lié existant et l’adresse de mémoire tampon de longueur / d’indicateur. Lorsque les décalages sont utilisés, les liaisons sont un « modèle » de la disposition des mémoires tampons de l’application et l’application peut passer cet « modèle » vers différentes zones de mémoire en modifiant le décalage. Un nouveau décalage peut être spécifié à tout moment et est toujours ajouté aux valeurs liées à l’origine.  
  
 Pour spécifier un décalage de la liaison, l’application définit l’attribut d’instruction SQL_ATTR_PARAM_BIND_OFFSET_PTR à l’adresse d’une mémoire tampon SQLINTEGER. Avant que l’application appelle une fonction qui utilise les liaisons, il place un décalage en octets dans cette mémoire tampon, tant que l’adresse de mémoire tampon de paramètre, ni l’adresse de mémoire tampon de longueur / d’indicateur a la valeur 0, et le paramètre dépendant est dans l’instruction SQL. La somme de l’adresse et le décalage doit être une adresse valide. (Cela signifie qu’un ou les deux le décalage et l’adresse à laquelle le décalage est ajouté peuvent être non valides, tant que leur somme est une adresse valide.)  
  
> [!NOTE]  
>  Décalages des liaisons ne sont pas pris en charge par ODBC 2. *x* pilotes.

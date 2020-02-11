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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68023344"
---
# <a name="parameter-binding-offsets"></a>Décalages des liaisons de paramètres
Une application peut spécifier qu’un décalage est ajouté aux adresses tampons de paramètre liées et aux adresses de mémoire tampon d’indicateur de longueur/indicateur correspondantes lorsque **SQLExecDirect** ou **SQLExecute** est appelé. Le résultat de ces ajouts détermine les adresses utilisées dans ces opérations.  
  
 Les décalages de liaison permettent à une application de modifier des liaisons sans appeler **SQLBindParameter** pour les paramètres précédemment liés. Un appel à **SQLBindParameter** pour relier un paramètre modifie l’adresse de la mémoire tampon et le pointeur de longueur/indicateur. La reliaison avec un décalage, en revanche, ajoute simplement un décalage à l’adresse tampon de paramètre liée existante et à l’adresse tampon de longueur/d’indicateur existante. Lorsque des décalages sont utilisés, les liaisons sont un « modèle » de la façon dont les mémoires tampons d’application sont présentées et l’application peut déplacer ce « modèle » dans différentes zones de mémoire en modifiant le décalage. Un nouveau décalage peut être spécifié à tout moment et est toujours ajouté aux valeurs liées à l’origine.  
  
 Pour spécifier un décalage de liaison, l’application définit l’attribut d’instruction SQL_ATTR_PARAM_BIND_OFFSET_PTR sur l’adresse d’une mémoire tampon SQLINTEGER destinée. Avant que l’application appelle une fonction qui utilise les liaisons, elle place un décalage en octets dans cette mémoire tampon, tant que l’adresse de la mémoire tampon du paramètre et l’adresse tampon de longueur/d’indicateur n’ont pas la valeur 0, et que le paramètre lié est dans l’instruction SQL. La somme de l’adresse et du décalage doit être une adresse valide. (Cela signifie que l’offset et l’adresse à laquelle le décalage est ajouté peuvent être non valides, à condition que leur somme soit une adresse valide.)  
  
> [!NOTE]  
>  ODBC 2 ne prend pas en charge les décalages de liaison. *x* pilotes.

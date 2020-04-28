---
title: Instruction CREATe INDEX | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c6aa512ff789fcbd00f45f84fb194d4ab3f5da07
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280969"
---
# <a name="create-index-statement"></a>CREATE INDEX, instruction
La syntaxe de l’instruction CREATe INDEX est la suivante :  
  
 CREATe [UNIQUE] INDEX *-Name* sur *table-Name* (*Column-identifier* [ASC] [desc] [, *Column-identifier* [ASC] [desc]...]) Avec \< *liste d’options d’index*>  
  
 où \<la *liste d’options d’index*> peut être : Primary &#124; Disallow null &#124; ignore null  
  
 Seul le pilote Microsoft Access utilise les options interdire les valeurs NULL et ignorer l’index NULL. Les pilotes dBASE et Paradox acceptent la syntaxe, mais ignorent la présence de l’une des deux options.  
  
 Lorsque le pilote Paradox est utilisé, l’instruction CREATe INDEX crée des fichiers de clé primaire et des fichiers secondaires Paradox.  
  
 Cette instruction n’est pas prise en charge par Microsoft Excel ou les pilotes de texte.

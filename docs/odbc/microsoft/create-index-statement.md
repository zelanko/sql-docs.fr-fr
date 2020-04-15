---
title: Déclaration DE l’INDEX CREATE (en anglais) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280969"
---
# <a name="create-index-statement"></a>CREATE INDEX, instruction
La syntaxe de la déclaration CREATE INDEX est la suivante :  
  
 CREATE [UNIQUE] *INDEX-name* ON *table-name* *(column-identifier* [ASC][DESC][, *column-identifier* [ASC][DESC]...]) Avec \< *liste d’options d’index*>  
  
 où \< *la liste d’options d’index* peut être>: PRIMARY &#124; DISALLOW NULL &#124; IGNORE NULL  
  
 Seul le pilote Microsoft Access utilise les options d’index DISALLOW NULL et IGNORE NULL. Les pilotes DBASE et Paradox acceptent la syntaxe, mais ignorent la présence de l’une ou l’autre option.  
  
 Lorsque le pilote Paradox est utilisé, la déclaration CREATE INDEX crée des fichiers clés primaires Paradox et des fichiers secondaires.  
  
 Cette déclaration n’est pas prise en charge par les pilotes Microsoft Excel ou Text.

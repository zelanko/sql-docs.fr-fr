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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ad15ad436b0f34f00acbd75e371e998183f22d2f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081910"
---
# <a name="create-index-statement"></a>CREATE INDEX, instruction
La syntaxe de l’instruction CREATe INDEX est la suivante :  
  
 CREATe [UNIQUE] INDEX *-Name* sur *table-Name* (*Column-identifier* [ASC] [desc] [, *Column-identifier* [ASC] [desc]...]) Avec \< *liste d’options d’index*>  
  
 où \<la *liste d’options d’index*> peut être : Primary &#124; Disallow null &#124; ignore null  
  
 Seul le pilote Microsoft Access utilise les options interdire les valeurs NULL et ignorer l’index NULL. Les pilotes dBASE et Paradox acceptent la syntaxe, mais ignorent la présence de l’une des deux options.  
  
 Lorsque le pilote Paradox est utilisé, l’instruction CREATe INDEX crée des fichiers de clé primaire et des fichiers secondaires Paradox.  
  
 Cette instruction n’est pas prise en charge par Microsoft Excel ou les pilotes de texte.

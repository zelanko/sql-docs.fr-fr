---
description: CREATE INDEX, instruction
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
ms.openlocfilehash: 7a3f5a13624cdb137e8c86cf2c27044c6705298f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483632"
---
# <a name="create-index-statement"></a>CREATE INDEX, instruction
La syntaxe de l’instruction CREATe INDEX est la suivante :  
  
 CREATe [UNIQUE] INDEX *-Name* sur *table-Name* (*Column-identifier* [ASC] [desc] [, *Column-identifier* [ASC] [desc]...]) AVEC \<*index option list*>  
  
 où \<*index option list*> peut être : la &#124; primaire ne pas autoriser la valeur null &#124; ignorer la valeur null  
  
 Seul le pilote Microsoft Access utilise les options interdire les valeurs NULL et ignorer l’index NULL. Les pilotes dBASE et Paradox acceptent la syntaxe, mais ignorent la présence de l’une des deux options.  
  
 Lorsque le pilote Paradox est utilisé, l’instruction CREATe INDEX crée des fichiers de clé primaire et des fichiers secondaires Paradox.  
  
 Cette instruction n’est pas prise en charge par Microsoft Excel ou les pilotes de texte.

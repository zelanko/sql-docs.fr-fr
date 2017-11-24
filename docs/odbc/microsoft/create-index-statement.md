---
title: "CRÉER des INDEX (instruction) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CREATE INDEX [ODBC]
- SQL grammar [ODBC], create index
ms.assetid: 69438247-eef3-44c5-bef2-acef4e146f41
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6737ad2bdde9516291863214d3da5dd6087e3ec2
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="create-index-statement"></a>CRÉER des INDEX (instruction)
La syntaxe de l’instruction CREATE INDEX est :  
  
 CRÉER des INDEX [UNIQUE] *-nom de l’index* ON *-nom de la table* (*identificateur de la colonne* [ASC] [Description] [, *identificateur de la colonne* [ASC][DESC]...]) AVEC \< *liste option d’index*>  
  
 où \< *liste option d’index*> peut être : primaire &#124; INTERDIRE NULL &#124; IGNORER LA VALEUR NULL  
  
 Uniquement le pilote Microsoft Access utilise les options d’index DISALLOW NULL et IGNORE NULL. Les pilotes de Corel dBASE acceptent la syntaxe, mais ignore la présence de l’option.  
  
 Lorsque le pilote Paradox est utilisé, l’instruction CREATE INDEX crée les fichiers de clé primaires de Corel et les fichiers secondaires.  
  
 Cette instruction n’est pas prise en charge par les pilotes Microsoft Excel ou texte.

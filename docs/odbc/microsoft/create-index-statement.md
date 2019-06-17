---
title: CREATE INDEX, instruction | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 93ddc3881796aee3194ec5268afc68ecbab1a487
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63233009"
---
# <a name="create-index-statement"></a>CREATE INDEX, instruction
La syntaxe de l’instruction CREATE INDEX est :  
  
 CRÉER un INDEX [UNIQUE] *nom de l’index* ON *nom de la table* (*identificateur de colonne* [ASC] [Description] [, *identificateur de colonne* [ASC][DESC]...]) AVEC \< *liste d’options d’index*>  
  
 où \< *liste d’options index*> peut être : PRINCIPAL &AMP;#124; INTERDIRE NULL &AMP;#124; IGNORER NULL  
  
 Seul le pilote Microsoft Access utilise les options d’index DISALLOW NULL et IGNORE NULL. Les pilotes de Paradox dBASE acceptent la syntaxe, mais ignorent la présence de des deux options.  
  
 Lorsque le pilote Paradox est utilisé, l’instruction CREATE INDEX crée des fichiers de clés primaires Paradox et les fichiers secondaires.  
  
 Cette instruction n’est pas prise en charge par les pilotes Microsoft Excel ou texte.

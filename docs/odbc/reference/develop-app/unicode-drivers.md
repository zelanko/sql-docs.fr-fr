---
description: Pilotes Unicode
title: Pilotes Unicode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], drivers
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: 3b4742d5-74fb-4aff-aa21-d83a0064d73d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1acdb0c630fe5f4b1b22f51015e7ee94e7d8a56a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424481"
---
# <a name="unicode-drivers"></a>Pilotes Unicode
Le fait qu’un pilote soit un pilote Unicode ou un pilote ANSI dépend entièrement de la nature de la source de données. Si la source de données prend en charge les données Unicode, le pilote doit être un pilote Unicode. Si la source de données ne prend en charge que les données ANSI, le pilote doit rester un pilote ANSI.  
  
 Un pilote Unicode doit exporter **SQLConnectW** pour qu’il soit reconnu comme pilote Unicode par le gestionnaire de pilotes.  
  
 Un pilote Unicode doit accepter des fonctions Unicode (avec un suffixe *W*) et stocker des données Unicode. Il peut également accepter des fonctions ANSI, mais n’est pas requis pour. (Le gestionnaire de pilotes ne passe pas un appel de fonction ANSI avec le suffixe *A* au pilote, mais le convertit en appel de fonction ANSI sans le suffixe, puis le transmet au pilote.)  
  
 Un pilote Unicode doit être en mesure de retourner des jeux de résultats au format Unicode ou ANSI, en fonction de la liaison de l’application. Si une application est liée à SQL_C_CHAR, le pilote Unicode doit convertir les données SQL_WCHAR en SQL_CHAR. Le gestionnaire de pilotes mappera SQL_C_WCHAR à SQL_C_CHAR pour les pilotes ANSI, mais aucun mappage pour les pilotes Unicode.  
  
> [!NOTE]  
>  Lorsque vous déterminez le type de pilote, le gestionnaire de pilotes appelle le pilote **SQLSetConnectAttr** et définit l’attribut SQL_ATTR_ANSI_APP au moment de la connexion. Si l’application utilise des API ANSI, SQL_ATTR_ANSI_APP sera définie sur SQL_AA_TRUE et, si elle utilise Unicode, elle sera définie sur la valeur SQL_AA_FALSE. Cet attribut est utilisé afin que le pilote puisse présenter un comportement différent selon le type d’application. L’attribut ne peut pas être défini directement par l’application et n’est pas pris en charge par **SQLGetConnectAttr**. Si un pilote présente le même comportement pour les applications ANSI et Unicode, il doit retourner SQL_ERROR pour cet attribut. Si le pilote retourne SQL_SUCCESS, le gestionnaire de pilotes sépare les connexions ANSI et Unicode lorsque le regroupement de connexions est utilisé.

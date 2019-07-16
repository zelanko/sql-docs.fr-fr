---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ca9b70ee6a96759e496b831f7c12dc3ee78419b7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68087872"
---
# <a name="unicode-drivers"></a>Pilotes Unicode
Si un pilote doit être un pilote Unicode ou un pilote de ANSI dépend entièrement de la nature de la source de données. Si la source de données prend en charge les données Unicode, le pilote doit être un pilote Unicode. Si la source de données prend uniquement en charge les données ANSI, le pilote doit rester un pilote ANSI.  
  
 Un pilote Unicode doit exporter **SQLConnectW** à être reconnue comme un pilote Unicode par le Gestionnaire de pilotes.  
  
 Un pilote Unicode doit accepter des fonctions Unicode (avec le suffixe de *W*) et stocker des données Unicode. Il peut également accepter des fonctions ANSI, mais n’est pas nécessaire pour. (Le Gestionnaire de pilotes ne passe pas d’un appel de fonction ANSI avec le *A* suffixe au pilote, mais convertit elle ANSI fonctionner appel sans le suffixe, puis transmet au pilote.)  
  
 Un pilote Unicode doit être en mesure de retourner des jeux de résultats dans Unicode ou ANSI, en fonction de la liaison de l’application. Si une application se lie à SQL_C_CHAR, le pilote Unicode doit convertir les données SQL_WCHAR SQL_CHAR. Le Gestionnaire de pilotes est mappage SQL_C_WCHAR SQL_C_CHAR pour les pilotes ANSI Contrairement à aucun mappage pour les pilotes d’Unicode.  
  
> [!NOTE]  
>  Lorsque vous déterminez le type de pilote, le Gestionnaire de pilotes appellera **SQLSetConnectAttr** et définir l’attribut SQL_ATTR_ANSI_APP au moment de la connexion. Si l’application est à l’aide des API ANSI, SQL_ATTR_ANSI_APP est fixé à SQL_AA_TRUE, et si elle est à l’aide d’Unicode, elle sera définie sur la valeur SQL_AA_FALSE. Cet attribut est utilisé afin que le pilote peut présenter un comportement différent selon le type d’application. L’attribut ne peut pas être défini par l’application directement, et il n’est pas pris en charge par **SQLGetConnectAttr**. Si un pilote présente le même comportement pour les applications ANSI et Unicode, elle doit retourner SQL_ERROR pour cet attribut. Si le pilote retourne SQL_SUCCESS, le Gestionnaire de pilotes séparer les connexions ANSI et Unicode lorsque le regroupement de connexions est utilisé.

---
title: Pilotes Unicode Microsoft Docs
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
ms.openlocfilehash: aabdd899d78c1141716725d57e343dc002dc96ad
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284351"
---
# <a name="unicode-drivers"></a>Pilotes Unicode
La question de savoir si un conducteur doit être un conducteur Unicode ou un conducteur DE l’ANSI dépend entièrement de la nature de la source de données. Si la source de données prend en charge les données Unicode, le pilote doit être un pilote Unicode. Si la source de données ne prend en charge que les données DE l’ANSI, le conducteur doit rester un pilote ANSI.  
  
 Un conducteur Unicode doit exporter **SQLConnectW** pour être reconnu comme pilote Unicode par le Driver Manager.  
  
 Un pilote Unicode doit accepter les fonctions Unicode (avec un suffixe de *W*) et stocker les données Unicode. Il peut également accepter les fonctions ANSI, mais n’est pas nécessaire. (Le Driver Manager ne passe pas un appel de fonction ANSI avec le suffixe *A* au conducteur, mais le convertit en un appel de fonction ANSI sans le suffixe, puis le transmet au conducteur.)  
  
 Un pilote Unicode doit être en mesure de retourner les ensembles de résultats en Unicode ou ANSI, selon la liaison de l’application. Si une application se lie à SQL_C_CHAR, le pilote Unicode doit convertir SQL_WCHAR données en SQL_CHAR. Le gestionnaire de pilote cartographiera SQL_C_WCHAR pour SQL_C_CHAR pour les pilotes ANSI, mais ne cartographie pas pour les pilotes Unicode.  
  
> [!NOTE]  
>  Lors de la détermination du type de pilote, le gestionnaire de pilote appelle **SQLSetConnectAttr** et définira l’attribut SQL_ATTR_ANSI_APP au moment de la connexion. Si l’application utilise des API ANSI, SQL_ATTR_ANSI_APP sera configurée pour SQL_AA_TRUE, et si elle utilise Unicode, elle sera définie à une valeur de SQL_AA_FALSE. Cet attribut est utilisé de sorte que le conducteur peut afficher un comportement différent basé sur le type d’application. L’attribut ne peut pas être défini directement par l’application, et il n’est pas pris en charge par **SQLGetConnectAttr**. Si un pilote présente le même comportement pour les applications ANSI et Unicode, il doit retourner SQL_ERROR pour cet attribut. Si le conducteur retourne SQL_SUCCESS, le Driver Manager séparera les connexions ANSI et Unicode lorsque la mise en commun des connexions est utilisée.

---
title: Cas d’identification (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 940d96ece6b2c344fa02e0daadd6248270f4d19e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300149"
---
# <a name="identifier-case"></a>Casse des identificateurs
Dans les déclarations SQL et les arguments de fonction de catalogue, les identificateurs et les identificateurs cités peuvent être sensibles ou non, ce qu’une application peut déterminer en appelant **SQLGetInfo** avec les options SQL_IDENTIFIER_CASE et SQL_QUOTED_IDENTIFIER_CASE.  
  
 Chacune de ces options a quatre valeurs de retour possibles : l’une indiquant que le cas d’identifiant ou d’identifiant cité est sensible et trois indiquant qu’il n’est pas sensible. Les trois valeurs qui ne sont pas sensibles aux cas décrivent en outre le cas dans lequel les identificateurs sont stockés dans le catalogue du système. La façon dont les identificateurs sont stockés dans le catalogue du système n’est pertinente qu’à des fins d’affichage, par exemple lorsqu’une application affiche les résultats d’une fonction de catalogue; il ne modifie pas la sensibilité aux cas des identificateurs.

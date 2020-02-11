---
title: Unicode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC]
- Unicode [ODBC], about Unicode
ms.assetid: 113e1c9a-8333-4805-86f2-e4b57ab816a5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7e0044a2e2efbf0d8921a07ed4679806ba50bcd1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087563"
---
# <a name="unicode"></a>Unicode
Unicode définit l’encodage des caractères dans de nombreux langages.  
  
 Pour plus d’informations sur la norme Unicode, consultez [le consortium Unicode](https://www.unicode.org).  
  
 Unicode définit un jeu de caractères universel. Une page de codes ANSI Windows définit un jeu de caractères, qui contient généralement des caractères pour une langue. Il peut être plus difficile d’écrire une application requise pour utiliser des pages de codes différentes.  
  
 Unicode ne nécessite pas de page de codes. Chaque point de code est mappé à un caractère unique dans un langage donné.  
  
 Actuellement, le seul encodage Unicode pris en charge par ODBC est UCS-2, qui utilise un entier 16 bits (longueur fixe) pour représenter un caractère. Unicode permet aux applications de fonctionner dans différents langages.  
  
 Le gestionnaire de pilotes ODBC 3,5 (ou version ultérieure) est compatible Unicode. Cela affecte deux domaines majeurs : les appels de fonction et les types de données de chaîne. Le gestionnaire de pilotes mappe les arguments de chaîne de fonction et les données de chaîne selon les exigences de l’application et du pilote, qui peuvent être compatibles Unicode ou ANSI. Ces deux domaines sont présentés en détail dans les sections, les [arguments de fonction Unicode](../../../odbc/reference/develop-app/unicode-function-arguments.md) et les [données Unicode](../../../odbc/reference/develop-app/unicode-data.md).  
  
 Le gestionnaire de pilotes ODBC 3,5 (ou version ultérieure) prend en charge l’utilisation d’un pilote Unicode avec une application Unicode et une application ANSI. Il prend également en charge l’utilisation d’un pilote ANSI avec une application ANSI. Le gestionnaire de pilotes fournit un mappage Unicode-à-ANSI limité pour une application Unicode utilisant un pilote ANSI.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Arguments des fonctions Unicode](../../../odbc/reference/develop-app/unicode-function-arguments.md)  
  
-   [Données Unicode](../../../odbc/reference/develop-app/unicode-data.md)

---
title: Unicode - France Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9824e76cebabb6f5f84505292801a0094e359f0f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302443"
---
# <a name="unicode"></a>Unicode
Unicode définit l’encodage pour les caractères dans de nombreuses langues.  
  
 Pour plus d’informations sur la norme Unicode, voir [The Unicode Consortium](https://www.unicode.org).  
  
 Unicode définit un ensemble de caractères universel. Une page de code WINDOWS ANSI définit un ensemble de personnages, contenant généralement des caractères pour une seule langue. Il peut être plus difficile d’écrire une application qui est nécessaire pour utiliser différentes pages de code.  
  
 Unicode n’exige pas de page de code. Chaque point de code est cartographié à un seul personnage dans une certaine langue.  
  
 Actuellement, le seul codage Unicode que ODBC prend en charge est UCS-2, qui utilise un 16 bits d’intégrage (longueur fixe) pour représenter un personnage. Unicode permet aux applications de fonctionner dans différentes langues.  
  
 Le gestionnaire de pilote ODBC 3.5 (ou plus) est compatible Unicode. Cela affecte deux domaines principaux : les appels de fonction et les types de données de chaîne. Le Driver Manager cartographie les arguments de chaîne de fonction et les données de chaîne comme l’exige l’application et le pilote, qui peuvent être soit compatibles Unicode ou SANS permis. Ces deux domaines sont discutés en détail dans les sections, [Unicode Function Arguments](../../../odbc/reference/develop-app/unicode-function-arguments.md) et [Unicode Data](../../../odbc/reference/develop-app/unicode-data.md).  
  
 L’ODBC 3.5 (ou plus) Driver Manager prend en charge l’utilisation d’un pilote Unicode avec une application Unicode et une application ANSI. Il soutient également l’utilisation d’un pilote ANSI avec une application ANSI. Le Driver Manager fournit une cartographie Unicode-à-ANSI limitée pour une application Unicode travaillant avec un pilote ANSI.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Arguments des fonctions Unicode](../../../odbc/reference/develop-app/unicode-function-arguments.md)  
  
-   [Données Unicode](../../../odbc/reference/develop-app/unicode-data.md)

---
title: Vues de Schema Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- schema views [ODBC]
- functions [ODBC], catalog functions
- catalog functions [ODBC], schema views
ms.assetid: f1dfb3e8-a7bd-46c3-92b6-c19531e8409d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a1a9e421c4835d35e3c4f3c644e69b8c7601e8e4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304250"
---
# <a name="schema-views"></a>Vues de schéma
Une application peut récupérer des informations de métadonnées de la DBMS soit en appelant les fonctions de catalogue ODBC ou en utilisant INFORMATION_SCHEMA vues. Les vues sont définies par la norme ANSI SQL-92.  
  
 Si elle est prise en charge par le DBMS et le conducteur, les vues INFORMATION_SCHEMA offrent un moyen plus puissant et complet de récupérer des métadonnées que les fonctions de catalogue ODBC fournissent. Une application peut exécuter sa propre déclaration **SELECT** personnalisée contre l’une de ces vues, peut joindre les points de vue ou peut effectuer un syndicat sur les vues. Tout en offrant une plus grande utilité et un plus large éventail de métadonnées, INFORMATION_SCHEMA vues ne sont pas souvent prises en charge par le DBMS. Cela pourrait changer à mesure que de plus en plus de DBMS et de conducteurs se conforment à SQL-92.  
  
 Pour déterminer quelles vues sont prises en charge, une application appelle **SQLGetInfo** avec l’option SQL_INFO_SCHEMA_VIEWS. Pour récupérer les métadonnées d’une vue prise en charge, l’application exécute une déclaration **SELECT** qui spécifie les informations de schéma requises.

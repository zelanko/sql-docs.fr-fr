---
title: Poignées descripteur Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application parameter descriptor [ODBC]
- automatically allocated descriptors [ODBC]
- implementation row descriptor [ODBC]
- descriptor handles [ODBC]
- handles [ODBC], descriptor
- implementation parameter descriptor [ODBC]
- apd [ODBC]
- ard [ODBC]
- explicitly allocated descriptors [ODBC]
- ipd [ODBC]
- ird [ODBC]
- application row descriptor [ODBC]
ms.assetid: 7741035c-f3e7-4c89-901e-fe528392f67d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ed0595c97f3f4ad92d976c89327a01e25cb5b753
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305910"
---
# <a name="descriptor-handles"></a>Handles de descripteur
Un *descripteur* est une collection de métadonnées qui décrit les paramètres d’une déclaration SQL ou les colonnes d’un ensemble de résultats, comme le voit l’application ou le conducteur (également connu sous le nom *de mise en œuvre*). Ainsi, un descripteur peut remplir l’un des quatre rôles :  
  
-   **Descripteur paramètre d’application (APD).** Contient des informations sur les tampons d’application liés aux paramètres dans une déclaration SQL, telles que leurs adresses, longueurs et types de données C.  
  
-   **Descripteur paramètre de mise en œuvre (IPD).** Contient des renseignements sur les paramètres dans un communiqué sqL, comme leurs types de données SQL, leurs longueurs et leur nullité.  
  
-   **Descripteur de ligne d’application (ARD).** Contient des informations sur les tampons d’application liés aux colonnes dans un ensemble de résultats, tels que leurs adresses, longueurs et types de données C.  
  
-   **Implémentation Descriptor de ligne (IRD).** Contient des informations sur les colonnes dans un ensemble de résultats, tels que leurs types de données SQL, les longueurs et l’annulation.  
  
 Quatre descripteurs (un remplissant chaque rôle) sont attribués automatiquement lorsqu’une déclaration est attribuée. Ceux-ci sont connus sous le nom *de descripteurs automatiquement attribués* et sont toujours associés à cette déclaration. Les applications peuvent également allouer des descripteurs avec **SQLAllocHandle**. Ceux-ci sont connus comme *des descripteurs explicitement alloués*. Ils sont attribués sur une connexion et peuvent être associés à une ou plusieurs déclarations sur cette connexion pour remplir le rôle d’une DPA ou d’une DPA sur ces déclarations.  
  
 La plupart des opérations dans ODBC peuvent être effectuées sans utilisation explicite de descripteurs par l’application. Cependant, les descripteurs fournissent un raccourci pratique pour certaines opérations. Supposons, par exemple, qu’une application veuille insérer des données de deux ensembles différents de tampons. Pour utiliser le premier ensemble de tampons, il appellerait à plusieurs reprises **SQLBindParameter** pour les lier aux paramètres dans une déclaration **INSERT,** puis exécuter la déclaration. Pour utiliser la deuxième série de tampons, il répéterait ce processus. Alternativement, il pourrait mettre en place des fixations à la première série de tampons dans un descripteur et à la deuxième série de tampons dans un autre descripteur. Pour passer d’un ensemble de fixations, l’application appellerait simplement **SQLSetStmtAttr** et associerait le descripteur correct à la déclaration sous le titre apD.  
  
 Pour plus d’informations sur les descripteurs, voir [Types de descripteurs](../../../odbc/reference/develop-app/types-of-descriptors.md).

---
title: "CRÉER des restrictions instruction TABLE | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CREATE TABLE statement limitations [ODBC]
- ODBC SQL grammar, CREATE TABLE statement limitations
ms.assetid: c5067855-20c9-456f-8d63-f375b4297f2e
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0d8f73082a87978bf735e2e44f97987ba34ffbb5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="create-table-statement-limitations"></a>CRÉER des restrictions de déclaration de TABLE
Lorsque le Microsoft Access, Microsoft Excel ou Paradoxdriver est utilisé et la longueur d’une colonne de texte ou binaire n’est pas spécifiée (ou est spécifiée en tant que 0), la longueur de colonne a la valeur 255.  
  
 Lorsque le pilote dBASE est utilisé et la longueur d’une colonne de texte ou binaire n’est pas spécifiée (ou est spécifiée en tant que 0), la longueur de colonne a la valeur 254.  
  
 Un maximum de 255 colonnes est pris en charge.  
  
 Lorsque le pilote Microsoft Excel est utilisé sur un ne 5.0, 7.0, ou une source de 97 données, une feuille de calcul ne peut pas être créé avec le même nom qu’une feuille de calcul qui a été supprimée précédemment. Lorsque le pilote Microsoft Excel est utilisé pour accéder à une feuille de calcul version 5.0, 7.0 ou 97, une instruction DROP TABLE supprime la feuille de calcul, mais ne supprime pas le nom de la feuille de calcul.  
  
 Lorsque le pilote Paradox est utilisé, les colonnes ne peuvent pas être ajoutées une fois qu’un index a été défini sur une table. Si la première colonne de la liste d’arguments d’une instruction CREATE TABLE crée un index, une deuxième colonne ne peut pas être incluse dans la liste d’arguments.

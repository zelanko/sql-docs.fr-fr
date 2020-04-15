---
title: Limites d’énoncés de table CREATE (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE TABLE statement limitations [ODBC]
- ODBC SQL grammar, CREATE TABLE statement limitations
ms.assetid: c5067855-20c9-456f-8d63-f375b4297f2e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a83acb061cf8192dff1c6adede349f49a0b0bbdb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280870"
---
# <a name="create-table-statement-limitations"></a>CREATE TABLE, instruction - limitations
Lorsque microsoft Access, Microsoft Excel ou Paradoxdriver sont utilisés, et que la longueur d’un texte ou d’une colonne binaire n’est pas spécifiée (ou est spécifiée comme 0), la longueur de la colonne sera réglée à 255.  
  
 Lorsque le pilote dBASE est utilisé, et la longueur d’un texte ou d’une colonne binaire n’est pas spécifiée (ou est spécifiée comme 0), la longueur de la colonne sera réglée à 254.  
  
 Un maximum de 255 colonnes est supportée.  
  
 Lorsque le pilote Microsoft Excel est utilisé sur une source de données MicrosoftExcel 5.0, 7.0 ou 97, une feuille de travail ne peut pas être créée du même nom qu’une feuille de travail qui a été précédemment abandonnée. Lorsque le pilote Microsoft Excel est utilisé pour accéder à une feuille de travail de la version 5.0, 7.0 ou 97, une déclaration DROP TABLE efface la feuille de travail, mais ne supprime pas le nom de la feuille de travail.  
  
 Lorsque le pilote Paradox est utilisé, les colonnes ne peuvent pas être ajoutées une fois qu’un index a été défini sur une table. Si la première colonne de la liste d’arguments d’une instruction CREATE TABLE crée un index, une deuxième colonne ne peut pas être incluse dans la liste d’arguments.

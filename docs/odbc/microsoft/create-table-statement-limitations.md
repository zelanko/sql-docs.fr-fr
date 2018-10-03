---
title: CREATE TABLE, instruction-Limitations | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f5eab1c3bf6891f10c897966035dced2ffdc10ba
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622107"
---
# <a name="create-table-statement-limitations"></a>CREATE TABLE, instruction - limitations
Lorsque le Microsoft Access, Microsoft Excel ou Paradoxdriver est utilisé et la longueur d’une colonne de texte ou binaire n’est pas spécifiée (ou est spécifiée en tant que 0), la longueur de colonne est définie sur 255.  
  
 Lorsque le pilote dBASE est utilisé et la longueur d’une colonne de texte ou binaire n’est pas spécifiée (ou est spécifiée en tant que 0), la longueur de colonne est définie sur 254.  
  
 Un maximum de 255 colonnes est pris en charge.  
  
 Lorsque le pilote Microsoft Excel est utilisé sur un ne 5.0, 7.0, ou d’une source de 97 données, une feuille de calcul ne peut pas être créé avec le même nom qu’une feuille de calcul qui a été supprimée précédemment. Lorsque le pilote Microsoft Excel est utilisé pour accéder à une feuille de calcul de la version 5.0, 7.0 ou 97, une instruction DROP TABLE efface la feuille de calcul, mais ne supprime pas le nom de la feuille de calcul.  
  
 Lorsque le pilote Paradox est utilisé, les colonnes ne peuvent pas être ajoutées une fois qu’un index a été défini sur une table. Si la première colonne de la liste d’arguments d’une instruction CREATE TABLE crée un index, une deuxième colonne ne peut pas être incluse dans la liste d’arguments.

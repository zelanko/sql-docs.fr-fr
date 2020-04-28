---
title: Grammaire SQL ODBC prise en charge (pilote ODBC Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- native Visual FoxPro language syntax [ODBC]
- FoxPro ODBC driver [ODBC], SQL grammar
- SQL grammar [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], SQL grammar
- grammar support in Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
- FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
ms.assetid: f41a38c2-e22e-4c65-a32e-9a6777435160
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f72548d0708a63f887f7d6da4d4f5988500f0eef
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81304082"
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>Grammaire ODBC SQL prise en charge (pilote ODBC Visual FoxPro)
Le pilote ODBC Microsoft Visual FoxPro prend en charge les éléments suivants :  
  
-   Toutes les instructions et clauses SQL dans la grammaire SQL minimale ODBC  
  
-   Instruction SQL supplémentaire issue de la grammaire SQL ODBC Core  
  
 Le tableau suivant répertorie les éléments pris en charge par le pilote, par le niveau de grammaire SQL ODBC.  
  
|Level|Éléments|Élément|  
|-----------|--------------|----------|  
|Minimum|Langage de définition de données (DDL)|CREATE TABLE et DROP TABLE|  
||Langage de manipulation de données (DML)|SELECT, INSERT, UPDATE et DELETE|  
||Expressions|Simple (par exemple, un>B + C)|  
||Types de données|CHAR, VARCHAR ou LONG VARCHAR|  
  
 En plus de la grammaire SQL ODBC prise en charge, le pilote ODBC Visual FoxPro prend en charge la syntaxe de langage Visual FoxPro native complète pour les commandes Visual FoxPro suivantes :  
  
 [ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [DELETE](../../odbc/microsoft/delete-sql-command.md)  
  
 [SUPPRIMER LA BALISE](../../odbc/microsoft/delete-tag-command.md)  
  
 [DROP TABLE](../../odbc/microsoft/drop-table-command.md)  
  
 [INDEX](../../odbc/microsoft/index-command.md)  
  
 [INSERT](../../odbc/microsoft/insert-sql-command.md)  
  
 [SELECT](../../odbc/microsoft/select-sql-command.md)  
  
 [UPDATE](../../odbc/microsoft/update-sql-command.md)

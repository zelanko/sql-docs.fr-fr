---
title: Prise en charge de la grammaire SQL ODBC (pilote ODBC de Visual FoxPro) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10df35f4f29de4ac3899efa0e86e48af861f1e65
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62633770"
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>Grammaire ODBC SQL prise en charge (pilote ODBC Visual FoxPro)
Le pilote ODBC Visual FoxPro Microsoft prend en charge les éléments suivants :  
  
-   Toutes les instructions SQL et les clauses dans la grammaire SQL minimale de ODBC  
  
-   Une instruction SQL supplémentaire à partir de la grammaire SQL de base ODBC  
  
 Le tableau suivant répertorie les éléments pris en charge par le pilote, selon le niveau de grammaire SQL de ODBC.  
  
|Level|Éléments|Élément|  
|-----------|--------------|----------|  
|Minimum|Langage de définition de données (DDL)|CREATE TABLE et DROP TABLE|  
||Langage de Manipulation de données (DML)|SÉLECTIONNER, insérer, mettre à jour et supprimer|  
||Expressions|Simple (tel que A > B + C)|  
||Types de données|CHAR, VARCHAR ou LONG VARCHAR|  
  
 En plus de la grammaire SQL ODBC pris en charge, le pilote ODBC Visual FoxPro prend en charge la syntaxe complète du langage Visual FoxPro native pour les commandes de Visual FoxPro suivantes :  
  
 [ALTER TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [DELETE](../../odbc/microsoft/delete-sql-command.md)  
  
 [SUPPRIMER L’ÉTIQUETTE](../../odbc/microsoft/delete-tag-command.md)  
  
 [DROP TABLE](../../odbc/microsoft/drop-table-command.md)  
  
 [INDEX](../../odbc/microsoft/index-command.md)  
  
 [INSERT](../../odbc/microsoft/insert-sql-command.md)  
  
 [SELECT](../../odbc/microsoft/select-sql-command.md)  
  
 [UPDATE](../../odbc/microsoft/update-sql-command.md)

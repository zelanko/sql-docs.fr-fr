---
title: Prise en charge de la grammaire de ODBC SQL (le pilote ODBC Visual FoxPro) | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- native Visual FoxPro language syntax [ODBC]
- FoxPro ODBC driver [ODBC], SQL grammar
- SQL grammar [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], SQL grammar
- grammar support in Visual FoxPro ODBC driver [ODBC]
- Visual FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
- FoxPro ODBC driver [ODBC], native Visual FoxPro language syntax
ms.assetid: f41a38c2-e22e-4c65-a32e-9a6777435160
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: acaf0c210d31cc17e597e9e24245cc46859f44f1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>Grammaire de prise en charge ODBC SQL (le pilote ODBC Visual FoxPro)
Le pilote ODBC Microsoft Visual FoxPro prend en charge les éléments suivants :  
  
-   Toutes les instructions SQL et les clauses dans la grammaire SQL minimale d’ODBC  
  
-   Une instruction SQL supplémentaire à partir de la grammaire SQL ODBC core  
  
 Le tableau suivant répertorie les éléments pris en charge par le pilote, par niveau de grammaire SQL de ODBC.  
  
|Level|Éléments|Élément|  
|-----------|--------------|----------|  
|Minimum|Langage de définition de données (DDL)|CREATE TABLE et DROP TABLE|  
||Langage de Manipulation de données (DML)|SÉLECTIONNER, insérer, mettre à jour et supprimer|  
||Expressions|Simple (par exemple un > B + C)|  
||Types de données|CHAR, VARCHAR ou LONG VARCHAR|  
  
 En plus de la grammaire SQL ODBC pris en charge, le pilote ODBC Visual FoxPro prend en charge la syntaxe du langage Visual FoxPro native complète pour les commandes de Visual FoxPro suivantes :  
  
 [MODIFICATION DE LA TABLE](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [DELETE](../../odbc/microsoft/delete-sql-command.md)  
  
 [SUPPRIMER LA BALISE](../../odbc/microsoft/delete-tag-command.md)  
  
 [DROP TABLE](../../odbc/microsoft/drop-table-command.md)  
  
 [INDEX](../../odbc/microsoft/index-command.md)  
  
 [INSERT](../../odbc/microsoft/insert-sql-command.md)  
  
 [SELECT](../../odbc/microsoft/select-sql-command.md)  
  
 [UPDATE](../../odbc/microsoft/update-sql-command.md)

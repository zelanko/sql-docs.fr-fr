---
title: Somn ète ODBC SQL Grammar (Visual FoxPro ODBC Driver) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304082"
---
# <a name="supported-odbc-sql-grammar-visual-foxpro-odbc-driver"></a>Grammaire ODBC SQL prise en charge (pilote ODBC Visual FoxPro)
Le pilote Microsoft Visual FoxPro ODBC prend en charge ce qui suit :  
  
-   Toutes les déclarations et clauses SQL dans la grammaire minimale SQL de l’ODBC  
  
-   Une déclaration SQL supplémentaire de la grammaire SQL de base de l’ODBC  
  
 Le tableau suivant répertorie les éléments pris en charge par le conducteur, par ODBC SQL Grammar level.  
  
|Level|Éléments|Élément|  
|-----------|--------------|----------|  
|Minimum|Langage de définition de données (DDL)|CREATE TABLE et DROP TABLE|  
||Langage de manipulation de données (DML)|SELECT, INSERT, UPDATE et DELETE|  
||Expressions|Simple (comme A>B-C)|  
||Types de données|CHAR, VARCHAR, ou LONG VARCHAR|  
  
 En plus de la grammaire ODBC SQL supportée, le Visual FoxPro ODBC Driver prend en charge la syntaxe en langue visuelle FoxPro native complète pour les commandes Visuelle FoxPro suivantes :  
  
 [TABLE DE MODIFICATION](../../odbc/microsoft/alter-table-sql-command.md)  
  
 [CRÉER UNE TABLE](../../odbc/microsoft/create-table-sql-command.md)  
  
 [Supprimer](../../odbc/microsoft/delete-sql-command.md)  
  
 [SUPPRIMER L’ÉTIQUETTE](../../odbc/microsoft/delete-tag-command.md)  
  
 [TABLE DE CHUTE](../../odbc/microsoft/drop-table-command.md)  
  
 [Index](../../odbc/microsoft/index-command.md)  
  
 [Insérer](../../odbc/microsoft/insert-sql-command.md)  
  
 [SELECT](../../odbc/microsoft/select-sql-command.md)  
  
 [mettre à jour](../../odbc/microsoft/update-sql-command.md)

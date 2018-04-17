---
title: Suppression de lignes dans l’ensemble de lignes avec SQLSetPos | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLSetPos function [ODBC], deleting rows
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
ms.assetid: 3117a47d-e179-4f76-89d0-656582f1c9bb
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 828ab8f154669473a6e90b60126d3b047c45e515
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>Suppression de lignes dans l’ensemble de lignes avec SQLSetPos
L’opération de suppression de **SQLSetPos** permet de supprimer une ou plusieurs lignes sélectionnées d’une table de la source de données. Pour supprimer des lignes avec **SQLSetPos**, l’application appelle **SQLSetPos** avec *opération* défini sur SQL_DELETE et *RowNumber* définie pour le numéro de la ligne à supprimer. Si *RowNumber* est 0, toutes les lignes dans l’ensemble de lignes sont supprimées.  
  
 Après avoir **SQLSetPos** est retournée, la ligne supprimée est la ligne actuelle et son statut est SQL_ROW_DELETED. La ligne ne peut pas être utilisée dans toutes les opérations positionnées supplémentaires, telles que les appels à **SQLGetData** ou **SQLSetPos**.  
  
 Lors de la suppression de toutes les lignes de l’ensemble de lignes (*RowNumber* est égal à 0), l’application peut empêcher le pilote à partir de la suppression de certaines lignes à l’aide du tableau d’opération de ligne, de la même façon que pour l’opération de mise à jour de **SQLSetPos**. (Consultez [mise à jour des lignes dans l’ensemble de lignes avec SQLSetPos](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).)  
  
 Chaque ligne supprimée doit être une ligne qui existe dans le jeu de résultats. Si les mémoires tampons d’application ont été remplies par extraction et un tableau d’état de ligne a été maintenu, ses valeurs à chacune de ces positions de ligne ne doivent pas être SQL_ROW_DELETED, SQL_ROW_ERROR ou SQL_ROW_NOROW.

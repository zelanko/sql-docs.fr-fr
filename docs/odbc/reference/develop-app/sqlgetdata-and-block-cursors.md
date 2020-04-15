---
title: SQLGetData et Block Cursors (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursors [ODBC], block
- SQLGetData function [ODBC], block cursors
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 12599cdc-7725-4faf-bcae-e163ea0f5851
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b60d7093552b8f1dbed87d9ad8840ddb5a9e0799
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299749"
---
# <a name="sqlgetdata-and-block-cursors"></a>SQLGetData et curseurs de bloc
**SQLGetData** fonctionne sur une seule colonne d’une seule rangée et ne peut pas aller chercher un tableau contenant des données provenant de plusieurs rangées. C’est parce que l’utilisation principale de **SQLGetData** est d’aller chercher de longues données dans les pièces, et il ya peu ou pas de raison de le faire pour plus d’une rangée à la fois.  
  
 Pour utiliser **SQLGetData** avec un curseur de bloc, une application appelle d’abord **SQLSetPos** pour positionner le curseur sur une seule rangée. Il appelle ensuite **SQLGetData** pour une colonne dans cette rangée. Cependant, ce comportement est facultatif. Pour déterminer si un conducteur prend en charge l’utilisation de **SQLGetData** avec des curseurs de bloc, une application appelle **SQLGetInfo** avec l’option SQL_GETDATA_EXTENSIONS.
